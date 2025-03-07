---
layout: post
title: How to redirect new customer account login to different page
description: To redirect to the previous visited page after customer login, change the routes.account_login_url , to routes.storefront_login_url.
date: 2025-03-06 18:39 +0800
image: https://img.yagisoftware.com/32-redirect-customer-login/cover.png
---

If you have switched to the new customer account ("Customer accounts", where the login is passwordless, one time code that is sent to customer email), by default, the customer will be redirected to their account page after they have login. This can be confusing, as they might expect to be redirected to the previous page, or the store homepage after login.

If you would like to redirect customer to a different page after login, you can change the login link (the link which customer clicks to login) to this format : 

`https://your-store.myshopify.com/customer_authentication/login?return_to=<the_page_to_redrect_to_after_login>`


If you are using official Shopify themes like Dawn, this link is located in the `sections/header.liquid` file. In the file, search for "**{% raw %}{{ routes.account_login_url }}{% endraw %}**" , and change it to the format shown above, or you can refer the examples below.

![Locate login link](https://img.yagisoftware.com/32-redirect-customer-login/1_routes.png)

Some third party or older themes might use "/account/login" as the login link in the theme code, you can search for this too.



Below are some examples : 

## Redirect to the page where customer last visited

To redirect to the previous visited page after customer login, change the routes.account_login_url , to **routes.storefront_login_url** . (Remember to use double bracket to output this value)

![Change to storefront url](https://img.yagisoftware.com/32-redirect-customer-login/storefront_url.gif)

## Redirect to store home page

To redirect to the store home page after customer login, change the {% raw %}{{ routes.account_login_url }}{% endraw %} , to **{% raw %}https://{{ shop.permanent_domain }}/customer_authentication/login?return_to=%2F{% endraw %}**

![Change to storefront url](https://img.yagisoftware.com/32-redirect-customer-login/homepage_url.gif)


## Redirect to specific page

To redirect to the specific page after customer login, change the {% raw %}{{ routes.account_login_url }}{% endraw %} , to **{% raw %}https://{{ shop.permanent_domain }}/customer_authentication/login?return_to={{ "/pages/special_welcome_page" &#124; url_encode }}{% endraw %}**

Replace the "/pages/special_welcome_page" to the page you want.


Source: 
[Official Shopify documentation on redirect after customer login](https://shopify.dev/docs/storefronts/themes/login#direct-customers-back-to-another-page-on-the-online-store)