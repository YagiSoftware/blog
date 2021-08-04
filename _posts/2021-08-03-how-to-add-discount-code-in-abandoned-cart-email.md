---
layout: post
title: Add discount code in abandoned cart email content
date: 2021-08-03 19:21 +0800
---

Providing discount code to an abandoned cart email can incentivize a customer to complete their purchase, sometimes they might get shocked by shipping price or being undecisive, adding a discount code might help them to complete their purchase.

Before editing the abandoned cart email content, make sure that the abandoned cart email is enabled, go to **Settings** > **Checkout** :
![checkout settings](https://img.yagisoftware.com/7-how-to-add-discount-code-in-abandoned-cart-email/checkout.png)

Ensure the "Automatically send abandoned checkout emails" is checked.
![abandoned cart email](https://img.yagisoftware.com/7-how-to-add-discount-code-in-abandoned-cart-email/enable_email.png)

Next, edit the abandoned cart email template by going to **Settings** > **Notification**.
![Notifications](https://img.yagisoftware.com/7-how-to-add-discount-code-in-abandoned-cart-email/notification.png)

Select '**Abandoned checkout**'.
![Abandoned checkout email template](https://img.yagisoftware.com/7-how-to-add-discount-code-in-abandoned-cart-email/abandoned_cart.png)

In the email body field, search for "**{% raw %}{{ email_body }}{% endraw %}**" (you can use "Ctrl + F" or "Command + F" in your web browser to search), then add your discount code text **after** the **{% raw %}{% endif %}{% endraw %}** part that is below it :

![email body](https://img.yagisoftware.com/7-how-to-add-discount-code-in-abandoned-cart-email/part.png)

You can use the code below to show the discount code text, feel free to edit the text and discount code as well. The text between `<strong></strong>` will be bolded.

```html
<p>You can use <strong>WELCOMEBACK15</strong> discount code to get 15% off items from your cart</p>

```

Scroll up and click "Save" to save the email content, then you can click the "Preview" button on the top right corner to preview the abandoned cart email content :

![preview](https://img.yagisoftware.com/7-how-to-add-discount-code-in-abandoned-cart-email/preview.png)

Your customer will then see this email content in their inbox if they have abandoned their cart.