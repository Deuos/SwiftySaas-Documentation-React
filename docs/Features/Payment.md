# Payment

##### Stripe Payment Setup

*Currently, this boilerplate is configured for one-time payments, you can view Stripe docs to add subscription-based payments. Which will be added to this boilerplate in the future.*

1. Create an account with [Stripe](https://stripe.com/), you won't need any personal details for test mode, but in production mode, it will ask for your SSN or business details.
2. Once logged in, go to `Developers` and then `Keys`, and you will see two keys. `Publishable Key` and `Secret Key`.
3. In your backend .env put the Secret key into your `STRIPE_APIKEY=""`, and in your frontend .env put the Publishable Key into the  `VITE_APP_STRIPE_PUB_KEY=""`
4. For Payments, the backend will create a session with the userId and it will generate an embedded checkout form in your frontend. Pass the price for the product you created from the frontend.
   1. This is the route for the payment API `Backend/src/services/stripe/payment.ts`
   2. This is the route for the frontend where you will pass the priceId `Frontend/src/routes/protected/payment/paymentcomponents/CheckoutForm.tsx`
   3. 
5. For Webhooks `Backend/src/services/stripe/webhook.ts` you can use the `Stripe CLI`, which under `developers` and then webhooks and test webhooks locally, you will receive a webhook secret which you will put into the backend .env and stripe provides good documentation for how this works.
   1. The default setup for this boilerplate is that it will delete the `User role`, and Add a `Paid role` to the user, so the user can access the paid routes and user routes.
6. For the latest price updates, the backend will fetch the price from Stripe and send it to your frontend. The route is located in  `Backend/src/routes/public/pricetable/price.ts`. In your frontend Pricing component, you can display the price.  `Frontend/src/dragdropcomponents/Pricing.tsx`

###### LemonSqueezy Payment Coming Soon...
