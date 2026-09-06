# EduCash V3 — Expanded Platform Prototype

This version adds a demo admin/content-management layer on top of the professional front end.

## New
- Admin dashboard (`admin.html`)
- Demo user/content data stored in browser localStorage
- Resource publish/unpublish controls
- Job approval and report controls
- Add resource/job demo actions
- Dashboard statistics
- Production safety checklist

## Important
The admin dashboard is intentionally a prototype. It must NOT be exposed as a real admin system without server-side authentication and authorization.

## To turn EduCash into a real service
Recommended production architecture:
- Frontend: Next.js/React or another production web framework
- Backend/API: Node.js/TypeScript or Python
- Database: PostgreSQL
- Authentication: secure email/password + optional Google login
- File storage: object storage with signed URLs
- Payments: a Ghana-supported payment processor with webhooks
- Email: transactional email provider
- Ads: an approved advertising network after traffic and policy review
- Moderation: admin review + report/appeal workflow
- Security: HTTPS, password hashing, CSRF protection, rate limiting, validation and audit logs

Do not collect mobile-money PINs, card PINs, passwords for other services, or one-time security codes.


## V4 additions
See `PRODUCTION_SETUP.md`, `supabase/schema.sql`, `.env.example`, and `server/payments.js` for the production integration starter.


## V5 additions
`account.html`, `supabase-client.js`, and `config.example.js` provide the real authentication connection starter. Follow `PRODUCTION_SETUP.md` before using it publicly.


## V6 additions
Student dashboard, authenticated session check, logout, password-reset flow, and dashboard navigation were added. Configure Supabase and its redirect URLs before testing these features.
