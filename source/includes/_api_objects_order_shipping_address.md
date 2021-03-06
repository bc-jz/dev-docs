## <span class="jumptarget"> Order Shipping Addresses </span>

Customer shipping address belonging to an order.

### <span class="jumptarget"> Order Shipping Address Object – Properties </span>

| Name | Type | Description |
| --- | --- | --- |
| id | int |
| order_id | int |
| first_name | string |
| last_name | string |
| company | string |
| street_1 | string |
| street_2 | string |
| city | string |
| zip | string |
| country | string |
| country_iso2 | string |
| state | string | The name of the state. Should be spelled out in full, e.g.: `California`. |
| email | string |
| phone | string |
| items_total | int |
| items_shipped | int |
| shipping_method | string |
| base_cost | decimal |
| cost_ex_tax | decimal |
| cost_inc_tax | decimal |
| cost_tax | decimal |
| cost_tax_class_id | int |
| base_handling_cost | decimal |
| handling_cost_ex_tax | decimal |
| handling_cost_inc_tax | decimal |
| handling_cost_tax | decimal |
| handling_cost_tax_class_id | int |
| shipping_zone_id | int |
| shipping_zone_name | string |
