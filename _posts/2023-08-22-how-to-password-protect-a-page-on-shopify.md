---
layout: post
title: How to password protect a page on Shopify
date: 2023-08-22 01:50 +0800
image: https://img.yagisoftware.com/22-password-protect-page/cover.png
description: First, we will create a metafield definiton for pages, to store the password value. Go to your store settings, select "Custom Data" on the left side bar, and click "Pages"...
---

You might have some content that you want to gate from public access, for example wholesale price list, or downloadable content for customers who have previously purchased certain product etc.

There's way to create a new page template that only show content to logged in customer which have certain tags, but what if you want to allow visitor to view the content without creating an account / logging in?

This tutorial will guide you (with copy paste code) on how to implement password protected page with metafields and custom coding on theme, and you can set different password for different page with ease.

![Password protected page](https://img.yagisoftware.com/22-password-protect-page/password_demo.gif)

Before we begin the tutorial, it would be best to [make a backup of your theme](https://yagisoftware.com/articles/how-to-backup-your-shopify-theme), in case anything goes wrong, you can revert the changes by publishing the copy of the original theme.

<br><br>
### Table of contents
<a href="#create-metafield-definition-for-page-to-store-the-password">Create metafield definition for page to store the password</a>
<br>
<a href="#modify-theme-code-to-add-password-input-box-and-gate-the-content">Modify theme code to add password input box and gate the content</a>
<br>


## Create metafield definition for page to store the password

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

<br><br>

## Modify theme code to add password input box and gate the content

Go to your store Shopify Admin, then select "Online Store" > "Theme", go to your current theme and select "Edit Code" :
![Edit code on current Shopify theme](https://img.yagisoftware.com/16-only-show-product-certain-customer/3edit_code.png)

Then search for "page.json" in the left side bar of the Theme code editor, and open the "page.json" file, locate the value for "main" -> "type". The value usually should be "main-page", we will then search for this file, search this value on the left side bar, and open the file.

![Open your page.json file and get main type name](https://img.yagisoftware.com/22-password-protect-page/6page_json.png)

(If your store theme does not have "page.json", then you can search for "page.liquid", and use it as a replacement for the "main-page.liquid" file for the steps below)

Open the "main-page.liquid" in the code editor (or another file name if it is different), and paste the following code at the top of the file : 

```
{% raw %}
{% capture contentForQueryString %}{{ content_for_header }}{% endcapture %}
  {% assign pageParams = contentForQueryString
    | split: '"pageurl":"'
    | last
    | split: '"'
    | first
    | split: '.myshopify.com'
    | last
    | split: '?'
    | last
    | replace: '\/', '/'
    | replace: '%20', ' '
    | replace: '\u0026', '&'
    | split: '&'
  %}

{% for param in pageParams %}
  {% if param contains 'password=' %}
  {% capture pagePassword %}{{ param | split: '=' | last }}{% endcapture %}
  {% endif %}
{% endfor %}
{% endraw %}
```

![Paste the code on the top of main page template](https://img.yagisoftware.com/22-password-protect-page/7main_page_top.png)

Next, search for {% raw %}{{ page.content }}{% endraw %} in the same file, and paste this line above it :
```
{% raw %}
{% if page.metafields.custom.password == empty or page.metafields.custom.password == pagePassword %}
{% endraw %}
```
![Add liquid code above content](https://img.yagisoftware.com/22-password-protect-page/8content_above.png)


Next, search for {% raw %}{{ page.content }}{% endraw %} in the same file, and paste this line below it :
```
{% raw %}
{% else %}
<p>
  {% if pagePassword %}
  {{ section.settings.wrong_password_prompt_text }}
  {% else %}
  {{ section.settings.password_prompt_text }}
  {%  endif %}
</p>
<div class="field">
  <input type="password" id="password-input" class="field__input" placeholder="Password" autofocus autocomplete="off" onkeypress="if(event.keyCode == 13){ window.location.href = '{{ request.path }}?password=' + this.value; }"/>
  <br>
  <button type="button" class="button" onclick="window.location.href = '{{ request.path }}?password=' + this.value;">{{ section.settings.submit_password_text }}</button>
</div>
{% endif %}
{% endraw %}
```
![Add liquid code above content](https://img.yagisoftware.com/22-password-protect-page/8content_below.png)


Next, search for {% raw %}{% schema %}{% endraw %} in the same file, and paste the following lines below the "settings: [" line :
```
{% raw %}
{
  "id": "password_prompt_text",
  "type": "text",
  "label": "Text to tell visitor to input password",
  "default": "Please input password to view this page"
},
{
  "id": "wrong_password_prompt_text",
  "type": "text",
  "label": "Text to tell visitor to input a correct password",
  "default": "Wrong password, please try again"
},
{
  "id": "submit_password_text",
  "type": "text",
  "label": "Text for the submit password button",
  "default": "Submit"
},
{% endraw %}
```

![Add settings code for the page section](https://img.yagisoftware.com/22-password-protect-page/9settings.png)

Save the code changes, then go to your theme, and click "Customize" :

![Customize theme](https://img.yagisoftware.com/19-terms-checkbox/1customize_theme.png)

Then navigate to the default page template in the Theme Editor (Click the top "Home page", and navigate to "Pages" > "Default page").
![Navigate to the page in theme editor](https://img.yagisoftware.com/22-password-protect-page/10navigate_page.png)

Then click the "Page" section of the left sidebar : 
![Click the page section on left sidebar](https://img.yagisoftware.com/22-password-protect-page/11page_section.png)

You can then customize the text prompt that will be shown to visitor on password protected page :
![Customize the text for the prompt](https://img.yagisoftware.com/22-password-protect-page/12customize.png)


After saving, you can try go to your store and access the page that is password protected, you should see a password box with the text prompt! You can try enter a wrong password, you should see that the page content is only shown when a correct password is supplied.

You can set password on other pages by setting the metafield (custom.password) value, go to the selected page, scroll down to "Metafields" section, and click "Show all" :
![Go to your desired page, then click 'Show All' metafield](https://img.yagisoftware.com/22-password-protect-page/4page_metafield.png)

In the password metafield section, type in your desired password value (visitor will need to input this password value to view the page content) : 
![Input your desired password for the password metafield](https://img.yagisoftware.com/22-password-protect-page/5page_set_password.png)