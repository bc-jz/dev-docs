|||
|---|---|
| **Manages** | [Product Object](/api/v2#product) |
| **OAuth Scopes** | store_v2_products |
| |store_v2_products_read_only

### <span class="jumptarget"> List Products </span>

Gets the collection of products. (Default sorting is by product id, from lowest to highest.)

*   OAuth 
> `GET /stores/{store_hash}/v2/products`
*   Basic Auth
> `GET /api/v2/products`

#### <span class="jumptarget"> Filters </span>

Filter parameters can be added to the URL query string to select specific products in the collection.

| Parameter | Type | Example |
| --- | --- | --- |
| min_id | int | /api/v2/products?min_id={value} |
| max_id | int | /api/v2/products?max_id={value} |
| name | string | /api/v2/products?name={value} |
| keyword_filter | string | /api/v2/products?keyword_filter={value} |
| description | string | /api/v2/products?description={value} |
| sku | string | /api/v2/products?sku={value} |
| condition | string | /api/v2/products?condition={value} |
| availability | string | /api/v2/products?availability={value} |
| brand_id | string | /api/v2/products?brand_id={value} |
| min_date_created | dateTime or date | /api/v2/products?min_date_created={value} |
| max_date_created | dateTime or date | /api/v2/products?max_date_created={value} |
| min_date_modified | dateTime or date | /api/v2/products?min_date_modified={value} |
| max_date_modified | dateTime or date | /api/v2/products?max_date_modified={value} |
| min_date_last_imported | date | /api/v2/products?min_date_last_imported={value} |
| max_date_last_imported | date | /api/v2/products?max_date_last_imported={value} |
| min_price | decimal | /api/v2/products?min_price={value} |
| max_price | decimal | /api/v2/products?max_price={value} |
| min_number_sold | int | /api/v2/products?min_number_sold={value} |
| max_number_sold | int | /api/v2/products?max_number_sold={value} |
| is_visible | string | /api/v2/products?is_visible={value} |
| is_featured | string | /api/v2/products?is_featured={value} |
| min_inventory_level | int | /api/v2/products?min_inventory_level={value} |
| max_inventory_level | int | /api/v2/products?max_inventory_level={value} |
| include_sku | boolean | /api/v2/products?include_sku={value} |
| category | string | /api/v2/products?category={value} |
| product_tax_code | string | /api/v2/products?product_tax_code={value} |

#### <span class="jumptarget"> Pagination </span>

Parameters can be added to the URL query string to paginate the collection. The maximum limit is 250. If a limit isn’t provided, up to 50 products are returned by default.

| Parameter | Type | Example |
| --- | --- | --- |
| Page | int | /api/v2/products?page={number} |
| Limit | int | /api/v2/products?limit={count} |

#### <span class="jumptarget"> Notes </span>

You can filter the retrieved fields by appending one of the following options to your request:

* ?include=
* ?include=@summary
* ?exclude=

For details, syntax, and examples, please see the [Get a Product](#get-a-product) operation.

#### <span class="jumptarget"> Response </span>

Example JSON returned in the response:

```json
[
  {
    "id": 32,
    "keyword_filter": null,
    "name": "[Sample] Tomorrow is today, Red printed scarf",
    "type": "physical",
    "sku": "",
    "description": "Densely pack your descriptions with useful information and watch products fly off the shelf.",
    "search_keywords": null,
    "availability_description": "",
    "price": "89.0000",
    "cost_price": "0.0000",
    "retail_price": "0.0000",
    "sale_price": "0.0000",
    "calculated_price": "89.0000",
    "sort_order": 0,
    "is_visible": true,
    "is_featured": true,
    "related_products": "-1",
    "inventory_level": 0,
    "inventory_warning_level": 0,
    "warranty": null,
    "weight": "0.3000",
    "width": "0.0000",
    "height": "0.0000",
    "depth": "0.0000",
    "fixed_cost_shipping_price": "10.0000",
    "is_free_shipping": false,
    "inventory_tracking": "none",
    "rating_total": 0,
    "rating_count": 0,
    "total_sold": 0,
    "date_created": "Fri, 21 Sep 2012 02:31:01 +0000",
    "brand_id": 17,
    "view_count": 4,
    "page_title": "",
    "meta_keywords": null,
    "meta_description": null,
    "layout_file": "product.html",
    "is_price_hidden": false,
    "price_hidden_label": "",
    "categories": [
      14
    ],
    "date_modified": "Mon, 24 Sep 2012 01:34:57 +0000",
    "event_date_field_name": "Delivery Date",
    "event_date_type": "none",
    "event_date_start": "",
    "event_date_end": "",
    "myob_asset_account": "",
    "myob_income_account": "",
    "myob_expense_account": "",
    "peachtree_gl_account": "",
    "condition": "New",
    "is_condition_shown": false,
    "preorder_release_date": "",
    "is_preorder_only": false,
    "preorder_message": "",
    "order_quantity_minimum": 0,
    "order_quantity_maximum": 0,
    "open_graph_type": "product",
    "open_graph_title": "",
    "open_graph_description": null,
    "is_open_graph_thumbnail": true,
    "upc": null,
    "avalara_product_tax_code": "",
    "date_last_imported": "",
    "option_set_id": null,
    "tax_class_id": 0,
    "option_set_display": "right",
    "bin_picking_number": "",
    "custom_url": "/tomorrow-is-today-red-printed-scarf/",
    "primary_image": {
      "id": 247,
      "zoom_url": "https://cdn.url.path/bcapp/et7xe3pz/products/32/images/247/in_123__14581.1393831046.1280.1280.jpg?c=1",
      "thumbnail_url": "https://cdn.url.path/bcapp/et7xe3pz/products/32/images/247/in_123__14581.1393831046.220.290.jpg?c=1",
      "standard_url": "https://cdn.url.path/bcapp/et7xe3pz/products/32/images/247/in_123__14581.1393831046.386.513.jpg?c=1",
      "tiny_url": "https://cdn.url.path/bcapp/et7xe3pz/products/32/images/247/in_123__14581.1393831046.44.58.jpg?c=1"
    },
    "availability": "available",
    "brand": {
      "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/brands/17.json",
      "resource": "/brands/17"
    },
    "images": {
      "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/products/32/images.json",
      "resource": "/products/32/images"
    },
    "discount_rules": {
      "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/products/32/discountrules.json",
      "resource": "/products/32/discountrules"
    },
    "configurable_fields": {
      "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/products/32/configurablefields.json",
      "resource": "/products/32/configurablefields"
    },
    "custom_fields": {
      "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/products/32/customfields.json",
      "resource": "/products/32/customfields"
    },
    "videos": {
      "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/products/32/videos.json",
      "resource": "/products/32/videos"
    },
    "skus": {
      "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/products/32/skus.json",
      "resource": "/products/32/skus"
    },
    "rules": {
      "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/products/32/rules.json",
      "resource": "/products/32/rules"
    },
    "option_set": null,
    "options": {
      "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/products/32/options.json",
      "resource": "/products/32/options"
    },
    "tax_class": {
      "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/taxclasses/0.json",
      "resource": "/taxclasses/0"
    }
  },
  {
    "id": 33,
    "keyword_filter": null,
    "name": "[Sample] Anna, multi-colored bangles",
    "type": "physical",
    "sku": "",
    "description": "One of the best things you can do to make your store successful is invest some time in writing great product descriptions.</p>",
    "search_keywords": null,
    "availability_description": "",
    "price": "59.0000",
    "cost_price": "0.0000",
    "retail_price": "0.0000",
    "sale_price": "0.0000",
    "calculated_price": "59.0000",
    "sort_order": 0,
    "is_visible": true,
    "is_featured": true,
    "related_products": "-1",
    "inventory_level": 0,
    "inventory_warning_level": 0,
    "warranty": null,
    "weight": "0.5000",
    "width": "0.0000",
    "height": "0.0000",
    "depth": "0.0000",
    "fixed_cost_shipping_price": "0.0000",
    "is_free_shipping": false,
    "inventory_tracking": "none",
    "rating_total": 0,
    "rating_count": 0,
    "total_sold": 0,
    "date_created": "Fri, 21 Sep 2012 02:46:41 +0000",
    "brand_id": 18,
    "view_count": 12,
    "page_title": "",
    "meta_keywords": null,
    "meta_description": null,
    "layout_file": "product.html",
    "is_price_hidden": false,
    "price_hidden_label": "",
    "categories": [
      14
    ],
    "date_modified": "Mon, 24 Sep 2012 05:28:02 +0000",
    "event_date_field_name": "Delivery Date",
    "event_date_type": "none",
    "event_date_start": "",
    "event_date_end": "",
    "myob_asset_account": "",
    "myob_income_account": "",
    "myob_expense_account": "",
    "peachtree_gl_account": "",
    "condition": "New",
    "is_condition_shown": false,
    "preorder_release_date": "",
    "is_preorder_only": false,
    "preorder_message": "",
    "order_quantity_minimum": 0,
    "order_quantity_maximum": 0,
    "open_graph_type": "product",
    "open_graph_title": "",
    "open_graph_description": null,
    "is_open_graph_thumbnail": true,
    "upc": null,
    "avalara_product_tax_code": "",
    "date_last_imported": "",
    "option_set_id": 13,
    "tax_class_id": 0,
    "option_set_display": "right",
    "bin_picking_number": "",
    "custom_url": "/anna-multi-colored-bangles/",
    "primary_image": {
      "id": 245,
      "zoom_url": "https://cdn.url.path/bcapp/et7xe3pz/products/33/images/245/HERO_cocolee_anna_92865__20303.1393831046.1280.1280.jpg?c=1",
      "thumbnail_url": "https://cdn.url.path/bcapp/et7xe3pz/products/33/images/245/HERO_cocolee_anna_92865__20303.1393831046.220.290.jpg?c=1",
      "standard_url": "https://cdn.url.path/bcapp/et7xe3pz/products/33/images/245/HERO_cocolee_anna_92865__20303.1393831046.386.513.jpg?c=1",
      "tiny_url": "https://cdn.url.path/bcapp/et7xe3pz/products/33/images/245/HERO_cocolee_anna_92865__20303.1393831046.44.58.jpg?c=1"
    },
    "availability": "available",
    "brand": {
      "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/brands/18.json",
      "resource": "/brands/18"
    },
    "images": {
      "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/products/33/images.json",
      "resource": "/products/33/images"
    },
    "discount_rules": {
      "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/products/33/discountrules.json",
      "resource": "/products/33/discountrules"
    },
    "configurable_fields": {
      "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/products/33/configurablefields.json",
      "resource": "/products/33/configurablefields"
    },
    "custom_fields": {
      "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/products/33/customfields.json",
      "resource": "/products/33/customfields"
    },
    "videos": {
      "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/products/33/videos.json",
      "resource": "/products/33/videos"
    },
    "skus": {
      "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/products/33/skus.json",
      "resource": "/products/33/skus"
    },
    "rules": {
      "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/products/33/rules.json",
      "resource": "/products/33/rules"
    },
    "option_set": {
      "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/optionsets/13.json",
      "resource": "/optionsets/13"
    },
    "options": {
      "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/products/33/options.json",
      "resource": "/products/33/options"
    },
    "tax_class": {
      "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/taxclasses/0.json",
      "resource": "/taxclasses/0"
    }
  }
]
```

### <span class="jumptarget"> Get a Product </span>

Gets a product.

*   OAuth 
> `GET /stores/{store_hash}/v2/products/{id}`
*   Basic Auth
> `GET /api/v2/products/{id}`

#### <span class="jumptarget"> Notes </span>

You can filter the retrieved fields by appending one of the following options to your request: 

- `?include=`
- `?include=@summary` 
- `?exclude=`

In particular, you can reduce payload size, and improve performance, by excluding the `description` field.

##### <span class="jumptarget" id="get-a-product-mandatory"> Mandatory Fields </span>

However, the following fields are always present on product API requests, and cannot be excluded:

- `id`
- `name`
- `date_modified`
- `primary_image`

##### <span class="jumptarget"> include </span>

The following sample request will retrieve *only* the specified `date_created`, `price`, and `cost_price` fields, plus the [mandatory fields](#get-a-product-mandatory) listed just above:

```
https://store-et7xe3pz.mybigcommerce.com/api/v2/products/32?include=date_created,price,cost_price
```

Here is a corresponding sample response:

```json
{
    "id": 32,
    "name": "[Sample] Tomorrow is today, Red printed scarf",
    "price": "89.0000",
    "cost_price": "0.0000",
    "date_created": "Fri, 21 Sep 2012 02:31:01 +0000",
    "date_modified": "Thu, 10 Dec 2015 21:10:17 +0000",
    "primary_image": {
        "id": 247,
        "tiny_url": "https://cdn.url.path/bcapp/k84uuwpy/products/32/images/247/in_123__14581.1348449270.60.90.jpg?c=1",
        "standard_url": "https://cdn.url.path/bcapp/k84uuwpy/products/32/images/247/in_123__14581.1348449270.500.750.jpg?c=1",
        "thumbnail_url": "https://cdn.url.path/bcapp/k84uuwpy/products/32/images/247/in_123__14581.1348449270.190.285.jpg?c=1",
        "zoom_url": "https://cdn.url.path/bcapp/k84uuwpy/products/32/images/247/in_123__14581.1348449270.1280.1280.jpg?c=1"
    },
    "metadata": []
}
```

##### <span class="jumptarget"> include=@summary </span>

The `?include=@summary` option retrieves the following predefined subset of fields, in addition to the [mandatory fields](#get-a-product-mandatory) listed above: 

- `availability`
- `calculated_price`
- `inventory_tracking`
- `sku`
- `inventory_level`
- `inventory_warning_level`
- `is_visible`
- `is_featured` 

Here is a sample request with the `?include=@summary` option appended:

```
https://store-et7xe3pz.mybigcommerce.com/api/v2/products/32?include=@summary
```

Here is a corresponding sample response:

```json
{
    "id": 32,
    "name": "[Sample] Tomorrow is today, Red printed scarf",
    "sku": "TTRPS",
    "calculated_price": "89.0000",
    "is_visible": true,
    "is_featured": true,
    "inventory_level": 0,
    "inventory_warning_level": 0,
    "inventory_tracking": "none",
    "date_modified": "Thu, 10 Dec 2015 21:10:17 +0000",
    "availability": "available",
    "primary_image": {
        "id": 247,
        "tiny_url": "https://cdn.url.path/bcapp/k84uuwpy/products/32/images/247/in_123__14581.1348449270.60.90.jpg?c=1",
        "standard_url": "https://cdn.url.path/bcapp/k84uuwpy/products/32/images/247/in_123__14581.1348449270.500.750.jpg?c=1",
        "thumbnail_url": "https://cdn.url.path/bcapp/k84uuwpy/products/32/images/247/in_123__14581.1348449270.190.285.jpg?c=1",
        "zoom_url": "https://cdn.url.path/bcapp/k84uuwpy/products/32/images/247/in_123__14581.1348449270.1280.1280.jpg?c=1"
    },
    "metadata": []
}
```

##### <span class="jumptarget"> exclude </span>

The `?exclude=` option excludes one or more specified fields. However, you cannot exclude the mandatory `id`, `name`, `date_modified`, or `primary_image` fields.

Here is a sample request with the `?exclude=` option appended:

```
https://store-et7xe3pz.mybigcommerce.com/api/v2/products/32?exclude=description
```

We have omitted the corresponding sample response. However, the following section shows a complete sample response for a request submitted with no `?include` or `?exclude` option. (The effect of the `?exclude=description` option shown above would be to omit the `"description": ` field shown as the sixth field below.)


#### <span class="jumptarget"> Response </span>

Example JSON returned in the response:

```json
{
  "id": 32,
  "keyword_filter": null,
  "name": "[Sample] Tomorrow is today, Red printed scarf",
  "type": "physical",
  "sku": "",
  "description": "Densely pack your descriptions with useful information and watch products fly off the shelf.",
  "search_keywords": null,
  "availability_description": "",
  "price": "89.0000",
  "cost_price": "0.0000",
  "retail_price": "0.0000",
  "sale_price": "0.0000",
  "calculated_price": "89.0000",
  "sort_order": 0,
  "is_visible": true,
  "is_featured": true,
  "related_products": "-1",
  "inventory_level": 0,
  "inventory_warning_level": 0,
  "warranty": null,
  "weight": "0.3000",
  "width": "0.0000",
  "height": "0.0000",
  "depth": "0.0000",
  "fixed_cost_shipping_price": "10.0000",
  "is_free_shipping": false,
  "inventory_tracking": "none",
  "rating_total": 0,
  "rating_count": 0,
  "total_sold": 0,
  "date_created": "Fri, 21 Sep 2012 02:31:01 +0000",
  "brand_id": 17,
  "view_count": 4,
  "page_title": "",
  "meta_keywords": null,
  "meta_description": null,
  "layout_file": "product.html",
  "is_price_hidden": false,
  "price_hidden_label": "",
  "categories": [
    14
  ],
  "date_modified": "Mon, 24 Sep 2012 01:34:57 +0000",
  "event_date_field_name": "Delivery Date",
  "event_date_type": "none",
  "event_date_start": "",
  "event_date_end": "",
  "myob_asset_account": "",
  "myob_income_account": "",
  "myob_expense_account": "",
  "peachtree_gl_account": "",
  "condition": "New",
  "is_condition_shown": false,
  "preorder_release_date": "",
  "is_preorder_only": false,
  "preorder_message": "",
  "order_quantity_minimum": 0,
  "order_quantity_maximum": 0,
  "open_graph_type": "product",
  "open_graph_title": "",
  "open_graph_description": null,
  "is_open_graph_thumbnail": true,
  "upc": null,
  "avalara_product_tax_code": "",
  "date_last_imported": "",
  "option_set_id": null,
  "tax_class_id": 0,
  "option_set_display": "right",
  "bin_picking_number": "",
  "custom_url": "/tomorrow-is-today-red-printed-scarf/",
  "primary_image": {
    "id": 247,
    "zoom_url": "https://cdn.url.path/bcapp/et7xe3pz/products/32/images/247/in_123__14581.1393831046.1280.1280.jpg?c=1",
    "thumbnail_url": "https://cdn.url.path/bcapp/et7xe3pz/products/32/images/247/in_123__14581.1393831046.220.290.jpg?c=1",
    "standard_url": "https://cdn.url.path/bcapp/et7xe3pz/products/32/images/247/in_123__14581.1393831046.386.513.jpg?c=1",
    "tiny_url": "https://cdn.url.path/bcapp/et7xe3pz/products/32/images/247/in_123__14581.1393831046.44.58.jpg?c=1"
  },
  "availability": "available",
  "brand": {
    "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/brands/17.json",
    "resource": "/brands/17"
  },
  "images": {
    "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/products/32/images.json",
    "resource": "/products/32/images"
  },
  "discount_rules": {
    "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/products/32/discountrules.json",
    "resource": "/products/32/discountrules"
  },
  "configurable_fields": {
    "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/products/32/configurablefields.json",
    "resource": "/products/32/configurablefields"
  },
  "custom_fields": {
    "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/products/32/customfields.json",
    "resource": "/products/32/customfields"
  },
  "videos": {
    "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/products/32/videos.json",
    "resource": "/products/32/videos"
  },
  "skus": {
    "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/products/32/skus.json",
    "resource": "/products/32/skus"
  },
  "rules": {
    "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/products/32/rules.json",
    "resource": "/products/32/rules"
  },
  "option_set": null,
  "options": {
    "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/products/32/options.json",
    "resource": "/products/32/options"
  },
  "tax_class": {
    "url": "https://store-et7xe3pz.mybigcommerce.com/api/v2/taxclasses/0.json",
    "resource": "/taxclasses/0"
  }
}
```

### <span class="jumptarget"> Get a Product Count </span>

Gets a count of products.

*   OAuth 
> `GET /stores/{store_hash}/v2/products/count`
*   Basic Auth
> `GET /api/v2/products/count`

#### <span class="jumptarget"> Filters </span>

Filter parameters can be added to the URL query string to select specific products in the collection.

| Parameter | Type | Example |
| --- | --- | --- |
| min_id | int | /api/v2/products?min_id={value} |
| max_id | int | /api/v2/products?max_id={value} |
| name | string | /api/v2/products?name={value} |
| keyword_filter | string | /api/v2/products?keyword_filter={value} |
| description | string | /api/v2/products?description={value} |
| sku | string | /api/v2/products?sku={value} |
| condition | string | /api/v2/products?condition={value} |
| availability | string | /api/v2/products?availability={value} |
| brand_id | string | /api/v2/products?brand_id={value} |
| min_date_created | date | /api/v2/products?min_date_created={value} |
| max_date_created | date | /api/v2/products?max_date_created={value} |
| min_date_modified | date | /api/v2/products?min_date_modified={value} |
| max_date_modified | date | /api/v2/products?max_date_modified={value} |
| min_date_last_imported | date | /api/v2/products?min_date_last_imported={value} |
| max_date_last_imported | date | /api/v2/products?max_date_last_imported={value} |
| min_price | decimal | /api/v2/products?min_price={value} |
| max_price | decimal | /api/v2/products?max_price={value} |
| min_number_sold | int | /api/v2/products?min_number_sold={value} |
| max_number_sold | int | /api/v2/products?max_number_sold={value} |
| is_visible | string | /api/v2/products?is_visible={value} |
| is_featured | string | /api/v2/products?is_featured={value} |
| min_inventory_level | int | /api/v2/products?min_inventory_level={value} |
| max_inventory_level | int | /api/v2/products?max_inventory_level={value} |
| include_sku | boolean | /api/v2/products?include_sku={value} |
| category | string | /api/v2/products?category={value} |
| product_tax_code | string | /api/v2/products?product_tax_code={value} |

#### <span class="jumptarget"> Notes </span>

If no filters are applied, the total number of products is returned.

#### <span class="jumptarget"> Response </span>

Example JSON returned in the response:

```json
{
  "count": 44
}
```

### <span class="jumptarget"> Create a Product </span>

Creates a new product. The example request shows how to create a basic product by sending a [product object](#product-object-properties) with the minimum required properties.

*   OAuth 
> `POST /stores/{store_hash}/v2/products`
*   Basic Auth
> `POST /api/v2/products`

#### <span class="jumptarget"> Read-only Properties </span>

The following properties of the product are read-only. If one or more of these properties are included in the request, it will be rejected.

*   id
*   calculated_price
*   brand
*   images
*   discount_rules
*   configurable_fields
*   custom_fields
*   primary_image
*   videos
*   skus
*   rules
*   option_set
*   options
*   tax_class

#### <span class="jumptarget"> Requirements </span>

The following properties of the product are required. The request won’t be fulfilled unless these properties are valid.

*   name
*   price
*   categories
*   type
*   availability
*   weight

#### <span class="jumptarget"> Notes </span>

Create a request by sending a [product object](#product-object-properties) with the minimum required properties:

```json
{
    "name": "Plain T-Shirt",
    "type": "physical",
    "description": "This timeless fashion staple will never go out of style!",
    "price": "29.99",
    "categories": [18],
    "availability": "available",
    "weight": "0.5"
}
```

When the `is_visible` property is not provided, the product's visibility is `false` by default.

To make newly created products immediately visible on the storefront, you must set `is_visible` to `true` when you create each product.

To maximize system performance, BigCommerce caps the number of categories to which a product can belong. The maximum is 1,000. If your `POST` includes an array of more than 1,000 `categories` ID values, BigCommerce will return a 403 error:

```
403 Access Denied/Forbidden
```

If automatic tax is enabled on the store, the value of `tax_class_id` will have no effect on the calculation of taxes.

### <span class="jumptarget"> Update a Product </span>

Updates an existing product.

*   OAuth 
> `PUT /stores/{store_hash}/v2/products/{id}`
*   Basic Auth
> `PUT /api/v2/products/{id}`

#### <span class="jumptarget"> Read-only Properties </span>

The following properties of the product are read-only. If one or more of these properties are included in the request, it will be rejected.

*   id
*   rating_total
*   rating_count
*   number_sold
*   date_created
*   date_modified
*   date_last_imported
*   calculated_price
*   brand
*   images
*   discount_rules
*   configurable_fields
*   custom_fields
*   primary_image
*   videos
*   skus
*   rules
*   option_set
*   options
*   tax_class

#### <span class="jumptarget"> Requirements </span>

There are no required properties when updating a product.

#### <span class="jumptarget"> Notes </span>

To update a product, set one or more [product properties](#product-object-properties) in the `PUT` request:

```json
{
    "custom_url": "/plain-tshirt/",
    "is_visible": true
}
```

For example, you can use a `PUT` to link a product to an option set:

```json
{
    "option_set_id": 14
}
```

Invalid property values will produce a `400 Bad Request` error response:

#### <span class="jumptarget"> Request </span>

```json 
{
    "condition": "Worn"
}
```

#### <span class="jumptarget"> Response </span>

```
400 Bad Request
```

Trying to set read-only properties will also produce a `400 Bad Request` error response:

#### <span class="jumptarget"> Request </span>

```json
{
    "number_sold": 99
}
```

#### <span class="jumptarget"> Response </span>

```
400 Bad Request
```

To maximize system performance, BigCommerce caps the maximum number of categories to which a product can belong, at 1,000. If your `PUT` includes an array of more than 1,000 `categories` ID values, BigCommerce will return a `403` error:

```
403 Access Denied/Forbidden
```

If automatic tax is enabled on the store, the value of `tax_class_id` will have no effect on the calculation of taxes.

### <span class="jumptarget"> Delete a Product </span>

Deletes a product.

*   OAuth 
> `DELETE /stores/{store_hash}/v2/products/{id}`
*   Basic Auth
> `DELETE /api/v2/products/{id}`

#### <span class="jumptarget"> Notes </span>

Successful deletion of a product returns a `204 No Content` response:

```
204 No Content
```

### <span class="jumptarget"> Delete All Products </span>

Deletes all products from the store.

*   OAuth 
> `DELETE /stores/{store_hash}/v2/products`
*   Basic Auth
> `DELETE /api/v2/products`

#### <span class="jumptarget"> Notes </span>

Successful deletion of all products returns a `204 No Content` response:

```
204 No Content
```
