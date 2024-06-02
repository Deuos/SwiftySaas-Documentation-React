# Email

##### Supertokens Email Setup

If you don't enable this feature, SuperTokens will send password reset and email verification emails via no-reply@supertokens.com. However, if you prefer to use your own email address, such as no-reply@swiftysaas.com, you can do so for free.

To configure this, head over to `backend/src/services/supertokens/supertoken.ts`, where you should uncomment the lines related to `SMTPService` and `smtpSettings` and fill in the required information. For more information, please refer to the [SuperTokens documentation](https://supertokens.com/docs/emailpassword/email-delivery/smtp/configure-smtp).

##### ConvertKit Setup

You can choose other services for sending emails, like SendGrid, MailChimp, etc. For authentication like Password reset and email verification, Supertoken handles all email sending for you, automatically via your custom email or their email.

So, why ConvertKit? Their free tier is okay, but you will have to do things manually, and automation requires a monthly subscription. However, their UI and process are easy to set up. One key feature is the mandatory inclusion of your business address in emails, as required by the [US CAN-SPAM Act](https://www.fcc.gov/general/can-spam). With ConvertKit, you can use their business address even with a free account, and they will forward all mail you receive by email. This is perfect for developers like us who don't have a physical business address yet.

1. Sign Up for ConvertKit
2. Head to `Settings`, `Advanced`, Add the API Key to `EMAIL_CONVERTKIT_APIKEY=""` and API Secret to `EMAIL_CONVERTKIT_APISECRET=""`
3. You can do more advanced things with their API by sending HTTPS requests from your backend to the ConvertKit servers with your authentication, such as adding users or sending emails.
4. For this boilerplate, we are just saving Email Addresses to two tags called Welcome and User.

   1. Head over to `Subscribers`, `Create a Tag`.
   2. To get the list of the IDs of the Tags, so we can automatically add users post sign up to `Welcome` and `User` tags in ConvertKit.
   3. This is [ConvertKit docs](https://developers.convertkit.com/#list-tags) for how to do it more in depth. I will show you a basic example.
   4. Use this curl with your APIKEY to get a list of the tags you created - `curl https://api.convertkit.com/v3/tags?api_key=<your_public_api_key>`
   5. Copy the Ids for `Welcome` and `User` and paste it in the `addUserToEmailList`, remove the default Ids and add yours in the `tags:[]`, also in the `url of the post`, remove the `default id` and set it to `User id `this will be the default, so if others fail the user will be in the user tag.
   6. This is the path for the file `Backend/src/services/usermanagementprogress/postSignUp.ts`
