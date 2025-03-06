---
layout: post
title: How to redirect new customer account login to different page
description: 
date: 2025-03-06 18:39 +0800
image:  abc
---

If you have switched to the new customer account ("Customer accounts", where the login is passwordless, one time code that is sent to customer email), by default, the customer will be redirected to their account page after they have login. This can be confusing, as they might expect to be redirected to the store homepage after login.

If you would like to redirect customer to a different page after login, you can change the login link (the link which customer clicks to login) to this format : 

`https://your-store.myshopify.com/customer_authentication/login?return_to=<the_page_to_redrect_to_after_login>`


If you are using official Shopify themes like Dawn, this link is located in the `sections/header.liquid` file. In the file, search for "routes.account_login_url" , and change it to the format shown above, or you can refer the examples below.

![Locate login link](https://img.yagisoftware.com/32-redirect-customer-login/1_header_link.png)

Below are some example : 

## Redirect to the page where customer last visited



## Redirect to store home page



## Redirect to specific page




Source: 

[Official Shopify documentation on redirect after customer login](https://shopify.dev/docs/storefronts/themes/login#direct-customers-back-to-another-page-on-the-online-store)