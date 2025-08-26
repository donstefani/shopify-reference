# Shopify Admin REST API — Product Object (2025‑07)

This document provides a **complete reference example** of the Shopify Product object 
as returned by the **Admin REST API (2025‑07 version)**.

---

## Example JSON Response

```jsonc
{
  "product": {
    "id": 11235813213455,
    "title": "Hiking backpack",
    "body_html": null,
    "vendor": "",
    "product_type": "",
    "created_at": "2025-08-26T12:34:56Z",
    "handle": "hiking-backpack",
    "updated_at": "2025-08-26T12:34:56Z",
    "published_at": "2025-08-26T12:34:56Z",
    "template_suffix": null,
    "status": "active",
    "published_scope": "web",
    "tags": "",
    "admin_graphql_api_id": "gid://shopify/Product/11235813213455",
    "variants": [
      {
        "id": 16180339887498,
        "product_id": 11235813213455,
        "title": "Default Title",
        "price": "0.00",
        "sku": "",
        "position": 1,
        "inventory_policy": "deny",
        "compare_at_price": null,
        "fulfillment_service": "manual",
        "inventory_management": null,
        "option1": "Default Title",
        "option2": null,
        "option3": null,
        "created_at": "2025-08-26T12:34:56Z",
        "updated_at": "2025-08-26T12:34:56Z",
        "taxable": true,
        "barcode": null,
        "grams": 0,
        "image_id": null,
        "weight": 0,
        "weight_unit": "kg",
        "inventory_item_id": 2233311419,
        "inventory_quantity": 0,
        "old_inventory_quantity": 0,
        "requires_shipping": true,
        "admin_graphql_api_id": "gid://shopify/ProductVariant/16180339887498"
      }
    ],
    "options": [
      {
        "id": 46910141521222530,
        "product_id": 11235813213455,
        "name": "Title",
        "position": 1,
        "values": ["Default Title"]
      }
    ],
    "images": [],
    "image": null
  }
}
```

---

## Notes

- `id` — unique product ID (numeric).  
- `admin_graphql_api_id` — Shopify GraphQL global ID for this product.  
- `variants` — array of variant objects with pricing, inventory, and shipping info.  
- `options` — array of product options (size, color, etc.).  
- `images` / `image` — product media references.  
- `status` — one of `active`, `draft`, or `archived`.  
- `published_scope` — typically `"web"`.  

---

## References

- [Shopify Admin REST API Docs](https://shopify.dev/docs/api/admin-rest/latest/resources/product)
- [Shopify GraphQL Admin API Docs](https://shopify.dev/docs/api/admin-graphql/latest/objects/Product)
