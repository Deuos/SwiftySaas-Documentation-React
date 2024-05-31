# Payment

##### Stripe Payment Setup


*Currently this is boilerplate is configured for One-time-Payments, you can view Stripe docs to add subscription based payments. Which will be added to this boilerplate in the future.*

1. Create a account with [Stripe](https://stripe.com/), you won't need any personal details for test mode, but in production mode it will ask for your ssn or business details.
2. Once logged in, you will see to Developers, and keys, and you will see two keys. Publishable Key and Secret Key.
3. In your backend .env put the Secret key into your STRIPE_APIKEY="", and in your frontend .env put the Publishable Key into the VITE_APP_STRIPE_PUB_KEY=""
4. For Payments the backend will create a session with the userId and it will generate a embedded checkout form in your frontend. Pass the priceID for the product you created from the frontend.
5. 1. This is the route for the payment api backend/src/services/stripe/payment.ts
   2. This is the route for the frontend where you will pass the priceId - frontend/src/routes/protected/payment/paymentcomponents/CheckoutForm.tsx
   3. 
6. For Webhooks `Backend/src/services/stripe/webhook.ts` you can use the Stripe CLI, which under developers and then webhooks and test webhooks locally, you will receive a webhook secret which you will put into the backend .env and stripe provides good documentation for how this works.
   1. The default setup for this boilerplate, is that it will delete User role, and Add Paid role to user, so the user can access the paid routes and user routes.
7. For latest price updates, the backend will fetch the price from stripe and send it your frontend. The route is located in Backend/src/routes/public/pricetable/price.ts. In your frontend Pricing componentt you can display the price. Frontend/src/dragdropcomponents/Pricing.tsx

###### LemonSqueezy Payment Coming Soon...
