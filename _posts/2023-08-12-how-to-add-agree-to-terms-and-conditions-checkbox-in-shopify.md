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

Go to your store Shopify Admin, then select "Online Store" > "Theme", go to your current theme and select "Edit Code" :
![Edit code on current Shopify theme](https://img.yagisoftware.com/16-only-show-product-certain-customer/3edit_code.png)

Then click the "Snippets" folder on the left side bar, and click "Add a new snippet", then name the file "**cart-termsbox**" (must be exactly this), and click "Done".
![Add snippets](https://img.yagisoftware.com/19-terms-checkbox/9add_snippets.png)

Then open this link (<a href="https://github.com/YagiSoftware/termsbox/blob/master/snippets/cart-termsbox.liquid" target="_blank">cart-termsbox.liquid</a>), and copy the code there and paste it in your newly created snippet file.

![Paste code](https://img.yagisoftware.com/19-terms-checkbox/10paste_code.png)


Next, in the Theme Editor, search for "main-cart-footer", then open the  "main-cart-footer.liquid" file, and scroll to the bottom, and paste this code right before the `{ "type": "@app" }` part :

```
{
  "type": "termsbox",
  "name": "Termsbox",
  "limit": 1,
  "settings": [
    {
      "id": "prelink_text",
      "type": "text",
      "label": "Text before the link to the terms",
      "default": "I have read"
    },
    {
      "id": "link_text",
      "type": "text",
      "label": "The link text of the terms",
      "default": "Terms and Conditions"
    },
    {
      "id": "postlink_text",
      "type": "text",
      "label": "Text after the link to the terms",
      "default": " and agree"
    },
    {
      "id": "terms_page",
      "type": "page",
      "label": "Terms and Conditions page"
    },
    {
      "type": "range",
      "id": "checkbox_scale",
      "min": 1,
      "max": 3,
      "step": 0.1,
      "label": "Checkbox size",
      "default": 1.2
    },
    {
      "type": "checkbox",
      "id": "mandatory",
      "label": "Customer must check the checkbox to checkout",
      "default": true
    },
    {
      "id": "internal_label",
      "type": "text",
      "label": "Internal label that will be shown in the order's Additional Details",
      "default": "Customer agreed to terms"
    }
  ]
},
```

![Main cart footer](https://img.yagisoftware.com/19-terms-checkbox/11main-cart-footer.png)


Click "Save", then in the same file, search for this text `when '@app'` (You can press Control + F to search, or Command + F if you are using Mac).

Then you can add the following code, after the `render block` line that is below `when '@app'` : 

{% raw %}
```liquid
{%- when 'termsbox' -%}
  <div {{ block.shopify_attributes }}>
    {% render 'cart-termsbox' , block: block %}
  </div>
```
{% endraw %}

![block case when paste code](https://img.yagisoftware.com/19-terms-checkbox/12when.png)


Click "Save", and now you have successfully added the terms and agreement checkbox snippet! In the next section, we will enable the checkbox in the Theme Editor.

## Enable and customize the terms checkbox in Theme Editor


<!-- ensure customer will go to the cart page -->
<!-- disable cart drawer, make when click cart icon, go to cart page -->
<!-- hide "buy now" option on the product page -->