---
layout: post
title: How to automatically handle high risk orders in Shopify
date: 2024-09-09 16:49 +0800
---

Shopify has built-in fraud analysis which tells you if an order is high risk. A high risk order could meant that a stolen card was used for the payment, or the customer profile has abnormally high chargeback rate etc, these signals a high possibility that you may get hit with chargeback if you fulfill the order, which can cause significant financial losses.

![High risk orders](https://yagisoftware.s3.amazonaws.com/29-high-risk-orders/high_fraud_risk@2x.png)

For high risk order, Shopify usually will recommend you to cancel and refund the order as soon as possible, to prevent chargeback in the future.

The problem with refunding transaction is that, [Shopify does not refund the transaction fee incurred for the order](https://community.shopify.com/c/shopify-discussions/transaction-credits-on-refunds-fees-after-march-1-2020-shopify/td-p/642688/page/3#:~:text=We%20won%27t%20be%20asking,that%20you%20agreed%20to%20already.), which means that if the high risk order is $200, you will still lose about $6 (approximately 3% of the order value) if you cancel and refund the order, these transaction fees could stack up and deducted in your future payout.

To avoid incurring the transaction fee when an order is placed, you can change the payment capture from automatic to manual, which the customer's card will not be charged until you manually go into the order and click "Capture", or when you fulfill the order, you can [follow this article on how to change this settings](https://yagisoftware.com/articles/save-transaction-fees-from-order-refund-by-changing-payment-capture).