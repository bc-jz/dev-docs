## <span class="jumptarget"> <a name="load"></a> Load, Uninstall, and User Removal Requests</span>

In addition to the **Auth Callback URI**, the [App Registration](#app-registration) wizard requests the following URIs.

| Name | Required? | Event Discussion |
| --- | --- | --- |
| Load Callback URI | Yes | Called when the store owner or user clicks to load your app. |
| Uninstall Callback URI | No | Called when the store owner clicks to uninstall your app. |
| Remove User Callback URI | No | Called when the store admin revokes a user's access to your app. |

Each BigCommerce request is a `GET` request and includes a signed payload that allows your app to:

*   Verify that the request came from BigCommerce.
*   Identify the store.
*   Identify the store owner or user.

The remainder of this entry discusses:

*   [The load request and response](#load-request-and-response).
*   [The Uninstall request](#uninstall-request-optional).
*   [The Remove User request](#remove-user-request-optional).
*   [The signed payload](#processing-the-signed-payload).

### <span class="jumptarget"> <a name="load_request"></a> Load Request and Response</span>

Once your app has been installed, the store owner or user can click its icon in the control panel to launch it. This causes BigCommerce to send a `GET` request to the **Load Callback URI** that you provided. In a production environment, the **Load Callback URI** must be publicly available, fully qualified, and served over TLS/SSL.

<aside class="warning">
<span class="aside-warning-hd">Handling Requests Securely</span><br><br>
The request comes from the client browser, rather than directly from BigCommerce. This allows you to use a non-publicly-available <b>Auth Callback URI</b> while testing your app.<br><br>

For security, Auth and Load callback should be handled server-side. If you are building a client-side application (such as an AngularJS Single Page App), you should handle Auth and Load callbacks outside that application. Use a separate service that accepts the Auth and Load callback requests, generates tokens, validates requests, and then redirects the user to your client-side app's entry point.
</aside>

The `GET` request contains a signed payload, as shown below.

```
GET /load?signed_payload=hw9fhkx2ureq.t73sk8y80jx9 HTTP/1.1
Host: app.example.com
```

Upon receiving a `GET` request to the **Load Callback URI**, your app needs to [process the signed payload](#processing-the-signed-payload).

After processing the payload, your app returns its user interface as HTML. BigCommerce renders this inside of an iframe. Please see [User&#160;Interface Constraints](#ui-constraints) for important information about your app's user interface.

### <span class="jumptarget"> <a name="uninstall"></a> Uninstall Request (Optional)</span>

Store owners have the option to uninstall any app at any time. When a store owner uninstalls an app, the app's OAuth token is revoked and the app cannot make requests to the Stores API on the store's behalf anymore.

You do not need to provide an **Uninstall Callback URI**. The lack of an **Uninstall Callback URI** does not prevent uninstallation. Instead, the **Uninstall Callback URI** allows you to track store owners who uninstall your app and to run cleanup operations, such as removing the store's user accounts from your system.

Should you choose to avail of this option and provide an **Uninstall Callback URI**, please note that it must be publicly available, fully qualified, and served over TLS/SSL. If provided, BigCommerce will send a `GET` request to your **Uninstall Callback URI** when a store owner clicks to uninstall your app. An example follows.

```
GET /uninstall?signed_payload=hw9fhkx2ureq.t73sk8y80jx9 HTTP/1.1
Host: app.example.com
```

Upon receiving the `GET` request, your app will need to [process the signed payload](#processing-the-signed-payload).

<aside class="notice">
<span class="aside-notice-hd">NOTE:</span>
Any HTML that you return in your response will not be rendered.
</aside>


### <span class="jumptarget"> <a name="remove-user"></a> Remove User Request (Optional)</span>

If you have not enabled [multi-user support](#multi-user-support), you will not provide a **Remove User Callback URI** and can ignore this section. If you enable multi-user support, you can optionally specify a **Remove User Callback URI**. It must be fully qualified, publicly available, and served over TLS/SSL. BigCommerce will send a `GET` request to your **Remove User Callback URI** when a store admin revokes a user's access to your app. An example follows.

```
GET /remove-user?signed_payload=hw9fhkx2ureq.t73sk8y80jx9 HTTP/1.1
Host: app.example.com
```

Upon receiving the `GET` request, your app will need to [process the signed payload](#processing-the-signed-payload).

<aside class="notice">
<span class="aside-notice-hd">NOTE:</span>
Any HTML that you return in your response will not be rendered.
</aside>

### <span class="jumptarget"> <a name="process"></a> Processing the Signed Payload</span>

Processing the signed payload involves splitting and decoding it verifying the HMAC signature, and processing the JSON object. 

#### <span class="jumptarget"> <a name="process"></a> Splitting and Decoding the Signed Payload</span>

The signed payload is a string containing a base64url-encoded JSON string and a base64url-encoded <a href="http://en.wikipedia.org/wiki/Hash-based_message_authentication_code" target="_blank">HMAC signature</a>. The parts are delimited by the `.` character:

```
encoded_json_string.encoded_hmac_signature
```

To decode the signed payload, complete the following steps:

1.  Split `signed_payload` into its two parts at the `.` delimiter.
2.  Decode `encoded_json_string` using base64url.
3.  Convert the decoded JSON string into an object. See [Processing the JSON object](#processing-the-json-object) for more about this object.
4.  Decode `encoded_hmac_signature` using base64url.
5.  Use your client secret to verify the signature. See the next section for more details.

#### <span class="jumptarget"> Verifying the HMAC Signature</span>

To verify the payload, you need to sign the payload using your client secret, and confirm that it matches the signature that was sent in the request.

<aside class="warning">
<span class="aside-warning-hd">Blocking Timing Attacks</span><br><br>
To limit the vulnerability of your app to <a href="http://codahale.com/a-lesson-in-timing-attacks/" target="_blank">timing attacks</a>, we recommend using a constant time-string comparison function, rather than the equality operator, to check that the signatures match.
</aside>

##### <span class="jumptarget"> Examples</span>

*   [PHP](#strcmp-php)

```php?start_inline=1
function verifySignedRequest($signedRequest)
{
	list($encodedData, $encodedSignature) = explode('.', $signedRequest, 2); 

	// decode the data
	$signature = base64_decode($encodedSignature);
        $jsonStr = base64_decode($encodedData);
	$data = json_decode($jsonStr, true);

	// confirm the signature
	$expectedSignature = hash_hmac('sha256', $jsonStr, $clientSecret(), $raw = false);
	if (!hash_equals($expectedSignature, $signature)) {
		error_log('Bad signed request from BigCommerce!');
		return null;
	}
	return $data;
}
```

<aside class="notice">
<span class="aside-notice-hd">NOTE:</span> 
<code>!hash_equals</code> is available in PHP 5.6 and later. If you are running an older version of PHP, pull in a compatibility library such as the following: <a href="https://packagist.org/packages/realityking/hash_equals" target="_blank">https://packagist.org/packages/realityking/hash_equals</a>. BigCommerce's sample app <NOBR><a href="https://github.com/bigcommerce/hello-world-app-php-silex" target="_blank">hello-world-app-php-silex app</a></nobr> does this automatically.
</aside>

*   [Ruby](#strcmp-ruby)

```ruby
require "base64"
require "openssl"

def verify(signed_payload, client_secret)
  message_parts = signed_payload.split(".")

  encoded_json_payload = message_parts[0]
  encoded_hmac_signature = message_parts[1]

  payload_object = Base64.strict_decode(encoded_json_payload)
  provided_signature = Base64.strict_decode(encoded_hmac_signature)

  expected_signature = OpenSSL::HMAC::hexdigest("sha256", client_secret, payload_object)

  return false unless secure_compare(expected_signature, provided_signature)

  JSON.parse(payload_object)
end

def secure_compare(a, b)
  return false if a.blank? || b.blank? || a.bytesize != b.bytesize
  l = a.unpack "C#{a.bytesize}"

  res = 0
  b.each_byte { |byte| res |= byte ^ l.shift }
  res == 0
end
```

### <span class="jumptarget" id="Identifying"> Processing the JSON Object</span>

The JSON object embedded in the `signed_payload` contains information about the BigCommerce store and the store owner or user.

#### <span class="jumptarget"> Identifying the Store</span>

You should use the store information to identify the store to which the request pertains.

#### <span class="jumptarget"> Interpreting the User Information</span>

Interpreting the user information varies as follows:

| Request type | Multiple users enabled | Multiple users not enabled |
| --- | --- | --- |
| Load | Compare the user information to see if it matches that of the store owner, received at the time of [app installation](#app-installation-and-update-sequence) or that of an existing user. If the user information does not match either of these, then it represents a new user that you should add to your database or other storage. | The information should match that of the store owner, received at the time of [app installation](#app-installation-and-update-sequence). |
| Uninstall | The user information should match that of the store owner. Only the store owner can uninstall your app. | Should match the store owner. |
| Remove user | The user information should match one of the users that you have stored. After locating the stored user, delete it from your database or other storage. | N/A |

#### <span class="jumptarget"> JSON Values</span>

| Name | Data Type | Value Description |
| --- | --- | --- |
| user.id | integer | Unique identifier for the user who initiated the callback. |
| user.email | string | Email address of the user who initiated the callback. |
| owner.id | integer | Unique identifier for the user listed as the store owner. |
| owner.email | string | Email address of the user listed as the store owner. |
| context | string | The context value is part of the API path for this store and includes the store_hash. |
| store_hash | string |Unique identifier for the store. |
| timestamp | float | The time (in Unix time) when the callback was generated. |

#### <span class="jumptarget"> JSON Example</span>

```json
{
    "user":
         {
        "id":9128,
        "email":"user@mybigcommerce.com"
     },
     "owner":
          {
         "id":9128,
         "email":"user@mybigcommerce.com"
     },
     "context":"stores/z4zn3wo",
     "store_hash":"z4zn3wo",
     "timestamp":1469823892.9123988
}
```
