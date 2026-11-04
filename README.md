MUHAMMAD TALHA NASAR — WEBSITE UPDATE
=====================================

FILES
- index.html: existing storefront with Supabase published-product feed.
- admin.html: private admin sign-in and product manager.
- supabase-config.js: your Supabase project URL and publishable key.

IMPORTANT LIMITATIONS / CHECKS
1. This is an initial product-catalogue integration, not a complete ecommerce checkout.
2. Existing demo cart/order behaviour in the original storefront is still a front-end demo. Do not accept real payments/orders yet.
3. The storefront falls back to the original sample products if Supabase returns no published products.
4. The current category buttons in the original template are sample categories. The new admin uses the categories table; categories must exist in Supabase before adding products.
5. Admin sign-in requires the existing Supabase Auth user whose UID is configured in admin.html.
6. Do not expose a Supabase service-role/secret key in any website file.

SUPABASE SETUP
- Ensure the four Storage policies exist for bucket product-images.
- In Authentication settings, disable public sign-ups after confirming your admin user exists.
- Add categories in Supabase Table Editor > categories, for example:
  Fragrances | fragrances
  Leather Craft | leather
  Eyewear | eyewear
  Watches | watches
- RLS should match the policies you already ran. Public product SELECT must only permit status='published'.

DEPLOY TO GITHUB PAGES
1. Download and unzip this package.
2. Open your GitHub repository for the website.
3. Upload/replace index.html, and upload admin.html and supabase-config.js into the repository root.
4. Commit changes.
5. Wait for GitHub Pages to deploy.
6. Public website: your existing GitHub Pages address.
7. Admin page: add /admin.html to the end of that address.

SECURITY
The admin page is not linked in the public navigation, but anyone can discover its URL. Actual access is controlled by Supabase Auth and RLS. Keep your password private. The publishable key is intentionally public; the service-role/secret key must never go in these files.

NEXT
Before deploying, test the admin page locally or on a private branch. Confirm you can sign in, add a draft, and publish it. Then verify the published item appears on the storefront.
