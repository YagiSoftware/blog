---
layout: post
title: How to hide products from search in Shopify store
date: 2021-06-27 17:42 +0800
image: https://mugshotbot.com/m/AKOkh1ZJ
---



Sometimes you might have a special product or service which you don't want a customer to be able to search from your store search or Google search, as you want to only let certain customers to access it via direct link from email or from an Adwords campaign.



Changing the product status to draft does hide it from search, but it would make it unavailable to those who have a direct link as well, hence this method does not work.



There's ways to hide product in search using product tags and editing code on the collection or search page template, but if you are not familiar with coding, it can be risky to do so as it might cause customer to unable to browse the product collections if you happen to accidentally mess up the collection page.



Fortunately, you can hide product from search without having to edit the code on your collection or search page.




You can utilize the "metafields" function from Shopify to hide the product from search. If you haven't heard of the term "metafields" before, metafields are extra pieces of data that you can attach to products, customers, orders, and other objects in your Shopify store.



Currently Shopify doesn't have an official way to edit metafields for products, you would have to download third party apps to be able to edit metafields. I recommend using [Metafields Custom Field Master](https://apps.shopify.com/metafields-manager-by-hulkapps?) app to edit metafields, as they have a generous free plan that lets you add metafields to unlimited products, I will be using this app for the following steps.



After installing the Metafields app, open it :
![open metafields app](https://yagisoftware.s3.amazonaws.com/2-how-to-hide-products-from-search-in-shopify-store/mt1.png)



Then select "Product":

![metafields product](https://yagisoftware.s3.amazonaws.com/2-how-to-hide-products-from-search-in-shopify-store/mt2.png)



Select the product you want to hide from search : 

![select product to hide from search](https://yagisoftware.s3.amazonaws.com/2-how-to-hide-products-from-search-in-shopify-store/mt3.png)



Fill in the metafields as follows :



Namespace: **seo**

Key: **hidden**

Type: **Integer**

Integer: **1**


Then click "Save".

![fill in metafields](https://yagisoftware.s3.amazonaws.com/2-how-to-hide-products-from-search-in-shopify-store/mt4.png)



And now this product will not show up in your store search and search engine like Google. You can try search name of this product in your store and it won't appear in the search result. How this works is [explained by Shopify here](https://shopify.dev/tutorials/manage-seo-data-with-admin-api#hide-a-resource-from-search-engines-and-sitemaps).





## Hide product from catalog page

Now that your product is hidden from search, the next place we are going to hide it is from the "All" catalog. By default, all Shopify stores have a "Catalog" page which show all available products (with stock) in your store, this page is usually located in `your-store.myshopify.com/collections/all` .



To override the default behavior of showing all products on the "Catalog" page, we will have to create a collection, and name its title as "**All**". ([Official Shopify guide here](https://help.shopify.com/en/manual/online-store/themes/change-catalog-page))



Create a collection, and name the title as "**All**".

![collection create](https://yagisoftware.s3.amazonaws.com/2-how-to-hide-products-from-search-in-shopify-store/collection1.png)


Set the collection to "**Manual**", then click "**Save**"

![collection manual](https://yagisoftware.s3.amazonaws.com/2-how-to-hide-products-from-search-in-shopify-store/collection2.png)



Then next, select all products and add them to the "**All**" collection, and then select the product you want to hide from the catalog, and click "Remove from collection", and select the "**All**" collection.

![collection all hide](https://yagisoftware.s3.amazonaws.com/2-how-to-hide-products-from-search-in-shopify-store/collection3.png)



Now the product which you have removed from the "All" collection will not show up in the Catalog page.



## Undo hide product

If you want the product to show on search, simply remove the metafields (namespace seo, key hidden) and click "Save", also remember to add back the product to the "All" collection.

<script async data-uid="3f46096ca1" src="https://yagisoft.ck.page/3f46096ca1/index.js"></script>