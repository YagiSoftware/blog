---
layout: post
title: How to hide Sidekick in Shopify Admin
description: In the custom CSS google chrome extension, input the following code
date: 2026-10-01 15:57 +0800
---


Recently Shopify has updated their Shopify Admin design, named "Polaris 2.0" . With the new design, Shopify has slapped a permanent "Work with Sidekick" box at the bottom of every page (except the home page hah), which can obstruct Admin operations, and cause confusion for merchants.

I use the full screen mode to edit code in Shopify Flow often, and the Sidekick box at the bottom has forced me to add a few empty lines below (to push the code up), as the code would have been obstructed by the Sidekick box : 

![Stupid](https://img.yagisoftware.com/35-how-to-hide-sidekick/stupid_sidekick.png)

If you are using Google Chrome, you can hide the Sidekick box, by adding some custom CSS code, with the help of Chrome extension.


I am using the ["Custom CSS by Denis" Chrome extension](https://chromewebstore.google.com/detail/custom-css-by-denis/cemphncflepgmgfhcdegkbkekifodacd?) , as it is a very lightweight extension, with no ads and featured by Google.

![Chrome extension](https://img.yagisoftware.com/35-how-to-hide-sidekick/chromeext.png)

You can install [this extension]((https://chromewebstore.google.com/detail/custom-css-by-denis/cemphncflepgmgfhcdegkbkekifodacd?)), and then after installation, go to your store Admin : 

![Open Admin](https://img.yagisoftware.com/35-how-to-hide-sidekick/step0.png)

Then open the extension (Custom CSS by Denis) : 
![Open Admin](https://img.yagisoftware.com/35-how-to-hide-sidekick/step1.png)

Ensure the domain shown is "admin.shopify.com", and click "Grant permission" :
![Open Admin](https://img.yagisoftware.com/35-how-to-hide-sidekick/step2.png)

Then paste in the following CSS code : 

```css
div[class^='_GlobalRibbonContainer'] { display: none }
```
![Open Admin](https://img.yagisoftware.com/35-how-to-hide-sidekick/step3.png)


After pasting, click your mouse anywhere to close the edit dialog, then refresh the page.

The pesky Sidekick box at the bottom should be gone now, enjoy! (If it didn't work, try quitting Google Chrome and open it again)
