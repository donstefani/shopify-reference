# Shopify Liquid — Product Object Reference

This document provides a **quick reference** for the `product` object available in Shopify Liquid templates.  
This is what themes use to render product details on the storefront.

---

## Basic Properties

```liquid
{{ product.id }}            <!-- Numeric product ID -->
{{ product.title }}         <!-- Product title -->
{{ product.handle }}        <!-- Product handle (URL-friendly) -->
{{ product.vendor }}        <!-- Product vendor -->
{{ product.product_type }}  <!-- Product type -->
{{ product.description }}   <!-- Plain text description -->
{{ product.description_html }} <!-- HTML description -->
{{ product.tags }}          <!-- Tags -->
{{ product.url }}           <!-- Product URL -->
{{ product.featured_image }} <!-- Featured image object -->
```

---

## Variants

```liquid
{% for variant in product.variants %}
  {{ variant.id }}
  {{ variant.title }}
  {{ variant.sku }}
  {{ variant.price | money }}
  {% if variant.image %}
    <img src="{{ variant.image | img_url: 'medium' }}" alt="{{ variant.image.alt }}">
  {% endif %}
{% endfor %}
```

- `variant.image` → linked product image (if set).  
- Falls back to `product.featured_image` if not set.

---

## Images

```liquid
{% for image in product.images %}
  <img src="{{ image | img_url: 'medium' }}" alt="{{ image.alt }}">
{% endfor %}
```

- `product.images` → array of product image objects.  
- Each `image` has: `id`, `alt`, `src`, `width`, `height`, etc.

---

## Options

```liquid
{% for option in product.options %}
  <h4>{{ option.name }}</h4>
  {% for value in option.values %}
    <span>{{ value }}</span>
  {% endfor %}
{% endfor %}
```

- Represents product options (like Size, Color).  
- `option.values` contains the available values for that option.

---

## Collections

```liquid
{% for collection in product.collections %}
  <a href="{{ collection.url }}">{{ collection.title }}</a>
{% endfor %}
```

- Lists the collections the product belongs to.  

---

## SEO

```liquid
{{ product.metafields_global_title_tag }}
{{ product.metafields_global_description_tag }}
```

- Used for customizing SEO title and description.  

---

## Notes

- Liquid `product` object is optimized for **theme rendering**, not API usage.  
- Some fields (like `inventoryQuantity` or `admin_graphql_api_id`) are **not available** in Liquid.  
- Use REST/GraphQL Admin APIs for full programmatic access.  

---

## References

- [Shopify Liquid Objects — Product](https://shopify.dev/docs/api/liquid/objects/product)
