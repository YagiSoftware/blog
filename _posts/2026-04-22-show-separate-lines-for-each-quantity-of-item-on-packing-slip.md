---
layout: post
title: Show separate lines for each quantity of item on packing slip
date: 2026-04-22 17:38 +0800
---

Sometimes packing mistake can happen, especially for a line item that contains multiple quantity, packers might mistakenly pick only 1 quantity for a line item (as typically one item usually only has one quantity). This would cause customer dissatisfaction, when customers found out they have received less quantity than they have ordered, and you would have to arrange additional shipment to ship the missed quantities.

To reduce the occurrence of packing mistake, you can display an item multiple times in the packing slip, if the item quantity is more than one.


In this tutorial, you will be guided to modify the packing slip template code, to achieve the following output of packing slip : 

![Desired output](https://img.yagisoftware.com/33-separate-line-items-packing-slip/intro.png)

First, go to your store settings, and select "Shipping and delivery" : 

![Shipping and delivery setting](https://img.yagisoftware.com/33-separate-line-items-packing-slip/settings_menu.png)

Next, scroll down and select "Packing slip template" : 

![Packing slip template](https://img.yagisoftware.com/33-separate-line-items-packing-slip/template_menu.png)

In the packing slip template code window, search for the line `{% raw %}{% for line_item in line_items_in_shipment %}{% endraw %}` , which should be around line 113.

Then insert this code, below that line :  
`{% raw %}{% for i in (1..line_item.shipping_quantity) %} {% endraw %} `

![Packing slip template code modification](https://img.yagisoftware.com/33-separate-line-items-packing-slip/code1.png)

Next, we will need to change the display of quantity to "1", from the original quantity (as we are outputting each quantity as each own row). 

Search for the line `{% raw %}{{ line_item.shipping_quantity }}{% endraw %}` , and insert "Qty: 1" above it. (you can change this text to "Quantity: 1", or other text you like).


![Packing slip template code modification](https://img.yagisoftware.com/33-separate-line-items-packing-slip/code2.png)

After inserting the "1" quantity text, we will then proceed to remove the original quantity below it. (`{% raw %}{{ line_item.shipping_quantity }} of {{ line_item.quantity }} {% endraw %}` )

![Packing slip template code modification](https://img.yagisoftware.com/33-separate-line-items-packing-slip/code3.png)

Finally,  insert an additional `{% raw %}{% endfor %}{% endraw %}` , right above the `{% raw %}{% endfor %}{% endraw %}` line, that is located below the "Qty: 1" text. (which should be around line 157)

![Packing slip template code modification](https://img.yagisoftware.com/33-separate-line-items-packing-slip/code4.png)

Click "Save", then go to your orders page, choose an order and click "Print" > "Print Packing slips", and you should see the updated packing slip template.

(If anything goes wrong, you can click the "Revert to default" button beside the "Save" button located at bottom, to revert back to the default packing slip code)

![Print packing slip](https://img.yagisoftware.com/33-separate-line-items-packing-slip/print_slip.png)

<!-- offer fully edited code to purchase -->

If you are not confident with the code modification, and prefer to just copy paste the updated packing slip template code and replace, you can purchase the (copy-pastable) updated packing slip template code here: [https://axelkee.gumroad.com/l/packing-slip-separate-line-items](https://axelkee.gumroad.com/l/packing-slip-separate-line-items)


