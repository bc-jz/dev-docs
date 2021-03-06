## <span class="jumptarget" id="approval"> App Store Approval Requirements </span>

Our submission guidelines aim to protect the merchant experience, and to provide enough structure for you to develop apps efficiently and effectively.

Before submitting your app, please be sure to carefully review it against the following requirements, to avoid having your app rejected and needing to re-submit it:

### <span class="jumptarget" id="approval"> App Approval Requirements </span>

*   Apps must perform as described.

*   All information supplied in the app submission process must be genuine and accurate.

*   Apps must provide pricing information – including pricing for starting a new service, and the cost of services after the free trial.

*   All API requests must be made using OAuth authentication.

*   Apps must be compatible with both the <a href="/themes/blueprint/" target="_blank">Blueprint theme framework</a> and the <a href="https://stencil.bigcommerce.com/docs/" target="_blank">Stencil theme framework</a>, for any storefront components.

* Apps must include contact information should a merchant need support on the app. Any relevant reference docs or media should also be included or linked.

*   Apps must be production-ready and free of defects.
<aside class="warning">
<span class="aside-warning-hd">Test before Submitting </span><br>
Install and test your app thoroughly prior to submission. Be sure to install and run your app inside of your sandbox store, as a draft area to conduct your tests.
</aside>

*   Apps must function properly on all [supported browsers](#supported-browsers), and must conform to the [user-interface constraints](#ui-constraints) – including P3P policies as necessary, and no mixed content.

*   The entire app should operate within the iframe that opens when the user clicks on your app icon in the control panel's launch bar. Exceptions may be made for apps that need to authenticate to other services using OAuth – as long as they open a new tab to do so.

*   Apps must be easy to use.

*   Whenever possible, apps must use the API resources to auto-fill and obtain information, rather than prompting the user. BigCommerce will reject apps requesting information that can be auto-filled.

    <aside class="notice">
    <span class="aside-notice-hd">Auto-Filling API</span><br> You can obtain the store name, phone number, and other information from the <a href="/api/v2/#store-information-reference" target="_blank">Store&#160;Information</a> resource.
    </aside>

*   The user ID and email address from the [OAuth flow](#receiving-the-post-response) should allow you to automatically log the merchant into any additional systems. BigCommerce prefers apps that provide the merchant with a single-sign-on experience.

*   Apps must [return some HTML](#responding-to-the-get-request) in response to GET requests to the [Auth Callback URI](#processing-the-signed-payload).

*   Must use a TLS/SSL certificate signed by a valid certificate authority. Self-signed certificates will generate browser warnings and are not acceptable.

*   No competitor integrations or references should appear in the app or in marketing materials.

*   Any instances of the BigCommerce brand name must match current branding, i.e., one word with an uppercase "C".

*   Apps must have all required information and files discussed in [App Submission](#app-submission).

### <span class="jumptarget" id="apps-accepted"> Types of Apps We're Accepting </span>

| Accepting | Not Accepting |
| --- | --- |
| Accounting | Real-Time Tax |
| Advertising | Customized Checkout |
| Analytics | Real-time Shipping Rate updates |
| Cloud integration | Payment Methods |
| Customer feedback |
| Drop shipping |
| Email marketing |
| Live chat |
| Marketing |
| Merchandising |
| Mobile |
| Multichannel listing |
| Order fulfillment |
| Order management |
| Point of sale |
| Product review |
| Shipping |
| Shopping comparison |
| Social media |
| Split testing |

Questions? Please contact [appstore@bigcommerce.com](mailto:appstore@bigcommerce.com)
