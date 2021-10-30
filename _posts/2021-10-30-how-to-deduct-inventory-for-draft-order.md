---
layout: post
title: How to deduct inventory for Draft Order
date: 2021-10-30 16:44 +0800
---

Shopify does provide a "Reserve items" function on Draft order, but it doesn't actually deduct the inventory count of the products in the draft order , wtf? Even after "reserving items", customer can still see the product available on the store, and proceed to add to cart and only to be greeted with a "sold out" error on the checkout page, what a bad user experience!

![sold out](https://img.yagisoftware.com/11-how-to-deduct-inventory-for-draft-order/out_of_stock.png)

There's a "Payment due later" option which lets you create an order from the draft order, and this will actually deduct the inventory, but if you are using third party fulfillment system, creating an order will trigger fulfillment on their side, which you might not want to, as the order is not even paid yet.

![payment due later](https://img.yagisoftware.com/11-how-to-deduct-inventory-for-draft-order/payment_due_later.png)


Wouldn't it be good if we can deduct inventory for the draft order without turning it into order? This way we won't oversell the product and won't accidentally fulfill unpaid order.

## Reserve inventory using Draft Order Helper app

Using [Draft Order Helper app](https://apps.shopify.com/draft-helper), you can deduct inventory for products used in a draft order easily. (Disclaimer: I am the developer of this app, the app has a free plan which you can try it out)

<div style="width: 100%; text-align: center;">
  <a href="https://apps.shopify.com/draft-helper" target="_blank"><img src="https://img.yagisoftware.com/Shopify-App-Store-Badge-Final-Black.png" style="max-width: 250px; border-radius: 0; box-shadow: none; border-width: 0;"></a>
</div>

<br>

After installing the app, you can go to your draft order, click "More actions" > "**Adjust inventory**".

![adjust inventory](https://yagisoftware.s3.amazonaws.com/11-how-to-deduct-inventory-for-draft-order/adjust_inventory.png)


You can then deduct the inventories for the products on the draft order by clicking "Deduct inventories".
![deduct inventory](https://img.yagisoftware.com/11-how-to-deduct-inventory-for-draft-order/deduct1.png)

Optionally, you can set the inventory to be auto restored after a specified date. If the draft order is not completed by then, the inventory will be automatically restored (you can also choose to manual restore later).
![auto restore inventory](https://img.yagisoftware.com/11-how-to-deduct-inventory-for-draft-order/deduct2.png)

After clicking "Confirm deduct", you can see that the inventory is deducted (from the Shopify admin > Inventory page).
![inventory deducted](https://img.yagisoftware.com/11-how-to-deduct-inventory-for-draft-order/deduct3.png)

## How the inventory deduction works under the hood



