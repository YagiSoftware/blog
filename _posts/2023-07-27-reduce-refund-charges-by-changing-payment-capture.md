---
layout: post
title: Reduce refund transaction fees by changing payment capture
date: 2023-07-27 15:27 +0800
---

Since March 2020, [Shopify has announced they will no longer return the transaction fees incurred for refunded orders](https://community.shopify.com/c/shopify-discussions/transaction-credits-on-refunds-fees-after-march-1-2020-shopify/td-p/642688/page/3#:~:text=We%20won%27t%20be%20asking,that%20you%20agreed%20to%20already.). This means that for a $1000 order, Shopify will charge you a processing fee of around $29, and later on if you decide to refund the customer, the customer will get back their $1000, but the processing fee of $29 will still be charged to your account! (You made 0 sales and lost money)

Sometimes customers might change their mind, and they will request to cancel the order and ask for refund, or there could be issue on the supplier side which causes the order to be unable to fulfill and had to be cancelled. These transactions fees can add up quickly, some of the merchants might say this is a cost of doing business, but I think this cost could be mitigated effectively by changing payment capture settings.

By default, Shopify will automatically charge the customers's card immediately when they place an order, and this will incur a transaction fee (which cannot be returned). To avoid getting charged the transaction fee, we can instruct Shopify to not automatically charge customers when they place an order.

To do so, we can change the payment capture setting to Manual Capture or Automatically capture when the order is fulfilled in the store settings.

![Store settings](https://img.yagisoftware.com/18-manual-payment-capture/1settings.png)

![Capture payment settings](https://img.yagisoftware.com/18-manual-payment-capture/2capture_option.png)

![Change payment capture to manual, or only capture upon fulfillment](https://img.yagisoftware.com/18-manual-payment-capture/3capture.png)

