---
layout: post
title: How to add shipping method / delivery method name to packing slip in Shopify
date: 2024-07-27 14:45 +0800
image: https://yagisoftware.s3.amazonaws.com/26-delivery-method-packing-slip/cover.png

description: Go to your store Settings, click Shipping and Delivery, click Packing slip template and add this line below shipping address
---

If your store uses multiple delivery carriers, it can be crucial to show the shipping method (carrier name) on the packing slip, to ensure the parcel is posted into the right delivery carrier.

This tutorial will guide you to place the shipping method text in the packing slip like this : 

![Delivery method on packing slip](https://yagisoftware.s3.amazonaws.com/26-delivery-method-packing-slip/delivery_method_packing_slip.png)

To edit the packing slip template, you can go to your store Settings > <strong>Shipping and Delivery</strong>, scroll to the "Packing Slips" section, and click <strong>Packing slip template</strong> .

![Edit packing slip template](https://yagisoftware.s3.amazonaws.com/26-delivery-method-packing-slip/settings-packingslip.png)

In the template code, search for the line `<div class="shipping-address">` , then add this line below it
{% raw %}
```liquid
<h2 class="">{{ order.shipping_method.title }}</h2>
```
{% endraw %}

![Add the line of code below the shipping-address div](https://yagisoftware.s3.amazonaws.com/26-delivery-method-packing-slip/shipping_address.png)

<br>

Next, search for the line `<div class="billing-address">` , then add this line below it
{% raw %}
```liquid
<h2>&nbsp;</h2>
```
{% endraw %}

![Add the line of code below the billing-address div](https://yagisoftware.s3.amazonaws.com/26-delivery-method-packing-slip/billing_address.png)

After inserting this two line, click "Save". As the "Preview template" button does not show the shipping method, we will need to go to an actual order and preview it.

![Preview packing slip](https://yagisoftware.s3.amazonaws.com/26-delivery-method-packing-slip/preview.png)

In the generated packing slip, you should now see the shipping method / delivery method there.

