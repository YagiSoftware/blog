---
layout: post
title: How to automatically handle high risk orders in Shopify with Flow
date: 2024-09-09 16:49 +0800
image: https://img.yagisoftware.com/29-high-risk-orders/cover.png

description: with Shopify Flow, we can setup an automation to check the order risk of a newly placed order, and proceed to capture the payment if it is not high risk, this way you don't have to worry about forgetting to capture a payment, and you don't have to worry about the loss of transaction fee while refunding a high risk order.
---

Shopify has built-in fraud analysis which tells you if an order is high risk. A high risk order could meant that a stolen card was used for the payment, or the customer profile has abnormally high chargeback rate etc, these signals a high possibility that you may get hit with chargeback if you fulfill the order, which can cause significant financial losses.

![High risk orders](https://img.yagisoftware.com/29-high-risk-orders/high_fraud_risk@2x.png)

For high risk order, Shopify usually will recommend you to cancel and refund the order as soon as possible, to prevent chargeback in the future.

The problem with refunding transaction is that, [Shopify does not refund the transaction fee incurred for the order](https://community.shopify.com/c/shopify-discussions/transaction-credits-on-refunds-fees-after-march-1-2020-shopify/td-p/642688/page/3#:~:text=We%20won%27t%20be%20asking,that%20you%20agreed%20to%20already.), which means that if the high risk order is $200, you will still lose about $6 (approximately 3% of the order value) if you cancel and refund the order, these transaction fees could stack up and deducted in your future payout.

To avoid incurring the transaction fee when an order is placed, you can change the payment capture from automatic to manual, which the customer's card will not be charged until you manually go into the order and click "Capture", or when you fulfill the order, you can [follow this article on how to change this settings](https://yagisoftware.com/articles/save-transaction-fees-from-order-refund-by-changing-payment-capture).

The downside of manual payment capture is that you will have to remember to capture the payment in the future (before the authorization expires), and you will not get payout until if it is not captured, which can be crucial for pre-orders or on-demand products.

Fortunately with Shopify Flow, we can setup an automation to check the order risk of a newly placed order, and proceed to capture the payment if it is not high risk, this way you don't have to worry about forgetting to capture a payment, and you don't have to worry about the loss of transaction fee while refunding a high risk order.

This tutorial requires using Shopify Flow app on your store, you can install the [free Shopify Flow app (by Shopify) here](https://apps.shopify.com/flow) if you haven't already.

## Turn off automatic payment capture

Before we begin to use the Flow automation, make sure that the automatic payment capture is turned off in the Store Settings.

1. Go to your Shopify store settings, then select "Payments"
2. Then find the "Payment capture method" section, and click "Manage"
![Store settings](https://img.yagisoftware.com/18-manual-payment-capture/1settings.png)

3. You can select either "Automatically when order is fulfilled" or "Manually". Both options will authorize the customers payment method (which give your store permission to charge them later, but they are not charged when an order is placed).
![Capture payment settings](https://img.yagisoftware.com/18-manual-payment-capture/2capture_option.png)

<br><br>

## Enable the Order Risk automation flow

Next, you can [download the Shopify Flow file here](https://tea.ibex.sh/soulchild/flow-examples/raw/branch/master/Capture%20payment%20if%20order%20is%20not%20high%20fraud%20risk.flow) (right click > "Save as" / "Download Linked File As"), and import it into your store. The flow content is shown below : 

![Auto capture for non-high risk flow](https://img.yagisoftware.com/29-high-risk-orders/capture_flow.png)

Open the Shopify Flow app ("Flow") in your store admin, then click "Import", and select the file.

![Import flow](https://img.yagisoftware.com/25-how-to-create-new-arrivals-collection/import_flow.png)

After importing, you should see a flow named "Capture payment if order is not high fraud risk" in the list of flow, click on it, then click "Turn on workflow" :


![Click into flow detail](https://img.yagisoftware.com/29-high-risk-orders/click_workflow.png)

![Turn on flow](https://img.yagisoftware.com/29-high-risk-orders/turn_on_workflow.png)


This flow automation will assess the order risk when an order is placed, and will automatically capture the payment of the order if it is deemed non high risk. (If the payment for some reason can't be captured automatically even though it is not high risk, the order will be tagged with "uncaptured").

If the order is high risk, the flow will cancel the order immediately , and send an internal email to a specific email address to notify about this order.

You can change the content and recipient of the notification email. To do this, click the “Edit” button on top, and click on the "Send internal email" action, and change the content / recipient.

![Change notification email recipient](https://img.yagisoftware.com/29-high-risk-orders/edit_recipient.gif)

With this automation, you can save on the transaction fee incurred on fradulent order, and you won't have to remember to capture order manually later on.

