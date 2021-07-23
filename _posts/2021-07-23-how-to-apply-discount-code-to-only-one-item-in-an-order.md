---
layout: post
title: How to apply discount code to only one item in an order
date: 2021-07-23 16:26 +0800
---

Caveat: this is a workaround using Buy X Get Y discount type from Shopify, and the discount code will apply to the lowest priced item that is qualified for discount, and the discount type must be percentage (not fixed amount), and customer must order least two eligible items to get discount on one item.

Discount code can be a good way to track sales brought in by an influencer or an affiliate partner, but giving too much discount might decrease your margin.

Say you want to create a discount code which give 20% off on item that belongs to a collection, but **you want the discount to apply on only just one item**, not on all of the items that are eligible in the order, as this would give too much discount, how do you go about it?

First, create a collection of all the items that eligible for the discount code if you haven't already.

Next, create a discount code, and select "**Buy X get Y**"
![Buy X get Y discount](https://img.yagisoftware.com/5-how-to-apply-discount-code-to-only-one-item-in-an-order/discount1.png)

Then select "**Minimum quantity of items**", input "1" as the quantity and select the collection you created earlier for both "Customer Buys" and "Customer Gets" section.

This way, when customer buy 1 of the items from the collection, they will get discount on 1 item from the collection.
![Minimum quantity](https://img.yagisoftware.com/5-how-to-apply-discount-code-to-only-one-item-in-an-order/discount2.png)

Set the discount percentage you want, and then make sure to check **Set a maximum number of uses per order**, and set the value to "**1**", this will ensure that the "buy 1 get 1 item discounted" logic only run once per order, so that customer only get one discounted item at most.

![Maximum use](https://img.yagisoftware.com/5-how-to-apply-discount-code-to-only-one-item-in-an-order/discount3.png)


Now when a customer use the discount code, only one item from the eligible collection will be discounted, and the **cheapest item in the collection will be discounted**.
![Only apply to one item](https://img.yagisoftware.com/5-how-to-apply-discount-code-to-only-one-item-in-an-order/discount4.png)

Another caveat is that the customer must order at least two items from the collection to be eligible for the discount, if they only order one item from the collection, then the discount code will not be valid.

![Must have at least two items](https://img.yagisoftware.com/5-how-to-apply-discount-code-to-only-one-item-in-an-order/discount5.png)


With this workaround, you can have a discount code that apply discount to only one item in the order.