# Main page (/)
On the main page, the user sees a full-screen menu with popular and/or special offers on top and the rest of the menu items on the bottom.
Out-of-stock or "coming soon" items (if any) are disabled (grayed out) and show up last.

Also, there is an autocomplete filter on the top of the page for a quick start.

Once the user clicks on one item from the menu - the user gets redirected to the "/new-order" page.

# New order page (/new-order)
On the new-order page, users see a 3-column layout.

Column 1 is the same as the main page, but this time it has a 20% width.

Column 2 is the "builder" section, which has 60% width and contains a form, where users can tweak the selected item - like toppings, quantity, etc. and add it to the final order.

Column 3 is 20% width and contains a list of items (which it's details and price) added to the order. Users can cancel items or edit them before submitting the final order.

Users can also add discounts/promo codes (if available).

At the bottom of the 3rd column, there is a total price and a button to submit a final order.

All calculations are made on the server-side.

[extra feature] While the user keeps editing the order - we store it in session storage. After the user submits the order - we clear the order from the session storage and assign it a UUID on the backend side.
Session storage can be replaced with DB storage - such order will have a status "draft", so the user can start making an order from one device and continue from another (ex. PC and phone).

[extra feature] In case, if we store a draft order on the server with a UUID - you can share this UUID with your friends (and/or family) so everybody can pick and choose what they want and add to it the main order. This will require WebSocket for live updates.

There's a "reset order" button, so the user can clear the order and return back the main page. But before that - we show a confirmation dialog, so the user can cancel reset and continue with the order.

[extra feature] Once a user submits the order to the backend - it gets UUID assigned, along with createdAt, and authenticated userID (if available).
While the order is "pending" it can be canceled.
Once an order is "in-progress" or "delivered" it can't be canceled.

[extra feature] Authorized users can save orders as a template, so they don't have to set the order from scratch every time.

Every item in the order shows as a separate card, which includes item name, details (if any), qty, and cost.
There's a cancel ("X") button on the card that removes the item from the order (with confirmation dialog).
There's also an "edit" item button - clicking on it will load the selected item to Column 2 (customization form).