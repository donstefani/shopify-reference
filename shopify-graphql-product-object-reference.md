# Shopify Admin GraphQL API — Product Object (2025‑07)

This document provides a **complete reference example** of the Shopify Product object 
as returned by the **Admin GraphQL API (2025‑07 version)**.

---

## Example GraphQL Query

```graphql
query getProduct($id: ID!) {
  product(id: $id) {
    id
    title
    descriptionHtml
    handle
    status
    vendor
    productType
    tags
    createdAt
    updatedAt
    publishedAt
    templateSuffix
    onlineStoreUrl
    featuredImage {
      id
      url
      altText
      width
      height
    }
    options(first: 5) {
      id
      name
      values
    }
    variants(first: 10) {
      edges {
        node {
          id
          title
          sku
          price
          compareAtPrice
          barcode
          weight
          weightUnit
          inventoryQuantity
          inventoryPolicy
          requiresShipping
          taxable
          createdAt
          updatedAt
          selectedOptions {
            name
            value
          }
        }
      }
    }
    images(first: 10) {
      edges {
        node {
          id
          url
          altText
          width
          height
        }
      }
    }
    collections(first: 5) {
      edges {
        node {
          id
          title
          handle
        }
      }
    }
    seo {
      title
      description
    }
  }
}
```

---

## Example JSON Response

```jsonc
{
  "data": {
    "product": {
      "id": "gid://shopify/Product/11235813213455",
      "title": "Hiking backpack",
      "descriptionHtml": "<p>A rugged, lightweight hiking backpack.</p>",
      "handle": "hiking-backpack",
      "status": "ACTIVE",
      "vendor": "Outdoor Supply Co",
      "productType": "Backpacks",
      "tags": ["outdoor", "gear"],
      "createdAt": "2025-08-26T12:34:56Z",
      "updatedAt": "2025-08-26T12:34:56Z",
      "publishedAt": "2025-08-26T12:34:56Z",
      "templateSuffix": null,
      "onlineStoreUrl": "https://example.myshopify.com/products/hiking-backpack",
      "featuredImage": {
        "id": "gid://shopify/ProductImage/5566778899",
        "url": "https://cdn.shopify.com/s/files/backpack.jpg",
        "altText": "Hiking backpack",
        "width": 1000,
        "height": 1200
      },
      "options": [
        {
          "id": "gid://shopify/ProductOption/334455",
          "name": "Color",
          "values": ["Black", "Green"]
        }
      ],
      "variants": {
        "edges": [
          {
            "node": {
              "id": "gid://shopify/ProductVariant/16180339887498",
              "title": "Black",
              "sku": "HB-001-BLK",
              "price": "99.99",
              "compareAtPrice": null,
              "barcode": "0123456789",
              "weight": 800,
              "weightUnit": "GRAMS",
              "inventoryQuantity": 25,
              "inventoryPolicy": "DENY",
              "requiresShipping": true,
              "taxable": true,
              "createdAt": "2025-08-26T12:34:56Z",
              "updatedAt": "2025-08-26T12:34:56Z",
              "selectedOptions": [
                { "name": "Color", "value": "Black" }
              ]
            }
          }
        ]
      },
      "images": {
        "edges": [
          {
            "node": {
              "id": "gid://shopify/ProductImage/5566778899",
              "url": "https://cdn.shopify.com/s/files/backpack.jpg",
              "altText": "Hiking backpack",
              "width": 1000,
              "height": 1200
            }
          }
        ]
      },
      "collections": {
        "edges": [
          {
            "node": {
              "id": "gid://shopify/Collection/123456",
              "title": "Outdoor Gear",
              "handle": "outdoor-gear"
            }
          }
        ]
      },
      "seo": {
        "title": "Hiking backpack",
        "description": "Lightweight and durable hiking backpack"
      }
    }
  }
}
```

---

## Notes

- `id` — global ID (GraphQL GID format).  
- `status` — GraphQL uses uppercase values (`ACTIVE`, `DRAFT`, `ARCHIVED`).  
- `options` and `variants` are connections (paginated with `first/after`).  
- `images` and `collections` are also connections.  
- `seo` is a nested object.  
- Some fields (like `unitPrice`, `presentmentPrices`, `sellingPlanGroups`) can be queried optionally for advanced pricing/subscriptions.  

---

## References

- [Shopify Admin GraphQL API Docs](https://shopify.dev/docs/api/admin-graphql/latest/objects/Product)
- [Shopify GraphQL Pagination](https://shopify.dev/docs/api/usage/pagination-graphql)
