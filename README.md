# Course_V1

Data Analytics training website with multi-course pages, payment flow, access verification, and analytics.

## Courses and offer pricing
- Advance Excel: MRP ₹999 → Offer ₹49
- Python: MRP ₹3000 → Offer ₹99
- Power BI: MRP ₹2500 → Offer ₹99
- Tableau: MRP ₹2500 → Offer ₹99
- SQL (MySQL): MRP ₹2000 → Offer ₹99
- Machine Learning + Deep Learning: MRP ₹5000 → Offer ₹99
- Data Analytics Combo (all courses): MRP ₹10,999 → Offer ₹499

## Website flow
1. User lands on `index.html` (Data Analytics homepage).
2. User can open dedicated course pages.
3. Cart supports multiple course selection and combo override.
4. Payment is done via Razorpay from `index.html`.
5. On success, user is redirected directly to `Excel_success_v3.html` with links.
6. Returning users can use `check_email.html` to verify and regain access.

## Access + verification details
- `paidUsers` in localStorage is used for same-device quick access.
- Google Script verification is attempted using both:
  - `?action=check&email=...`
  - fallback `?email=...`
- Payment save to sheet is attempted using both:
  - `?action=save&...`
  - fallback legacy query params.

## Analytics files
- `analytics.js`
- `analytics_dashboard.html`


## UX updates
- Added interactive Why Data Analytics metrics section with animations.
- Added floating WhatsApp support button on homepage.
- Added About Us block with Owner Dashboard link (dashboard itself remains login-protected).
- Fixed verify-email logic to avoid false-positive access from partial responses like "NOT FOUND".
