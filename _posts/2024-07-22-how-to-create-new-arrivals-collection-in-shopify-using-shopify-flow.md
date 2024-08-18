---
layout: post
title: How to create new arrivals collection in Shopify using Shopify Flow
date: 2024-07-22 22:04 +0800
image: https://yagisoftware.s3.amazonaws.com/24-how-to-change-shopify-checkout-flow-to-three-page-checkout/cover.png

description: In the Shopify Flow app, create a trigger
---

This tutorial requires using Shopify Flow app on your store, you can install the [free Shopify Flow app (by Shopify) here](https://apps.shopify.com/flow) if you haven't already.

Shopify's collection is useful to group products together, and we can use automated collection with tags, to group products that have the specified tag into one collection. 

With the tag, we can easily group new arrival products into collection by assigning a tag to them when creating product, but who has the time to remove the tag for those products one by one afterwards? Heck, sometimes we might even forgot to apply tag when creating product.

Fortunately, Shopify Flow app can help us automate the process of adding and removing tag for products!

First, let's create a new collection to store the new arrival products. Select **Automated** for the collection type, and select the product must match **all conditions**, and set the condition to "Product tag" is equal to "new-arrival".

![Create a new collection](https://yagisoftware.s3.amazonaws.com/25-how-to-create-new-arrivals-collection/collection.png)

Next, we can proceed to create the Flow automation for automating addition and removal of tags : 

![Flow detail](https://yagisoftware.s3.amazonaws.com/25-how-to-create-new-arrivals-collection/flow_detail.png)

I have created the flow shown above, you can <a href="https://tea.ibex.sh/soulchild/flow-examples/raw/branch/master/Set%20new%20arrival%20tag.flow" download>download the flow file here</a> (right click > "Save as"), and import it into your store.

Open the Shopify Flow app ("Flow") in your store admin, then click "Import", and select the file.

![Import flow](https://yagisoftware.s3.amazonaws.com/25-how-to-create-new-arrivals-collection/import_flow.png)

After importing, you should see a flow named "Set new arrival tag" in the list of flow, click on it, then click "Turn on workflow" :

![Click into flow detail](https://yagisoftware.s3.amazonaws.com/25-how-to-create-new-arrivals-collection/flow_click.png)

![Turn on flow](https://yagisoftware.s3.amazonaws.com/25-how-to-create-new-arrivals-collection/flow_turn_on.png)


After turning on the flow, the automation will be active, you can test it out by creating a product in your Admin, and then you should see it appearing in the "New Arrival" collection within 1-2 minutes. The tag will also automatically be removed after 30 days, and the product will no longer appear in the collection afterwards.

You can change the "Wait" time to shorter / longer to your liking (you can change it to a shorter period like 5 minutes if you want to test it out and confirm it works). To do this, click the "Edit" button on top, and click on the "Wait" action, and change the time period.

![Flow edit](https://yagisoftware.s3.amazonaws.com/25-how-to-create-new-arrivals-collection/edit_flow.gif)




