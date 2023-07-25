---
layout: post
title: How to hide products from search in Shopify store
date: 2023-07-18 17:42 +0800
image: https://mugshotbot.com/m/AKOkh1ZJ
description: Go to your Shopify Admin, select the product which you want to hide from store search and search engine, scroll down to the 'Metafields' section, then type "1" for the 'Hide from search engine' field (that we created earlier) ...
---

Last updated at 18 July 2023, to use Shopify's native metafields editor.

Sometimes you might have a special product or service which you don't want a customer to be able to search from your store search or Google search, as you want to only let certain customers to access it via direct link from email or from an Adwords campaign.


Changing the product status to draft does hide it from search, but it would make it unavailable to those who have a direct link as well, hence this method does not work.


With the recent metafields feature released by Shopify, you can hide product from search without having to edit the code on your collection or search page. There is a preset metafields value we can set to instruct Shopify to hide the product from the store search and also Google search (and other Search Engine like Bing etc).

Here's a video walkthrough (you can scroll down for detailed steps) :

<div class="video-container">
<iframe width="560" height="315" src="https://www.youtube.com/embed/kbtC8RNsmXY?rel=0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

<br><br><br>

Go to your store settings, and select "**Custom Data**" :

![Select custom data](https://img.yagisoftware.com/2-how-to-hide-products-from-search-in-shopify-store/1custom_data.png)

Select **Products** in the Metafields list :

![Select products](https://img.yagisoftware.com/2-how-to-hide-products-from-search-in-shopify-store/2products.png)

Click **Add definition** :

![Add definitions](https://img.yagisoftware.com/2-how-to-hide-products-from-search-in-shopify-store/3add_def.png)


For the Namespace and key, type in "**seo.hidden**" (must be exactly this), then for the "Name" and "Description", you can type any text which you can use to identify this metafield later on. (We use "Hide from store search and search engine")
![type in "seo.hidden" into namespace](https://img.yagisoftware.com/2-how-to-hide-products-from-search-in-shopify-store/4namespace.png)


Click "Select type", then select "Integer", then click "Save" to save this metafield definition.

![set type to integer](https://img.yagisoftware.com/2-how-to-hide-products-from-search-in-shopify-store/5integer.png)


Then go to the product which you want to hide from store search and search engine, scroll down to the "Metafields" section, then type "1" for the "Hide from search engine" field (that we created earlier). Typing "1" will hide the product from store search and search engine like Google search results etc.


![set product to hidden](https://img.yagisoftware.com/2-how-to-hide-products-from-search-in-shopify-store/6set_hidden.png)




And now this product will not show up in your store search and search engine like Google. You can try search name of this product in your store and it won't appear in the search result. How this works is [explained by Shopify here](https://shopify.dev/tutorials/manage-seo-data-with-admin-api#hide-a-resource-from-search-engines-and-sitemaps).


Although the product is hidden from search, it might still appear on the "All products" catalog in your store. In the next section, we will look into how to remove it from the catalog.


## Hide product from catalog page

Now that your product is hidden from search, the next place we are going to hide it is from the "All" catalog. By default, all Shopify stores have a "Catalog" page which show all available products (with stock) in your store, this page is usually located in `your-store.myshopify.com/collections/all` .



To override the default behavior of showing all products on the "Catalog" page, we will have to create a collection, and name its title as "**All**". ([Official Shopify guide here](https://help.shopify.com/en/manual/online-store/themes/change-catalog-page))



Create a collection, and name the title as "**All**".

![collection create](https://img.yagisoftware.com/2-how-to-hide-products-from-search-in-shopify-store/collection1.png)


Set the collection to "**Manual**", then click "**Save**"

![collection manual](https://img.yagisoftware.com/2-how-to-hide-products-from-search-in-shopify-store/collection2.png)



Then next, select all products and add them to the "**All**" collection, and then select the product you want to hide from the catalog, and click "Remove from collection", and select the "**All**" collection.

![collection all hide](https://img.yagisoftware.com/2-how-to-hide-products-from-search-in-shopify-store/collection3.png)



Now the product which you have removed from the "All" collection will not show up in the Catalog page.



## Undo hide product

If you want the product to show on search, simply remove the value for the "hide from search engine" metafield field in your product page, and click "Save", also remember to add back the product to the "All" collection.
