---
layout: post
title: How to delay automatic fulfillment using Shopify Flow
description: Import the Flow file to delay fulfillment, then you can select the Wait step, and change the duration to the duration you want to delay for, then click enable workflow.
date: 2024-11-25 17:04 +0800
image: https://img.yagisoftware.com/31-delay-automatic-fulfillment/cover.png
---

Shopify allows Automatic Fulfillment, which will automatic fulfill an order when an order is placed, this is especially useful if your store integrates with third party fulfillment services, as the order information is sent to the fulfillment service immediately after the order is paid.

This is handy, until one of the scenarios below occurs:

1. [Customer wants to make changes to their order details, such as shipping address](https://yagisoftware.com/articles/how-to-let-customer-update-order-shipping-address-on-your-shopify-store)
2. Customer agrees to a post purchase upsell, and the additional line items need to be added to the order
3. Some other apps need to modify the order right after it is placed to add additional information

If the automatic fulfillment is enabled, the order is already sent and locked with fulfillment service, and thus requires manual editing on the fulfillment service platform, which can be a pain to do whenever such scenario arise.


But turning off automatic fulfillment entirely and manually marking order as fulfilled one by one is too time consuming, wouldn't it be good if there's a solution to delay automatic fulfillment for a set time period (eg: 30 minutes), where customer can make changes,then only the order is sent to fulfillment service?

Fortunately, with Shopify Flow, we can setup an automated Flow to achieve this.

This tutorial requires using Shopify Flow app on your store, you can install the [free Shopify Flow app (by Shopify) here](https://apps.shopify.com/flow) if you haven't already.

## Setup the flow to wait and fulfill order

Next, you can [download the Shopify Flow file here](https://tea.ibex.sh/soulchild/flow-examples/raw/branch/master/Delay_Send_Fulfillment.flow) (right click > "Save as" / "Download Linked File As"), and import it into your store. The flow content is shown below : 

![Wait and fulfill order flow](https://img.yagisoftware.com/31-delay-automatic-fulfillment/3_flow.png)

Open the Shopify Flow app ("Flow") in your store admin, then click "Import", and select the file.

![Import flow](https://img.yagisoftware.com/25-how-to-create-new-arrivals-collection/import_flow.png)


If you would like to change the wait duration, you can click on "Edit", select the "Wait" step, and change the duration : 

![Change the wait duration](https://img.yagisoftware.com/31-delay-automatic-fulfillment/4_wait_duration.png)

Once you are happy with the duration, you can turn on the workflow, and it will run automatically on the background, it will wait for the set time before sending the order data to fulfillment services.

## Turn off automatic fulfillment on store settings

Once the workflow is turned on, you can turn off automatic fulfillment on your store settings, so that the order will not automatically sent to fulfillment service right after it was placed. Instead , the workflow will pick it up after the time delay is up.

Go to your store settings, select "General" : 

![Store settings](https://img.yagisoftware.com/31-delay-automatic-fulfillment/1_store_settings.png)

Then scroll to "Order processing", and select "Don't fulfill any of the order's line items automatically".

![Disable auto fulfillment](https://img.yagisoftware.com/31-delay-automatic-fulfillment/2_disable_auto.png)

## Apps that allow customer to make changes to order within set time limit

If you like to let customer to change their shipping address within a time limit after an order is placed, I have developed an app for this, the app name is [Yagi Address Edit Helper app](https://apps.shopify.com/address-edit-helper), feel free to give it a try! I am confident this app can reduce your store's support workload.

If you like to let customer to cancel their order within a time limit after an order is placed, I have also developed an app for this, the app name is [Yagi Order Cancellable app](https://apps.shopify.com/cancellable), feel free to give it a try! I am confident this app can reduce your store's support workload as well.
