# Seo

##### Google Analytics Setup

1. Create a [Google Analytics account](https://analytics.google.com/analytics/web/?authuser=0#/provision/SignUp) and create a new Ga4 Property for your domain. We will use Google Analytics because they have the best tracking out there.
2. In your Frontend folder, go to `main.tsx` and add your Ga4 Property in the ID section. This will initialize ga4 throughout your app.
3. To alter pageview settings, change the settings at `frontend/src/additionalcomponents/analytics/PagetrackGa4.tsx`

##### Seo Example

1. You can call `Seo.tsx` anywhere on your pages to optimize the Metadata for a certain page. Look at `Frontend/src/services/seo/Seo.tsx` to preset the images or add additional metadata for your pages. Place any public images into your `Public` folder so it's accessible by URL.
2. To test out metadata locally you can use extensions like [Open Graph Preview](https://addons.mozilla.org/en-US/firefox/addon/open-graph-preview-and-debug/) (Firefox Only) or [META SEO Inspector](https://chromewebstore.google.com/detail/ibkclpciafdglkjkcibmohobjkcfkaef?hl=en) (Chrome Only)

##### SiteMap

1. In your `public` folder, there should be a sitemap premade for you. You can edit it or ask chatgpt to automatically update it with your routes.
2. Your `robots.txt` file should be similar to your `sitemap.xml`
