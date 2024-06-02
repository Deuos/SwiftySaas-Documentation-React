# Authentication Setup

Step 1: Create an account with [Supertokens](https://supertokens.com/).

Step 2: Select Email password + Social Login

Step 3: Select Prebuilt UI

Step 4: Finish all steps in Supertokens

##### Frontend Setup

**Env Setup**

In your .env.example please rename it to .env

`VITE_APP_FRONTEND_URL="http://localhost:3000" `

`VITE_APP_BACKEND_URL="http://localhost:4000" `

For development purposes use these URLs, `http://localhost:3000` will be accessible by your browser while `http://localhost:4000` will be your API, so your backend.

When you are in production mode rename the urls to something like this.

`VITE_APP_FRONTEND_URL="https://swiftysaas.com" `

`VITE_APP_BACKEND_URL="https://api.swiftysaas.com" `

**Frontend Supertoken Config**

To configure visit `Frontend/Src/services/supertokens/supertokens.tsx`

Most of its already configured for you.

`getRedirectionURL`, once a user signs in, they will be redirected to `/Profile`. If you want to change the url post sign in or sign up. Change it to whatever path you desire.

In `recipeList`, `EmailVerification` is currently Required, so a user does need to verify their email post signup. To make optional email verification, change it from `Required` to `Optional`. Both on Frontend and Backend Supertoken Config. Alternativity you will need to remove EmailVerificationClaim for each of the check routes. View [Supertokens documentation](https://supertokens.com/docs/thirdparty/common-customizations/email-verification/about) for more information.

To configure the look of the Supertokens Sign In/Sign Up UI look at this [documentation](https://supertokens.com/docs/passwordless/common-customizations/styling/changing-style) provided by them.

##### Backend Setup

**Env Setup**

Please do the same for the .env in your backend

In your .env.example please rename it to .env

`VITE_APP_FRONTEND_URL="http://localhost:3000"`

`VITE_APP_BACKEND_URL="http://localhost:4000"`

For development purposes use these urls, Localhost:3000 will be accessible by your browser while Localhost:4000 will be your api, so your backend.

When you are in production mode rename the urls to something like this.

`VITE_APP_FRONTEND_URL="https://swiftysaas.com"`

`VTE_APP_BACKEND_URL="https://api.swiftysaas.com"`

Please add Supertoken Urls and Api Keys, [click here](https://supertokens.com/dashboard-saas) for the link

`SUPERTOKENS_CONNECTIONURI=""`

`SUPERTOKENS_APIKEY=""`

**Backend Supertoken Config**

To configure visit `Backend/src/services/supertokens/supertoken.ts`

If you like to use your own custom email address for Password reset, Verify Email, via Supertokens. You can forward the emails using the `smtpSettings`, which is already prefilled out, and you just need to update it with your information all allow for it to be used. Then in `recipeList` uncomment the `emailDelivery` section.

For EmailVerfication, change from Optional to Required. But make sure to keep it the same on both Frontend and Backend.

##### User Dashboard Setup

To set up your User Dashboard, which will allow you to manage your users, you can use the insertions below to help you set it up. But make sure that your backend server is running, if you haven't set up your MongoDB database then it will run into errors due it it not being configured.

Dashboard Email and Password will be different from the website Sign In/Sign up. To create your Admin account for Dashboard, you will need your API key, and the limit is 3 Admin Accounts on the Free Plan.

To start, please run your Backend server, via npm run start

In your browser visit, `http://localhost:4000/auth/dashboard` or in your production mode the path will be the same

If you are in **Mac/Linux** use the following command.

`curl --location --request POST 'YOURSUPERTOKENURL' \ --header 'rid: dashboard' \ --header 'api-key: <YOUR-API-KEY>' \ --header 'Content-Type: application/json' \ --data-raw '{"email": "<YOUR_EMAIL>","password": "<YOUR_PASSWORD>"}'`

If you are on **Windows**, you will need to use [Postman](https://www.postman.com/) which is a free API calling service to test your API calls.

Paste the same line into the URL box and it will auto-configure and ask you for the password, and email, and URL link.

This will create your Email and Password for your Admin. From their, you can directly access the user accounts created, and change passwords, emails, etc.
