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
    "body_html": "<p>A rugged, lightweight hiking backpack.</p>",
    "vendor": "Outdoor Supply Co",
    "product_type": "Backpacks",
    "created_at": "2025-08-26T12:34:56Z",
    "handle": "hiking-backpack",
    "updated_at": "2025-08-26T12:34:56Z",
    "published_at": "2025-08-26T12:34:56Z",
    "template_suffix": null,
    "status": "active",
    "published_scope": "web",
    "tags": "outdoor, gear",
    "admin_graphql_api_id": "gid://shopify/Product/11235813213455",
    "variants": [
      {
        "id": 16180339887498,
        "product_id": 11235813213455,
        "title": "Black",
        "price": "99.99",
        "sku": "HB-001-BLK",
        "position": 1,
        "inventory_policy": "deny",
        "compare_at_price": null,
        "fulfillment_service": "manual",
        "inventory_management": "shopify",
        "option1": "Black",
        "option2": null,
        "option3": null,
        "created_at": "2025-08-26T12:34:56Z",
        "updated_at": "2025-08-26T12:34:56Z",
        "taxable": true,
        "barcode": "0123456789",
        "grams": 800,
        "image_id": 987654321,
        "weight": 0.8,
        "weight_unit": "kg",
        "inventory_item_id": 2233311419,
        "inventory_quantity": 25,
        "old_inventory_quantity": 25,
        "requires_shipping": true,
        "admin_graphql_api_id": "gid://shopify/ProductVariant/16180339887498"
      }
    ],
    "options": [
      {
        "id": 46910141521222530,
        "product_id": 11235813213455,
        "name": "Color",
        "position": 1,
        "values": ["Black", "Green"]
      }
    ],
    "images": [
      {
        "id": 987654321,
        "product_id": 11235813213455,
        "position": 1,
        "created_at": "2025-08-26T12:34:56Z",
        "updated_at": "2025-08-26T12:34:56Z",
        "alt": "Hiking backpack front view",
        "width": 1000,
        "height": 1200,
        "src": "https://cdn.shopify.com/s/files/backpack-front.jpg",
        "variant_ids": [16180339887498],
        "admin_graphql_api_id": "gid://shopify/ProductImage/987654321"
      }
    ],
    "image": {
      "id": 987654321,
      "product_id": 11235813213455,
      "position": 1,
      "created_at": "2025-08-26T12:34:56Z",
      "updated_at": "2025-08-26T12:34:56Z",
      "alt": "Hiking backpack front view",
      "width": 1000,
      "height": 1200,
      "src": "https://cdn.shopify.com/s/files/backpack-front.jpg",
      "variant_ids": [16180339887498],
      "admin_graphql_api_id": "gid://shopify/ProductImage/987654321"
    }
  }
}
```

---

## Notes

- `id` — unique product ID (numeric).  
- `admin_graphql_api_id` — Shopify GraphQL global ID for this product.  
- `variants` — array of variant objects with pricing, inventory, and shipping info.  
- `options` — array of product options (size, color, etc.).  
- `images` — array of product images.  
- `image` — the featured image.  
- `variant_ids` inside each image shows which variants use that image.  
- `variant.image_id` matches an `images[].id`.  

---

## References

- [Shopify Admin REST API Docs](https://shopify.dev/docs/api/admin-rest/latest/resources/product)
- [Shopify Product Image Docs](https://shopify.dev/docs/api/admin-rest/latest/resources/product-image)
