---
layout: post
title: How to hide “Add to cart / Buy now” button and replace with contact us link
date: 2021-08-08 00:27 +0800
---

There might be some products which you don't want customers to be able to purchase online due to licensing issues, or the product is only available to purchase in-person in store due to regulation etc.

This tutorial will guide you on how to hide the add to cart / buy now button, and optionally replace it with a "contact us" link. This tutorial will require you to edit code of your theme, knowledge of HTML / CSS / Liquid would help but it is not required. 

![before and after](https://img.yagisoftware.com/8-hide-add-to-cart-button-and-add-contact-us/beforeafter.png)

## Create a new product template and section
First thing, create a new product template. Select “**Theme**” > “**Actions**” > “**Edit code**”
![edit code](https://img.yagisoftware.com/4-how-to-customize-sorting-options-on-collection-page/edit_code.png)

Click "Add new template", then select "product" for template,  "liquid" as template type, and name it as "product.contactus" , and click "Create template".

![add new template](https://img.yagisoftware.com/8-hide-add-to-cart-button-and-add-contact-us/add_new_template.png)

![product liquid template](https://img.yagisoftware.com/8-hide-add-to-cart-button-and-add-contact-us/product_contact_us_new.png)

Open the newly created "product.contactus.liquid" file, then find the part that is similar to `section "product-template"`. (Can be "product-form" on some theme). Remember this name, as we are going to open this section file next.

![product-section-name](https://img.yagisoftware.com/8-hide-add-to-cart-button-and-add-contact-us/product-section.png)

Next, open the section file (eg: product-template.liquid, in the sections folder), and select all (Ctrl + A or Command + A) and **copy** (Ctrl + C or Command + C) :
![product-section-open](https://img.yagisoftware.com/8-hide-add-to-cart-button-and-add-contact-us/product-template-section.png)

We will going to paste this in the new section we are going to create.

Create a new section, and name it as **product-contactus-template** .
![new section](https://img.yagisoftware.com/8-hide-add-to-cart-button-and-add-contact-us/new-section.png)
![new section-2](https://img.yagisoftware.com/8-hide-add-to-cart-button-and-add-contact-us/new-section-2.png)

Next, **replace** the code of the newly created section with the code we copied just now. Select all (Ctrl + A or Command A), backspace and paste (Ctrl + V or Command + V), and click Save.

![paste new section](https://img.yagisoftware.com/8-hide-add-to-cart-button-and-add-contact-us/paste-new-section.png)

## Get the parent class name of the add to cart / buy button, and hide it

Next, open your product page in your web browser. Right click on the "Add to cart" button, then select "**Inspect**" / "**Inspect Element**" , this will show the HTML code of the buttons. Then move your mouse to the code area, and slowly move up until the highlighted area includes both "Add to cart" and "checkout" button.

Then check the `class="..."` part, and copy the first word (separated by space), this is the class name which we will use later to hide the add to cart / buy now buttons.

Demo video :
<video style="width: 100%;" controls>
  <source src="https://img.yagisoftware.com/8-hide-add-to-cart-button-and-add-contact-us/containerclass.mp4" type="video/mp4">
Your browser does not support the video tag.
</video>
<br>
From the example video above (from my store theme), the class name is `product-form__item` (yours might differ). Copy this word, then **open the section file you have created previously** (_product-contactus-template.liquid_).

At the bottom of **product-contactus-template.liquid**, add this block of code : 


```
{% raw %}{% stylesheet %}

.product-form__item {
  display: none;
}

{% endstylesheet %}{% endraw %}

```

Replace the ".product-form__item" with the word you have copied just now, remember to add a dot (**.**) before the word, as the dot means "class name". This block of code tells your Shopify store to hide the part containing add to cart / buy now button, with the "display : none" code.

Eg: if your class name is **product-form__controls-group**, then it should look like this instead : 

```
{% raw %}{% stylesheet %}

.product-form__controls-group {
  display: none;
}

{% endstylesheet %}{% endraw %}

```

Press save, it should look like this  :
![pasted code](https://img.yagisoftware.com/8-hide-add-to-cart-button-and-add-contact-us/product-pasted.png)


## Update the new product template

Open the new product template created just now (**“product.contactus.liquid”**), then find the part that is similar to section "product-template". (Can be “product-form” on some theme).

![product contactus template](https://img.yagisoftware.com/8-hide-add-to-cart-button-and-add-contact-us/product-section.png)

And then change this part to **product-contactus-template** , which is the name of section we modified just now.
```
{% raw %}{% section 'product-contactus-template' %}{% endraw %}
```

Press save, then in your Shopify Admin, go to the Product you want to hide add to cart / buy button.

And change the **Theme template** to "contactus" , this will use the "product.contactus.liquid" file to display the product.
![product template](https://img.yagisoftware.com/8-hide-add-to-cart-button-and-add-contact-us/change-product-template.png)

Press save, then now when you view the product page, the "Add to cart" and "Buy now" button is gone! You can change the theme template for all the products which you want to hide the add to cart / buy button.

## Add a contact us link

This part assumes you want to use the same design / style of the add to cart button for the contact us link.

To replicate the design of add to cart button, we first have to get the class name of the add to cart button.

Open your product page (which uses the normal product template, not the contactus template) in your web browser. Right click on the "Add to cart" button, then select "**Inspect**" / "**Inspect Element**" , and then copy all the classes of that button :

![button classes](https://img.yagisoftware.com/8-hide-add-to-cart-button-and-add-contact-us/btn-class.png)

And also remember the code for the add to cart button (`<button type="submit" name="add ....>`), as we will need to find for this part in the product template later.

Next, go to the contact us section template (product-contactus-template.liquid, under sections folder), and find the code of add to cart button, and then go up to the parent with the class name (the class name we used in the previous section).
![contact-us-code](https://img.yagisoftware.com/8-hide-add-to-cart-button-and-add-contact-us/contact-us-code-small.png)

And then find the ending part of the parent (`</div>`), and add code below it to show the "Contact Us" link :
```html
<a href="https://your-store.myshopify.com/pages/contact-us" class="btn product-form__cart-submit btn--secondary-accent">Contact Us for pricing</a>
```

The `href` would be the URL to your store's contact us page, and paste the classes you copied just now from the add to cart button into the `class` ('btn ... btn--secondary-accent'). You can change the "Contact Us for pricing" to any text you want.

Click "Save", then go to the product page that has **contactus** template chosen, then you should see a contact us link there : 
![contact us button](https://img.yagisoftware.com/8-hide-add-to-cart-button-and-add-contact-us/contact-us-result.png)


