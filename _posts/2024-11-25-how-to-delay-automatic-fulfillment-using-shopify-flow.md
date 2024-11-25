---
layout: post
title: How to delay automatic fulfillment using Shopify Flow
date: 2024-11-25 17:04 +0800
---

Shopify allows Automatic Fulfillment, which will automatic fulfill an order when an order is placed, this is especially useful if your store integrates with third party fulfillment services, as the order information is sent to the fulfillment service immediately after the order is paid.

This is handy, until one of the scenarios below occur:

1. Customer wants to make changes to their order details, such as shipping address
2. Customer agrees to a post purchase upsell, and the additional line items need to be added to the order
3. Some other apps need to modify the order right after it is placed to add additional information

If the automatic fulfillment is enabled, the order is already sent and locked with fulfillment service, and thus requires manual editing on the fulfillment service platform, which can be a pain to do whenever such scenario arise.


But turning off automatic fulfillment wholely and manually marking order as fulfilled one by one is too time consuming, wouldn't it be good if there's a solution to delay automatic fulfillment for a set time period, where customer can make changes, 