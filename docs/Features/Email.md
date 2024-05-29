# Email

##### ConvertKit Setup

You can choose other methods for sending emails, for Authenication like Password reset, Email Verfication, Supertoken handles all email sending for you, automically via your custom email or their email.

So Why ConvertKit? Their free tier is ok, you will have to do things manually and automatication costs monthly subscription. But thier UI/Process is easy to setup, along with one key feature which is a mantory to include your business address under emails all commercial email required by law [US CAN-Spam ACT](https://www.fcc.gov/general/can-spam). With ConvertKit, you can use their business address even under a free account instead of your and they will send all mail you recieve by email. Which is perfect for developers like us who don't have a physical business address yet.

1. Sign Up for ConvertKit
2. Head to Settings, Advanced, Add the API Key to EMAIL_CONVERTKIT_APIKEY="" and API Secret to EMAIL_CONVERTKIT_APISECRET=""
3. You can do more advanced things with their API, which is just sending https requests from your backend to the convertkit servers with your authenication and adding users or send emails via that.
4. For this boilerplate, we are just saving Email Addresses to two tags called Welcome and User.
   1. Head over to Subscribers, Create a Tag.
   2. To get the list of the IDs of the Tags, so we can automatiocally add users post sign up to Welcome and User tags in ConvertKit.
   3. This is [ConvertKit docs](https://developers.convertkit.com/#list-tags) for how to do it more in depth. I will show you a basic example.
   4. Use this curl with your APIKEY to get a list of the tags you created - `curl https://api.convertkit.com/v3/tags?api_key=<your_public_api_key>`
   5. Copy the Ids for Welcome and User and paste it in the addUserToEmailList, remove the default Ids and add yours in the tags:[], also in the url of the post, remove the default id and set it to User id this will be the default, so if others fail the user will be in the user tag.
   6. This is the path for the file Backend/src/services/usermanagementprogress/postSignUp.ts
