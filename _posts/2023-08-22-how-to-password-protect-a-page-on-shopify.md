---
layout: post
title: How to password protect a page on Shopify
date: 2023-08-22 01:50 +0800
---

You might have some content that you want to gate from public access, for example wholesale price list, or downloadable content for customers who have previously purchased certain product etc.

There's way to create a new page template that only show content to logged in customer which have certain tags, but what if you want to allow visitor to view the content without creating an account / logging in?

This tutorial will guide you (with copy paste code) on how to implement password protected page with metafields and custom coding on theme, and you can set different password for different page with ease.

Example demo gif here

Before we begin the tutorial, it would be best to [make a backup of your theme](https://yagisoftware.com/articles/how-to-backup-your-shopify-theme), in case anything goes wrong, you can revert the changes by publishing the copy of the original theme.


= Table of contents

= First section title (Create metafield definition for page to store the password)

First, we will create a metafield definiton for pages, to store the password value. Go to your store settings, select "Custom Data" on the left side bar, and click "Pages":
![Create custom data metafield definition for Pages](https://img.yagisoftware.com/22-password-protect-page/1custom_data.png)

Then click "Add definiton":
![Click "Add definition"](https://img.yagisoftware.com/22-password-protect-page/2page_definition.png)

In the definition form, input **password** for the "Name" field, and ensure the "Namespace and key" field value is **custom.password**, and select "Single line text" for the type, and remember to enable "Storefront access", so the theme code can access this value later on. Click "Save" to save the changes.
![Add page metafield definition namespace and key and type](https://img.yagisoftware.com/22-password-protect-page/3page_type.png)

Next, go to your desired page (Online Stores > Pages, and select your page), and scroll down to "Metafields" section, and click "Show all" :
![Go to your desired page, then click 'Show All' metafield](https://img.yagisoftware.com/22-password-protect-page/4page_metafield.png)

In the password metafield section, type in your desired password value (visitor will need to input this password value to view the page content) : 
![Input your desired password for the password metafield](https://img.yagisoftware.com/22-password-protect-page/5page_set_password.png)

= Second section title (Modify theme code to add password input box and gate the content)

Go to your store Shopify Admin, then select "Online Store" > "Theme", go to your current theme and select "Edit Code" :
![Edit code on current Shopify theme](https://img.yagisoftware.com/16-only-show-product-certain-customer/3edit_code.png)

Then search for "page.json" in the left side bar of the Theme code editor, and open the "page.json" file, locate the value for "main" -> "type". The value usually should be "main-page", we will then search for this file, search this value on the left side bar, and open the file.

![Open your page.json file and get main type name](https://img.yagisoftware.com/22-password-protect-page/6page_json.png)