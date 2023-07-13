---
layout: post
title: How to deduct inventory for draft order on Shopify
date: 2021-10-30 16:44 +0800
image: https://mugshotbot.com/m/nwAKhiPe
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

## Limitation: How the inventory deduction works under the hood
Due to how Shopify works, there's a caveat on using the app to deduct the inventory from draft order.

You have to make sure there's enough inventory count **after** deducting the inventory using this app (eg: say the draft order place 5 quantity for an item, you need to ensure there is at least 5 quantity **after** deducting inventory, else customer can't checkout), this is because Shopify will deduct the inventory again when customer finish paying for the order.

You can workaround this inventory limitation (of having quantity needed after deducting inventory) by using the "collect payment" button > "pay by credit card" or "mark as paid" mechanism in the draft order.

Here's the inventory flow : 

1. You use Draft Helper app to deduct inventory (eg: inventory goes from 10 to 5)
2. Customer checks out and make payment, Shopify deduct the inventory again  (inventory goes from 5 to 0)
3. Shortly after the order is paid, Draft Helper app automatically replenish the inventory deducted by Shopify to prevent double deduction. (inventory goes from 0 to 5).

<br>
Sorry about the inventory flow, as Shopify will always deduct inventory when customer finish checkout. The best workaround the app can do is to replenish the inventory.


You can also restore the deducted inventory for the draft order, right before sending the customer to checkout, in case you don't have enough inventory at that time.


## Prevent overselling and save manual work on adjusting inventory

With [Draft Order Helper app](https://apps.shopify.com/draft-helper), you can deduct inventory for items in draft order with just 1-click, and even schedule date to auto restore inventory should the draft order is not completed by then. You can prevent overselling and also save time on manual adjustment / workaround.

[Draft Order Helper app](https://apps.shopify.com/draft-helper) comes with a free plan, give it a try you if you would like to solve the issue of overselling and save time on manual inventory adjustment workaround.

I understand it might be hard to trust a random app you came across on internet, you can refer to [these reviews on the app from happy store owners](https://apps.shopify.com/draft-helper/reviews), most of them has used the app for many months and are very happy with it.

I am actively supporting the app as well, if you have any question on installing or using the app, you can always email me and I will get back to you as soon as I can.

Cheers,

[Axel Kee](/about) (developer of Draft Order Helper app)
