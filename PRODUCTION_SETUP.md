
# EduCash V4 — Production Integration Starter

This version prepares EduCash for a real backend without putting secret credentials into the website.

## Recommended stack

**Supabase** can provide the PostgreSQL database, authentication and storage layer. Its Auth system supports email/password and other sign-in methods, and Row Level Security (RLS) can restrict database rows by user. See the official documentation:
https://supabase.com/docs

**Paystack** can handle EduCash Premium payments. Paystack supports Ghana mobile-money payments and GHS transactions. Payment secrets must remain on the server. See:
https://paystack.com/docs/

## Setup order

1. Create a Supabase project.
2. Run `supabase/schema.sql` in the Supabase SQL Editor.
3. Enable email/password authentication.
4. Create storage for study-material files and add RLS policies before allowing uploads.
5. Create a server environment using `.env.example`.
6. Install the server dependencies inside `server/`.
7. Add your Paystack test secret key to the server environment.
8. Test Premium payment in Paystack's test environment.
9. Implement and verify the Paystack webhook before activating Premium status.
10. Add server-side admin authorization; never rely on a browser-only admin flag.
11. Deploy the frontend and API over HTTPS.
12. Only after testing, switch to production payment keys.

## Revenue plan

EduCash can eventually use:
- display advertising after traffic/policy review,
- optional Premium membership,
- paid partner job listings,
- sponsored educational content,
- affiliate partnerships where appropriate.

Do not charge students for access to a job merely to “unlock” employment, and do not promise guaranteed earnings.

## Security

Never put:
- Paystack secret keys,
- Supabase service-role keys,
- database passwords,
- student passwords,
- mobile-money PINs,
- card PINs,
- one-time security codes

inside the public website or source repository.

The included server is a starter only; it still needs Supabase transaction recording, webhook-to-subscription mapping, rate limiting, logging, input validation and deployment configuration before production.


## V5: connect the real account system

1. Create a Supabase project.
2. Run `supabase/schema.sql`.
3. Copy `config.example.js` to `config.js`.
4. Put the Supabase project URL and **publishable key** in `config.js`. Do not put a service-role key in the browser.
5. Open `account.html` to test sign-up/login.
6. Configure the allowed Site URL and redirect URLs in Supabase Authentication settings.
7. Replace the demo localStorage account flow with this authenticated flow throughout the site.
8. Add server-side profile creation and admin authorization using database policies/claims.

Supabase's current JavaScript client supports `createClient`, email/password sign-up and `signInWithPassword`, and Supabase recommends its Auth + RLS model for authorization. citeturn0search0turn0search2

For Premium payments, keep using the V4 server route. Paystack's current documentation says Ghana supports Mobile Money and requires a webhook to receive the final payment status; supported Ghana providers include MTN, AirtelTigo/ATMoney and Telecel. citeturn0search8turn0search11


## V6: student dashboard
The dashboard checks the current Supabase session before displaying account information. Password reset uses Supabase's `resetPasswordForEmail()` and `updateUser()` flow. Configure the site's allowed redirect URLs in Supabase Auth settings before production.
