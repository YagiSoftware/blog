---
layout: post
title: How to customize sorting options on collection page
date: 2021-07-19 16:08 +0800
image: https://mugshotbot.com/m/UAXj52qf
---

On most theme, the default sorting option on the collection / catalog page is "Alphabetically, A-Z", which products will be sorted from A to Z.

This default sorting option may not be ideal, it might be more appealing to show customers the best selling products or featured products.

This post will go over on how to set the default selected sorting option, and how to customize the available sorting options, like removing some option, or customize the text shown on the dropdown.

## How to change default sorting option on collection

If you have created collection, you can go to the collection and change the sorting option like this :

![sort option](https://yagisoftware.s3.amazonaws.com/4-how-to-customize-sorting-options-on-collection-page/collection2.png)

## How to change default sorting option on catalog / products page without coding

By default, all Shopify stores have a “Catalog” page which show all available products (with stock) in your store, this page is usually located in your-store.myshopify.com/collections/all .

You can override the default sorting option by creating a new collection and name its title as "**All**", and change the sorting option to the one you want.

![create collection](https://yagisoftware.s3.amazonaws.com/2-how-to-hide-products-from-search-in-shopify-store/collection1.png)

![collection all](https://yagisoftware.s3.amazonaws.com/4-how-to-customize-sorting-options-on-collection-page/collectionAll.png)

And use "Automated" Collection type, and use conditions of "Product price" is greater than 0, this will automatically match almost all your product in the store. 

![automated collection using price](https://yagisoftware.s3.amazonaws.com/4-how-to-customize-sorting-options-on-collection-page/collectionAllPrice.png)

![sort option](https://yagisoftware.s3.amazonaws.com/4-how-to-customize-sorting-options-on-collection-page/collection2.png)

## How to change default sorting option on catalog / products page with coding

If you don't want to create a new collection for the Catalog/ products page just for the sorting option, you can opt to edit the code of the collection page instead.

Select "Theme" > "Actions" > "Edit code"

![theme edit code](https://yagisoftware.s3.amazonaws.com/4-how-to-customize-sorting-options-on-collection-page/edit_code.png)


Open "**collection.liquid**", this file controls the layout of the collection page. Depending on the theme you use, some of them might include a different section for it, if there's a section in this file, then we will navigate to that file instead.

![collection.liquid](https://yagisoftware.s3.amazonaws.com/4-how-to-customize-sorting-options-on-collection-page/collection_template.png)

Next, search for "**collection.default_sort_by**", and find for the result that starts the line with {% raw %}"{% assign" {% endraw %}, which for the example below, is the

{% raw %}
  {%- assign sort_by = collection.sort_by | default: collection.default_sort_by -%}
{% endraw %}
  
line.


![default-sort-by](https://yagisoftware.s3.amazonaws.com/4-how-to-customize-sorting-options-on-collection-page/default_sort_by.png) 


We then proceed to add some code (the if and endif part) below it :

{% raw %}
```liquid
{%- assign sort_by = collection.sort_by | default: collection.default_sort_by -%}

{% if collection.handle == "all" %}
    {% assign sort_by = 'best-selling' %}
{% endif %}

```
{% endraw %}

The code above will make the sorting option to become "Best selling", if it is the catalog / product page.

You can change it to options listed below : (the 'best-selling' part shown above)

1. manual

2. best-selling

3. title-ascending

4. title-descending

5. price-ascending

6. price-descending

7. created-ascending

8. created-descending

WIP 🚧
