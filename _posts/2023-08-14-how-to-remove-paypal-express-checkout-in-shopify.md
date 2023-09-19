---
layout: post
title: How to hide / remove Express Checkout buttons in Shopify
date: 2023-08-14 15:20 +0800
image: https://img.yagisoftware.com/20-hide-paypal-express/cover.png
description: After saving the configuration, the Express Checkout methods on the top will be hidden, but customer can still select the “Paypal” method after they have input their shipping address and selected shipping option 
---

[Click here to jump to solution](#hide-express-checkout-buttons-using-yagi-express-payment-hider-app)

When you set up a new Shopify store and configured Paypal, Shopify will automatically add these express checkout buttons on the top of the checkout page of your store :

![Express Payment buttons in Checkout page](https://img.yagisoftware.com/20-hide-paypal-express/2express_checkouts.png)

The problem with these express checkout buttons placed on top, is that it can confuse customers into thinking that these are the only payment methods available, and if they don't have these payment methods (eg: Paypal, or Google Pay), they will leave the checkout page in frustration, thinking that the store can't accept their payments, causing your store conversion rate to drop significantly! 💸


You might have came across solutions that instruct you to add code into the cart file like this :

```html
/* This does not work! */

{% raw %}
{% if additional_checkout_buttons %}
  <div class="additional-checkout-buttons">
    {{ content_for_additional_checkout_buttons }}
  </div>
{% endif %}
{% endraw %}

<style>
.additional-checkout-buttons { 
	display: none;
}
</style>
```
<br><Br>
Previously you can choose to show the express checkout buttons on your cart page (enable the "Show dynamic checkout buttons" in theme settings), and Shopify will automatically hide them on the Checkout page, and then you can insert CSS code above to hide the button on the cart page, so that Customers will not see the express checkout buttons on both the cart and checkout page.

Unfortunately this workaround does not work anymore after mid of 2022, as Shopify has changed how their system works. Worse, Shopify is planning to deprecate the checkout.liquid file, so that even if you are on a Shopify Plus plan, you will not be able to customize the checkout page and hide the express checkout buttons using HTML / CSS / JS code after August 2024.


What if there is a way to hide the express checkout buttons at the top of checkout, but customer still can select Paypal method in the payment selection step?

{% comment %}
The good news is that Shopify has released feature which lets app developers to use native code to remove certain payment methods. (not CSS workaround etc that might affect your store layout).
{% endcomment %}


## Hide Express Checkout buttons using Yagi Express Payment Hider app

Using [Yagi Express Payment Hider](https://apps.shopify.com/yagi-express-payment-hider) app, you can easily hide the express checkout buttons on the checkout page. (Disclaimer: I am the app developer of the app)


<div style="width: 100%; text-align: center;">
  <a href="https://apps.shopify.com/yagi-express-payment-hider" target="_blank"><img src="https://img.yagisoftware.com/Shopify-App-Store-Badge-Final-Black.png" style="max-width: 250px; border-radius: 0; box-shadow: none; border-width: 0;"></a>
</div>

<br><br>
After installing the app, you can configure to hide the express checkout buttons :
![Hide Express Payment in Checkout page](https://img.yagisoftware.com/20-hide-paypal-express/hide_express.gif)


The app hides the Express Checkout methods on the top, but customer can still select the "Paypal" method after they have input their shipping address and selected shipping option : 


![Paypal method remain selectable at the payment method selection step](https://img.yagisoftware.com/20-hide-paypal-express/1select_paypal.png)


The app uses native [Shopify functions](https://www.shopify.com/enterprise/shopify-functions) (official function that directly manipulate the output of available shipping methods / payment methods etc) to remove the express checkout buttons, which will not affect existing store functionality / layout (unlike some other HTML / CSS code workaround).

With [Yagi Express Payment Hider app](https://apps.shopify.com/yagi-express-payment-hider), you can remove the express checkout buttons and the top of checkout page, to reduce confusion of customers and checkout abandonment, and recover your revenue!

I understand it might be hard to trust a random app you came across on internet, you can refer to [these reviews on these other apps I made, from happy store owners](https://apps.shopify.com/partners/yagi-software), most of them has used my apps for many years and are very happy with it.

I have been in the business of serving Shopify merchants for more than 5 years, and am actively supporting the app as well, if you have any question on installing or using the app, you can always email me and I will get back to you as soon as I can.



