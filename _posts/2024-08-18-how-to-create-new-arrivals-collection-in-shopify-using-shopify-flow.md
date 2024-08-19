---
layout: post
title: How to create new arrivals collection in Shopify using Shopify Flow
date: 2024-08-18 22:04 +0800
image: https://yagisoftware.s3.amazonaws.com/25-how-to-create-new-arrivals-collection/cover.png

description: In the Shopify Flow app, create a trigger

cta_code: |
  <div class="mx-auto max-w-3xl py-8 px-6" id="cta-box">
    <div class="w-full flex flex-wrap">
        <h2 class="font-semibold text-3xl md:text-4xl tracking-tight">Get the flow file for adding tag when a product is published</h2>
        <div style="margin: 1em auto; display: flex; align-content: center; justify-content: space-around; column-gap: 50px;">
          <img src="https://img.yagisoftware.com/flowfile.png" alt="abandoned checkout checklist and workaround tips" style="display: inline-block; width: 160px; filter: drop-shadow(0 4px 3px rgb(0 0 0 / 0.07)) drop-shadow(0 2px 2px rgb(0 0 0 / 0.06));">
        </div>
        <h3 class="text-gray-700 text-base lg:text-xl mt-4">You will also receive tips to improve your store's customer experience, about once a week</h3>
    </div>
  
    <div class="w-full text-center mx-auto">
      <script async data-uid="438f6be252" src="https://yagisoft.ck.page/438f6be252/index.js"></script>
      <p class="text-gray-700 text-sm">We respect your privacy, unsubscribe any time</p>
    </div>
  </div>
---

This tutorial requires using Shopify Flow app on your store, you can install the [free Shopify Flow app (by Shopify) here](https://apps.shopify.com/flow) if you haven't already.

Shopify's collection is useful to group products together, and we can use automated collection with tags, to group products that have the specified tag into one collection. 

With the tag, we can easily group new arrival products into collection by assigning a tag to them when creating product, but who has the time to remove the tag for those products one by one afterwards? Heck, sometimes we might even forgot to apply tag when creating product.

Fortunately, Shopify Flow app can help us automate the process of adding and removing tag for products!

First, let's create a new collection to store the new arrival products. Select **Automated** for the collection type, and select the product must match **all conditions**, and set the condition to "Product tag" is equal to "new-arrival".

![Create a new collection](https://yagisoftware.s3.amazonaws.com/25-how-to-create-new-arrivals-collection/collection.png)

Next, we can proceed to create the Flow automation for automating addition and removal of tags : 

![Flow detail](https://yagisoftware.s3.amazonaws.com/25-how-to-create-new-arrivals-collection/flow_detail.png)

This flow will automate adding tag to a product when a product is created, and wait for 30 days, and then remove the tag from the product.

I have created the flow shown above, you can <a href="https://tea.ibex.sh/soulchild/flow-examples/raw/branch/master/Set%20new%20arrival%20tag.flow" download>download the flow file here</a> (right click > "Save as"), and import it into your store.

Open the Shopify Flow app ("Flow") in your store admin, then click "Import", and select the file.

![Import flow](https://yagisoftware.s3.amazonaws.com/25-how-to-create-new-arrivals-collection/import_flow.png)

After importing, you should see a flow named "Set new arrival tag" in the list of flow, click on it, then click "Turn on workflow" :

![Click into flow detail](https://yagisoftware.s3.amazonaws.com/25-how-to-create-new-arrivals-collection/flow_click.png)

![Turn on flow](https://yagisoftware.s3.amazonaws.com/25-how-to-create-new-arrivals-collection/flow_turn_on.png)


After turning on the flow, the automation will be active 🙌, you can test it out by creating a product in your Admin, and then you should see it appearing in the "New Arrival" collection within 1-2 minutes. The tag will also automatically be removed after 30 days, and the product will no longer appear in the collection afterwards.

You can change the "Wait" time to shorter / longer to your liking (you can change it to a shorter period like 5 minutes if you want to test it out and confirm it works). To do this, click the "Edit" button on top, and click on the "Wait" action, and change the time period.

![Flow edit](https://yagisoftware.s3.amazonaws.com/25-how-to-create-new-arrivals-collection/edit_flow.gif)


Sometimes we might create products in draft status, to work on the product information or to wait for the inventory to arrive, and we only want to add the product to new arrival collection after setting its status to "Published" (not right after creation).

You can get the flow file below : 



