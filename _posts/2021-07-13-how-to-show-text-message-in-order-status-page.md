---
layout: post
title: How to show text message in order status (thank you) page
date: 2021-07-13 20:31 +0800
image: https://mugshotbot.com/m/lQh9xE8i
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

![order status page message](https://yagisoftware.s3.amazonaws.com/3-how-to-show-text-message-in-order-status-page/message.png)

[Official Shopify documentation on the addContentBox function](https://help.shopify.com/en/manual/orders/status-tracking/customize-order-status/order-status-javascript-asset)

## Show different message on different order
Say, you have different delayed shipping date for different order, how do you show them on the order status page instead of a fixed text message?


To assign different message to different order, we can make use of the [metafields](https://www.shopify.my/partners/blog/110057030-using-metafields-in-your-shopify-theme) feature of Shopify, metafields are extra pieces of data that you can attach to products, customers, orders, and other objects in your Shopify store.

Currently Shopify doesn't have an official way to edit metafields for products, you would have to download third party apps to be able to edit metafields. I recommend using [Metafields Custom Field Master](https://apps.shopify.com/metafields-manager-by-hulkapps?) app to edit metafields, as they have a generous free plan that lets you add metafields to unlimited products, I will be using this app for the following steps.



After installing the Metafields app, open it :
![open metafields app](https://yagisoftware.s3.amazonaws.com/2-how-to-hide-products-from-search-in-shopify-store/mt1.png)



Then select "**Order**", and select the order you want to add custom message to.

You can set the **Namespace** and **Key** to any value you want, but make sure that they are the same for all the orders which you want to display message on the order status page. We will use the Namespace and Key value later. I have set the Namespace to **delay** and Key to **message**.

Set the **Type** to **String**, then type the message you want to display at the bottom text box, and click save.

![metafields namespace key value](https://yagisoftware.s3.amazonaws.com/3-how-to-show-text-message-in-order-status-page/metafield_value.png)


Now go back to the Settings > Checkout > Additional script field, and replace the code with below : 


{% raw %}
```html
<script>
  {% if order.metafields.delay.message != blank %}
    Shopify.Checkout.OrderStatus.addContentBox(
     '<h2>Notice</h2>',
     '<p>{{ order.metafields.delay.message }}</p>'
    )
  {% endif %}
</script>

```
{% endraw %}

This code will show the message on order status page only if we have set the metafields for it (Namespace 'delay' and Key 'message'), you can change the 'delay' and 'message' in the code above to the values you have set in the Namespace and Key earlier.


<script async data-uid="3f46096ca1" src="https://yagisoft.ck.page/3f46096ca1/index.js"></script>