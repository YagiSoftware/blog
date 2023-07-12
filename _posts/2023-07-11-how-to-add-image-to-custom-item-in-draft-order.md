---
layout: post
title: How to add image to custom line item in a Draft Order
date: 2023-07-11 16:37 +0800
---

Currently Shopify does not have a way to attach image to a custom line item in a draft order, which is unfortunate, as customer needs to see how the product looks like before deciding to purchase.

This article will show a workaround for this issue, there is still some imperfection, like the image will not show directly on the checkout page (due to Shopify limitation), but this article will guide you to show the image on the invoice email (which the customer can view and print), the draft order page in the Shopify Admin (which the staff can view and print), and also on the packing slip (which the staff can view and print).


Disclaimer: This workaround requires usage of an app, Draft Order Helper [https://apps.shopify.com/draft-helper](https://apps.shopify.com/draft-helper). The app is used to add the image link information to the custom line item, I am the developer of the app, the app has a free plan which you can give it a try.


First, go to your Shopify Admin > *Content* > *Files* , and upload the image you want to use there.

![Shopfiy Admin Files](https://img.yagisoftware.com/15-custom-line-item-image/1files.png)

![Upload the image](https://img.yagisoftware.com/15-custom-line-item-image/2upload.png)

And then copy the link for that image, we will need to paste this link later on.

![Copy link for the image](https://img.yagisoftware.com/15-custom-line-item-image/3copy_link.png)


Next, if you have not install the Draft Helper app yet, you can install it here : [https://apps.shopify.com/draft-helper](https://apps.shopify.com/draft-helper). (You need this app to proceed to the next step)


Next, go to the detail page of the draft order which you want to attach the image to the custom item, click the *More actions* menu, and select *Edit line item properties*.

![Edit line item properties](https://img.yagisoftware.com/15-custom-line-item-image/4edit_properties.png)

![Edit line item properties of custom item](https://img.yagisoftware.com/15-custom-line-item-image/5custom_edit.png)

Input **"image"** for the **name** field, and paste in the link you have copied in the previous step into the value field : 

![Paste the image link](https://img.yagisoftware.com/15-custom-line-item-image/6apply_edit.png)

Then click the "Apply changes to current draft" button to apply the changes.

You should now see the image attached to the custom item in the draft order detail page : 

![Custom item image shown in draft order detail page](https://img.yagisoftware.com/15-custom-line-item-image/7draft_custom_image.png)

The custom item now have an image attached to it, although it is not using the same layout like a normal product, but you (and your staff) can now know how the product looks like for the custom item.

In the checkout page for the draft order, the customer can click the "image" link on the custom item, to view the image : 

![Customer can click the image link attached to the custom item in checkout page to view the image](https://img.yagisoftware.com/15-custom-line-item-image/8checkout_image.gif)

Although the custom image is not shown directly on the checkout page, customer can still view the image by clicking the link attached to the custom item on the checkout page.

## Draft Order Invoice Email Template

WIP: