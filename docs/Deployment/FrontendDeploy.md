# Frontend Deployment

##### [Render.com](Render.com) Recommended

The free tier on render is great, I currently have all my sites running on render so you can test it out yourself it the service is good or not.

1. Click `New`, `Static Site`
2. Connect your `Source Code` via Github, Gitlab, Bitbucket, etc.
3. Specify a `project name`, along with a `branch`
   1. **Build Command** `npm run build`
   2. **Publish Directory** `dist`
   3. Copy `.env` file into **Environments**
   4. Alter **Redirects/Rewrites** to **Source** `/*` **Destination** `/index.html` **Action** `Rewrite`
4. Adding **Custom Domains**, via `Settings`, `Custom Domains`, and add your `domain `and verify it.
5. Using **Cloudflare CDN** cache the websites to help boost the load times

##### Testing the App Locally

`npm run build`

`npm run preview`

You can view the build on localhost:3000 or change it via package.json preview script.
