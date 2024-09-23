---
layout: post
title: How to set different description for each product variant in Shopify
date: 2024-09-21 18:27 +0800
---

By default, Shopify will show the same product description for all variants, despite the variants having different contents. One common workaround is to put all variants information into the product description, but this would make it harder for the customer to read information relevant to the variant of their interest.

Wouldn't it be good if we can show different variant description when customer selects different variant? This tutorial will guide you on implementing different variant description using variant metafields and some custom code. (No apps required)

![Different description shown to different variant](https://img.yagisoftware.com/30-variant-description/end-result.gif)

## Create metafield definition for variant to store the description

First, we will create a metafield definiton for variants, to store the description unique for each variant.

![Variant metafield](https://img.yagisoftware.com/30-variant-description/variant_metafield1.png)
![Variant metafield](https://img.yagisoftware.com/30-variant-description/variant_metafield2.png)
![Variant metafield](https://img.yagisoftware.com/30-variant-description/variant_metafield3.png)
![Variant metafield](https://img.yagisoftware.com/30-variant-description/variant_metafield4.png)
![Variant metafield](https://img.yagisoftware.com/30-variant-description/variant_metafield5.png)