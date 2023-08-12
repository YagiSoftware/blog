---
layout: post
title: How to add agree to terms and conditions checkbox in Shopify
date: 2023-08-12 00:00 +0800
---

Notice: This tutorial adds the checkbox on the cart page (not the checkout page, as modifying the checkout page requires Shopify Plus plan), and this tutorial assumes your store is using newer themes that is Online Store 2.0 compatible like Dawn (or other newer themes that support blocks).

At the end of tutorial, you will be able to add a checkbox for customer to agree to terms and conditions in the cart page like this :

![Terms checkbox demo](https://img.yagisoftware.com/19-terms-checkbox/checkbox_demo.gif)

When customer checks the checkbox and place an order, the order will contain the time which the customer has checked the checkbox, this can be useful as proof in case of any legal dispute.

![Proof of checked box](https://img.yagisoftware.com/19-terms-checkbox/yes_check.png)
<!-- Gifs of showing the effect -->

<!-- proof of checkbox checked -->

<br><br>

## Ensure customers will go to cart page before checking out

As the terms and agreement checkbox only appears in the cart page, we have to ensure that customers will visit the cart page before checking out, this means that we have to disable the "Buy Now" button in the product page, and also disable the Cart drawer by redirecting customer to the cart page when they click on the cart icon.


Go to your Shopify Admin, select "Online Store" > "Themes", then go to your current theme, and click "Customize": 
![Go to Online Store, Themes, and click Customize](https://img.yagisoftware.com/19-terms-checkbox/1customize_theme.png)


In the Theme Editor, navigate to "Products" > "Default product" page :
![Select the "Products", "Default product" template](https://img.yagisoftware.com/19-terms-checkbox/2select_products.png)


On the product page, select "Buy buttons" on the left side bar :
![Select the buy buttons](https://img.yagisoftware.com/19-terms-checkbox/3select_buy_buttons.png)

Uncheck the "Show dynamic checkout buttons", this will hide the "Buy Now" button on the product page. (Customer can only add product to cart, and must navigate to cart page to check the checkbox and checkout)
![Disable dynamic checkout on product page](https://img.yagisoftware.com/19-terms-checkbox/4disable_dynamic_checkout.png)

Then click the "Settings" icon on the left side bar in the Theme editor, go to the "Cart" section, and select "Page" or "Popup Notification" for the cart type. (I recommend selecting the "Popup Notification" as customer won't get redirected to cart page immediately after adding item to cart)
![Select "page" or "popup notification" for cart type](https://img.yagisoftware.com/19-terms-checkbox/5cart_type.png)

### Hide the Checkout button from the notification drawer

If you have selected "Popup notification" in the previous step, you will need to hide the checkout button from the notification drawer.

To hide the checkout button, click the three dots from the Theme Editor, and select "Edit code " :

![Select "Edit code" from the Theme Editor](https://img.yagisoftware.com/19-terms-checkbox/6edit_code.png)

In the code editor, search for "base.css", then click the "base.css" file, and add the following snippet to the top of the file :

```css
/* hide the checkout button from notification drawer */
.cart-notification__links button[name="checkout"] {
  display: none !important;
}
```

![Insert the following code in the base.css file](https://img.yagisoftware.com/19-terms-checkbox/7hide_checkout.png)


Click "Save" to save the changes, and the Checkout button is now hidden from the notification drawer.

![Before and after the code](https://img.yagisoftware.com/19-terms-checkbox/8before_after.png)

<br><br>

## Add the terms and agreement checkbox snippet
<!-- ensure customer will go to the cart page -->
<!-- disable cart drawer, make when click cart icon, go to cart page -->
<!-- hide "buy now" option on the product page -->