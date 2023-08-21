---
layout: post
title: How to password protect a page on Shopify
date: 2023-08-22 01:50 +0800
---

Example page that you want to password protect might be Wholesaler price that is not for public, and you don't require customer to login to view it, hence you can't use customer tag to decide whether to show the page content.

![Duplicate your current theme](https://img.yagisoftware.com/22-password-protect-page/1custom_data.png)


![Create custom data metafield definition for Pages](https://img.yagisoftware.com/22-password-protect-page/1custom_data.png)
![Click "Add definition"](https://img.yagisoftware.com/22-password-protect-page/2page_definition.png)
![Add page metafield definition namespace and key and type](https://img.yagisoftware.com/22-password-protect-page/3page_type.png)
![Go to your desired page, then click 'Show All' metafield](https://img.yagisoftware.com/22-password-protect-page/4page_metafield.png)
![Input your desired password for the password metafield](https://img.yagisoftware.com/22-password-protect-page/5page_set_password.png)

Go to your store Shopify Admin, then select "Online Store" > "Theme", go to your current theme and select "Edit Code" :
![Edit code on current Shopify theme](https://img.yagisoftware.com/16-only-show-product-certain-customer/3edit_code.png)


![Open your page.json file and get main type name](https://img.yagisoftware.com/22-password-protect-page/6page_json.png)