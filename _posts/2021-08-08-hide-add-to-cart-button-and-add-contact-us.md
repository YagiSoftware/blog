---
layout: post
title: How to hide “Add to cart / Buy now” button and replace with contact us link
date: 2021-08-08 00:27 +0800
---

There might be some products which you don't want customers to be able to purchase online due to licensing issues, or the product is only available to purchase in-person in store due to regulation etc.

This tutorial will guide you on how to hide the add to cart / buy now button, and optionally replace it with a "contact us" link. This tutorial will require you to edit code of your theme, knowledge of HTML / CSS / Liquid would help but it is not required. 

![before and after](https://img.yagisoftware.com/8-hide-add-to-cart-button-and-add-contact-us/beforeafter.png)

## Create a new product template
First thing, create a new product template. Select “**Theme**” > “**Actions**” > “**Edit code**”
![edit code](https://img.yagisoftware.com/4-how-to-customize-sorting-options-on-collection-page/edit_code.png)

Click "Add new template", then select "Product", "Liquid", and name it as "product.contactus" , and click "Create template".

![add new template](https://img.yagisoftware.com/8-hide-add-to-cart-button-and-add-contact-us/add_new_template.png)

![product liquid template](https://img.yagisoftware.com/8-hide-add-to-cart-button-and-add-contact-us/product_contact_us_new.png)

Open the newly created "product.contactus.liquid" file, then find the part that is similar to `section "product-template"`. (Can be "product-form" on some theme). Remember this name, then we are going to find this section file next.

![product-section-name](https://img.yagisoftware.com/8-hide-add-to-cart-button-and-add-contact-us/product-section.png)

Next, open the section file, and select all (Ctrl + A or Command + A) and **copy** (Ctrl + C or Command + C) :
![product-section-open](https://img.yagisoftware.com/8-hide-add-to-cart-button-and-add-contact-us/product-template-section.png)

We will going to paste this in the new section we are going to create.

Create a new section, and name it as **product-contactus-template** .
![new section](https://img.yagisoftware.com/8-hide-add-to-cart-button-and-add-contact-us/new-section.png)
![new section-2](https://img.yagisoftware.com/8-hide-add-to-cart-button-and-add-contact-us/new-section-2.png)

Next, **replace** the code of the newly created section with the code we copied just now. Select all (Ctrl + A or Command A) and paste (Ctrl + V or Command + V), and click Save.

![paste new section](https://img.yagisoftware.com/8-hide-add-to-cart-button-and-add-contact-us/paste-new-section.png)

<video style="width: 100%;" controls>
  <source src="https://img.yagisoftware.com/8-hide-add-to-cart-button-and-add-contact-us/containerclass.mp4" type="video/mp4">
Your browser does not support the video tag.
</video>