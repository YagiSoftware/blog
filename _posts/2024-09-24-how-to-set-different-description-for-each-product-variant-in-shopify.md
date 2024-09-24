---
layout: post
title: How to set different description for each product variant in Shopify
description: First, we will create a metafield definiton for variants, to store the description unique for each variant. Go to your store settings, select Custom Data on the left side bar, and click Variants ...
date: 2024-09-24 10:27 +0800
image: https://img.yagisoftware.com/30-variant-description/cover.png
---

By default, Shopify will show the same product description for all variants, despite the variants having different contents. One common workaround is to put all variants information into the product description, but this would make it harder for the customer to read information relevant to the variant of their interest.

Wouldn't it be good if we can show different variant description when customer selects different variant? This tutorial will guide you on implementing different variant description using variant metafields and some custom code. (No apps required)

![Different description shown to different variant](https://img.yagisoftware.com/30-variant-description/end-result.gif)

## Create metafield definition for variant to store the description

First, we will create a metafield definiton for variants, to store the description unique for each variant. Go to your store settings, select "Custom Data" on the left side bar, and click "Variants":

![Click custom data in store settings, and click variants](https://img.yagisoftware.com/30-variant-description/variant_metafield1.png)

Then click "Add definiton":
![Click add definition](https://img.yagisoftware.com/30-variant-description/variant_metafield2.png)

In the definition form, input **Variant Description** for the "Name" field, and ensure the "Namespace and key" field value is **custom.variant_description**, and select "Rich text" for the type, and remember to enable "Storefront access" (set to "Read"), so the theme code can access this value later on. Click "Save" to save the changes.
![Set the metafield key and value and value type](https://img.yagisoftware.com/30-variant-description/variant_metafield3.png)

Next, go to the product variants you want to edit the description (Online Stores > Product, and select your product, and scroll to the variants), click on the variant, and scroll down to "Metafields" section, and click "View all", then edit the "Variant Description" as you like :

![Click into specific variant](https://img.yagisoftware.com/30-variant-description/variant_metafield4.png)
![Set metafields definition](https://img.yagisoftware.com/30-variant-description/variant_metafield5.png)

## Add custom code to show the variant description in product page

Next, we will customize the product page in the Theme Editor, to add code to show the variant description.

Go to your Shopify Admin, select "Online Store" > "Themes", then go to your current theme, and click "Customize": 
![Go to Online Store, Themes, and click Customize](https://img.yagisoftware.com/19-terms-checkbox/1customize_theme.png)

Then navigate to the product page template : 
![Navigate to product page template](https://img.yagisoftware.com/30-variant-description/product_template1.png)

Change the product preview to a product that has variants (the product variant description which you have edited in earlier steps), then click "Add block" under the "Product information" section.
![Add block in the product information section](https://img.yagisoftware.com/30-variant-description/product_template2.png)

Select "Custom Liquid" :
![select custom liquid](https://img.yagisoftware.com/30-variant-description/product_template3.png)

Next, click into the "Custom Liquid" block, 

![Click into custom liquid](https://img.yagisoftware.com/30-variant-description/click_custom_liquid.png)

And add this code : 

{% raw %}
```liquid
{% for variant in product.variants %}
<div class="yagi-variant-description" data-variant-id="{{ variant.id }}" style="display:none;">
  {{ variant.metafields.custom.variant_description | metafield_tag }}
</div>
{% endfor %}

<script>
function yagiHideAllVariantDescriptionExcept(variant){
  document.querySelectorAll('.yagi-variant-description').forEach(el => {
    el.style.display = 'none';
  });

  const descriptionEl = document.querySelector(`.yagi-variant-description[data-variant-id="${variant}"]`);
  if (descriptionEl){ descriptionEl.style.display = 'block'; }
}

const queryString = location.search;
const urlParams = new URLSearchParams(queryString);
var variantId = '{{ product.variants.first.id }}';

if(urlParams.get('variant')){
  variantId = urlParams.get('variant');
}

yagiHideAllVariantDescriptionExcept(variantId);

document.addEventListener("DOMContentLoaded", (event) => {
  document.querySelector("input[type='hidden'].product-variant-id").addEventListener('change', yagiVariantChanged);
});

function yagiVariantChanged() {
  if (document.querySelector('.product-variant-id')?.value !== variantId) {
    variantId = document.querySelector('.product-variant-id')?.value;

    if(!variantId) { variantId == '{{ product.variants.first.id }}' }
    yagiHideAllVariantDescriptionExcept(variantId);
  }
}
</script>
```
{% endraw %}


Save the changes, then you should see the variant description appear in the product page. Different variant description will appear based on your selection of variant.

Next, you can reposition the variant description block (custom liquid) to the position you want, by dragging it in the Theme customizer.
![Reposition the block](https://img.yagisoftware.com/30-variant-description/product_template4.png)


And now you can go to the actual product page on your store, and see the variant description in action.