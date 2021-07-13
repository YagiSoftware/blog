---
layout: post
title: How to show text message in order status (thank you) page
date: 2021-07-13 20:31 +0800
image: https://mugshotbot.com/m/AKOkh1ZJ
---

If your product got backordered or got shipment delayed, displaying the delayed delivery date on the order status (thank you / tracking) page could be a good way to inform customer.

To display text on the order status page, go to your Shopify store admin > **Settings** > **Checkout**

![checkout settings](https://yagisoftware.s3.amazonaws.com/3-how-to-show-text-message-in-order-status-page/checkout_script_1.png)

Then scroll down to **Order processing** section, and find the **Additional scripts** field.

![checkout additional script](https://yagisoftware.s3.amazonaws.com/3-how-to-show-text-message-in-order-status-page/checkout_script_2.png)


Then paste in the following code into the **Additional scripts** field : 

```html
<script>
  Shopify.Checkout.OrderStatus.addContentBox(
   '<h2>Notice</h2>',
   '<p>Your message here</p>'
  )
</script>

```

Click save, then you can view this text in the order status page. You can select an order in the admin, then select "More actions" > "View order status page" to view the order status page.
![view order status page](https://yagisoftware.s3.amazonaws.com/3-how-to-show-text-message-in-order-status-page/view_order_status.png)


```
<script>
  {% if order.metafields.delay.message != blank %}
    Shopify.Checkout.OrderStatus.addContentBox(
     '<h2>Notice</h2>',
     '<p>{{ order.metafields.delay.message }}</p>'
    )
  {% endif %}
</script>

```