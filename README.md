# Shopify Product Object Reference

This repository contains **quick reference documentation** for the Shopify **Product object** across different contexts:

- **Admin REST API** — full JSON product object with variants, options, and images  
- **Admin GraphQL API** — GraphQL query/response format with product, variants, options, and images  
- **Liquid (Theme Layer)** — product object as available in themes (`product`, `variants`, `images`, `options`, `collections`)  

The goal of this project is to provide developers with a **clear and complete example** of the Product object structure, including variants, images, options, and related properties.  
These references are meant to be a practical aid for developers working with Shopify APIs or theme development.

---

## Files

- [shopify-product-object-reference-with-images.md](shopify-product-object-reference-with-images.md) — REST Admin API Product object reference  
- [shopify-graphql-product-object-reference-with-images.md](shopify-graphql-product-object-reference-with-images.md) — GraphQL Admin API Product object reference  
- [shopify-liquid-product-object-reference.md](shopify-liquid-product-object-reference.md) — Liquid Product object reference for themes  

---

## Visual Reference

![Shopify Product Object Relationships](shopify-product-relationships.png)  
*Diagram showing Product ↔ Variants ↔ Images relationships across REST, GraphQL, and Liquid.*

---

## Contributing

If you notice **anything missing, incorrect, or that could be improved**, please open an issue in this repository.  
Pull requests with corrections, improvements, or examples are also welcome!

---

## Disclaimer

These examples are **for reference purposes only**.  
Values shown are **sample data** and may differ depending on your store configuration, installed apps, or API version.

---

## References

- <a href="https://shopify.dev/docs/api/admin-rest/latest/resources/product" target="_blank">Shopify Admin REST API Docs</a>  
- <a href="https://shopify.dev/docs/api/admin-graphql/latest/objects/Product" target="_blank">Shopify Admin GraphQL API Docs</a>  
- <a href="https://shopify.dev/docs/api/liquid/objects/product" target="_blank">Shopify Liquid Product Object Docs</a>  

---

## Author

Created as a quick reference by a Shopify developer who wanted a **single, easy-to-use resource** for working with Product objects.  
If this helps you, consider leaving feedback or contributing improvements. 🚀
