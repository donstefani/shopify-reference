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
          image {
            id
            url
            altText
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
              ],
              "image": {
                "id": "gid://shopify/ProductImage/5566778899",
                "url": "https://cdn.shopify.com/s/files/backpack.jpg",
                "altText": "Hiking backpack"
              }
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

## Mutating the Variant ↔ Image Relationship

Unlike REST (which uses `variant.image_id` and `image.variant_ids`), GraphQL only supports linking **from the variant to the image**.

To associate an image with a variant:

```graphql
mutation {
  productVariantUpdate(input: {
    id: "gid://shopify/ProductVariant/16180339887498",
    imageId: "gid://shopify/ProductImage/5566778899"
  }) {
    productVariant {
      id
      image {
        id
        url
      }
    }
    userErrors {
      field
      message
    }
  }
}
```

---

## Notes

- `variant.image` gives you the linked image.  
- GraphQL does **not** expose `variant_ids` on `ProductImage` (one-directional only).  
- To reassign, use `productVariantUpdate` with a new `imageId`.  
- If no variant-specific image is set, themes fall back to the product’s `featuredImage`.  

---

## References

- [Shopify Admin GraphQL API Docs](https://shopify.dev/docs/api/admin-graphql/latest/objects/Product)
- [Shopify ProductVariant Update Mutation](https://shopify.dev/docs/api/admin-graphql/latest/mutations/productVariantUpdate)
- [Shopify GraphQL Pagination](https://shopify.dev/docs/api/usage/pagination-graphql)
