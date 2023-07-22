---
layout: post
title: Only show products to certain customers in Shopify (without app)
date: 2023-07-18 12:12 +0800
description: Go to your Shopify Admin,
---

It could be some early drop of products which you only want VIP customer to be able to purchase first, or wholesale products with heavily discounted price which you only want registered wholesale customer to be able to purchase it.

There's apps that offer features that lock a product and make it available only for selected customers, they offer comprehensive rules management, but if you just want to show product to customers that are tagged with certain tag, it might be overkill to use an app for it.

This tutorial will guide you on how to modify your theme to create a new product template , which the private product can use, and the product will only show to the tagged customers. This tutorial will require some copy pasting of code, the tutorial will guide on where and how to copy paste, you can follow without having any coding experience. As the tutorial only creates new product template and does not modify existing ones, you don't have to worry that you might mess up existing code.

This tutorial assume you are using newer Shopify themes which support sections / blocks (Online Store 2.0).



## Create new product template


## Create new product section json, edit the <section> part


## Make a page that show notice text for unauthorized customers

First, we will create a page with text that tell customer that they do not have access to the product, later on we will redirect the customer to this page if they accidentally access the product.

Go to your Shopify Admin, select "Sales Channel" > "Online Store" > "Pages", then create a new page :

![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/1add_page.png)
![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/2page_content.png)

Remember to set the page to be visible.

## Create a new product template for the private product

![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/3edit_code.png)
![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/4product_json.png)
![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/5main-product.png)
![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/6add_section.png)
![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/7copy_paste.png)
![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/8if.png)
![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/9endif.png)
![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/10copy_page_link.png)
![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/10product.png)
![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/11product_template.png)
![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/12main-product-private.png)
![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/13tag-product.png)
![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/14tag-customer.png)
![Image](https://img.yagisoftware.com/16-only-show-product-certain-customer/15hide-from-collection.png)