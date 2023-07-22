---
layout: post
title: Only show products to certain customers in Shopify (without app)
date: 2023-07-18 12:12 +0800
description: In the Shopify theme code editor, we search for "product.json" file, open it, and search for the "main-product" text, and duplicate the "main-product.liquid" file
image: https://img.yagisoftware.com/16-only-show-product-certain-customer/cover.png
---

It could be some early drop of products which you only want VIP customer to be able to purchase first, or wholesale products with heavily discounted price which you only want registered wholesale customer to be able to purchase it.

There's apps that offer features that lock a product and make it available only for selected customers, they offer comprehensive rules management, but if you just want to show product to customers that are tagged with certain tag, it might be overkill to use an app for it.

This tutorial will guide you on how to modify your theme to create a new product template , which the private product can use, and **the product will only show to the tagged customers**. This tutorial will require some copy pasting of code, the tutorial will guide on where and how to copy paste, you can follow without having any coding experience. As the tutorial only creates new product template and does not modify existing ones, you don't have to worry that you might mess up existing code.

This tutorial assume you are using newer Shopify themes which support sections / blocks (Online Store 2.0).




## Make a page that show notice text for unauthorized customers

First, we will create a page with text that tell customer that they do not have access to the product, later on we will redirect the customer to this page if they accidentally access the product.

Go to your Shopify Admin, select "Sales Channel" > "Online Store" > "Pages", then create a new page :

![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/1add_page.png)
![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/2page_content.png)

Remember to set the page to be visible.

## Create a new product template for the private product

Next, go to "Online Store" > "Themes", select your current theme, and click the three dots, and click "Edit code", to edit the code of theme.

![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/3edit_code.png)

Search for "product.json" (this is the default template of the product), and open the file, then search for the value of "sections" > "main" > "type", this value is the filename of the actual product template used. (This value usually is "main-product") We will open this file.
![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/4product_json.png)


Next, we search for the filename ("main-product"), and open the file : 
![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/5main-product.png)

Next, click the "Add a new section", select "liquid", and name the file as "main-product-private" (we will refer to this filename in later steps)
![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/6add_section.png)

Delete all the code in the newly created "main-product-private.liquid" file, then copy everything from "main-product.liquid", and paste it into "main-product-private.liquid" file.
![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/7copy_paste.png)

After pasting the code to "main-product-private.liquid" file, go to the top of the file, and paste this code right before the `<section...` part : 

```{% raw %}
{% if customer.tags contains "VIP" %}
{% endraw %}```

![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/8if.png)


And then in the same file, press Control + F (or Command + F if you are using Mac), and search for "</section>", locate the "</section>" line that appears right before "{% raw %}{% schema %}{% endraw %}".

Then add this code after the "</section>" line : 
```{% raw %}
{% else %}
  <script>
    window.location.href = "https://vulpes-yagi.myshopify.com/pages/unauthorized-access-to-product";
  </script>
{% endif %}
{% endraw %}```


Remember to replace the `https://vulpes-yagi.myshopify.com/pages/unauthorized-access-to-product` part with the link to your page that shows the unauthorized text which we created earlier.

![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/9endif.png)

To get the link to the page, you can go to your page, and copy the link from the Search engine listing section : 
![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/10copy_page_link.png)

Remember to click "Save" after making changes on the `main-product-private.liquid` file. The code we pasted earlier will redirect the customer to the page that shows unauthorized message, if the customer does not have the "VIP" tag (uppercase VIP).


Next, in the theme code editor, we search for "product.json" file, open it.

![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/10product.png)

Then, we click "Add a new template", then select "product" as the template type, and select "JSON", and input "private" into the file name (the actual filename will be "product.private.json")

![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/11product_template.png)

In the newly created "product.private.json" file, change the "main-product" to "main-product-private".  (in "sections" > "main" > "type")

This will tell the product template to refer to the "main-product-private.liquid" template file we modified earlier.

![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/12main-product-private.png)

click "Save" to save the changes.

Next, go to the product which you want to show for certain tagged customer, and tag the product with "private", and choose the "private" template (which refer to product.private.liquid) for the product, and click "Save".

![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/13tag-product.png)

To confirm it works, you can go to your online store website, navigate to the Catalog page (that shows all products of your store), and click on the private product, you should be redirected to the unauthorized page:
![Unauthorized page](https://img.yagisoftware.com/16-only-show-product-certain-customer/unauthorized.gif)

Now you can add the "VIP" tag to customers who you want them to be able to view the product (and place order for the product) :
![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/14tag-customer.png)


## Hide the product from collections for unauthorized customers

We can go a step further to hide the product from collections / catalog, so that unauthorized customers will not see them in collections.

To do this, open the theme and select "Edit code", then search for the file "main-collection-product", and open the file.

In the file, search for "for product in" (press "Control + F" or "Command + F"), and add this block of code right below that line :
```{% raw %}
{% if product.tags contains "private" %}
  {% unless customer.tags contains "VIP" %}
    {% continue %}
  {% endunless %}
{% endif %}
{% endraw %}```


Click "Save", and now the product will not appear in collection if the customer does not have the tag "VIP".

![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/15hide-from-collection.png)