---
layout: post
title: How to exclude sale items / products From Discount code
date: 2022-03-09 23:21 +0800
image: https://mugshotbot.com/m/c1QrhRVy
---


Discount code is a great way to promote sales, but letting customer to apply discount code on an already discounted sale item might cut into margin, which we don't want to. This post will show steps on how to exclude products from discount code created in Shopify.

Note that this is a workaround as Shopify discount code don't have native excluding functionality.


## Step 1 - Input "Compare At" price for the item you want to exclude

The "Compare At" price is the original higher price for the item (before discount), set this price for the products you want to exclude from discount.

![compare at price](https://yagisoftware.s3.amazonaws.com/13-how-to-exclude-products-from-discount-code/compare_at_price.png)

Select your product you want to exclude from discount in Shopify Admin > Products, then fill in the compare at price :

![compare at price](https://img.yagisoftware.com/13-how-to-exclude-products-from-discount-code/compare_at_price_2.png)

## Step 2 - Create a collection with automated condition

Next, go to Shopify Admin > Collection, and create collection.

![create collection](https://img.yagisoftware.com/13-how-to-exclude-products-from-discount-code/create_collection.png)

In the **collection type**, select **Automated**.   

For the condition, select **all conditions**, then select **Compare at Price** - **is empty**.
![automated collection](https://img.yagisoftware.com/13-how-to-exclude-products-from-discount-code/automated_collection.png)

Click "Save" to create the collection.

This collection will automatically exclude the products you have filled with "Compare At" price in Step 1.

## Step 3 - Edit the discount code to apply only to the collection

Select your discount code in the Shopify Admin > Discounts. Then in the **Applies To** section, select **Specific collections**, and choose the collection you have created in the previous step.

![applies to](https://img.yagisoftware.com/13-how-to-exclude-products-from-discount-code/applies.png)


And now your discount code should exclude the sale items / products 🙌.