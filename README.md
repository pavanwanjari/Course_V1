# Course_V1

Data Analytics training website with multi-course pages, payment flow, access verification, and analytics.

## Courses and offer pricing
- Advance Excel: MRP ₹999 → Offer ₹49
- Python: MRP ₹3000 → Offer ₹99
- Power BI: MRP ₹2500 → Offer ₹99
- Tableau: MRP ₹2500 → Offer ₹99
- SQL (MySQL): MRP ₹2000 → Offer ₹99
- Data Analytics Combo (all courses): MRP ₹10,999 → Offer ₹399

## Website flow
1. User lands on `index.html` (Data Analytics homepage).
2. User can open dedicated course pages:
   - `course_advance_excel.html`
   - `course_python.html`
   - `course_power_bi.html`
   - `course_tableau.html`
   - `course_mysql.html`
3. Payment is done from `index.html` buy section.
4. On success, user is redirected directly to `Excel_success_v3.html` with course access links.
5. Returning users can use `check_email.html` to verify and regain access.

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
Simple static landing funnel for the Excel course offer.

## Current flow
1. User lands on `index.html` and fills lead details.
2. User completes Razorpay payment.
3. On successful payment, user gets direct access to `Excel_success_v3.html`.
4. Returning users can use `check_email.html` (same email) to regain access.

## Payment + sheet sync behavior
- Payment success now:
  - marks user as paid in current session for instant course access
  - stores paid email locally (`paidUsers`) for same-device re-access
  - attempts to save purchase in Google Sheet web app using:
    - `?action=save&...`
    - fallback legacy request `?...` if first response is not explicit success
3. User verifies purchase email on `check_email.html`.
4. User accesses materials on `Excel_success_v3.html`.

## Analytics dashboard (private)
- Shared tracker script: `analytics.js`
- Dashboard page: `analytics_dashboard.html`
- Dashboard is protected by user login (`owner` / `partner`) and session-based access.
- Clear analytics is double-protected:
  1. Requires typing `CLEAR ALL`
  2. Requires re-entering valid access key

- Dashboard is now protected by user login (`owner` / `partner`) and session-based access.
- Clear analytics is **double-protected**:
  1. Requires typing `CLEAR ALL`
  2. Requires re-entering valid access key

### Default dashboard users
- `owner` with key `owner@123`
- `partner` with key `partner@123`

> Immediately change these keys in `analytics_dashboard.html` before production use.

### How to change keys safely
1. Open browser console.
2. Generate SHA-256 hash for your new key:
   ```js
   async function h(v){
     const d = await crypto.subtle.digest("SHA-256", new TextEncoder().encode(v));
     return [...new Uint8Array(d)].map(b=>b.toString(16).padStart(2,"0")).join("");
   }
   h("your-new-key").then(console.log)
   ```
3. Replace hash value in `DASHBOARD_USERS` in `analytics_dashboard.html`.
## Analytics dashboard (new)
- Shared tracker script: `analytics.js`
- Dashboard page: `analytics_dashboard.html`
- Tracked events now include:
  - landing + checkout events (`buy_now_clicked`, `payment_success`, `payment_failed`)
  - verify flow events (`verify_started`, `verify_success`, `verify_not_found`, `verify_error`)
  - dashboard usage event (`dashboard_viewed`)

### How to use
1. Open the website and perform user actions.
2. Visit `analytics_dashboard.html`.
3. Review summary cards, event counts, and recent event logs.

> Note: this dashboard uses browser `localStorage`, so it is ideal for MVP/demo. For production, send the same events to GA4 or your backend and visualize in Looker Studio/Metabase.

## Next production improvements
- Move payment verification fully to backend/webhook and grant signed access tokens.
- Persist lead + payment records to a secure database.
- Move dashboard auth and analytics storage to server-side (best security).


## Multi-course pages (new)
- Index now includes a course catalog with links to dedicated pages:
  - `course_advance_excel.html`
  - `course_python.html`
  - `course_power_bi.html`
  - `course_tableau.html`
  - `course_mysql.html`
- Each course page includes:
  - Why course is important
  - Complete roadmap (step-by-step)
  - Resources options (PDF, videos, interview questions)
  - Single-course and combo pricing with buy/contact CTA
- Use server-side analytics storage with daily conversion reports.
## Next production improvements
- Move payment verification fully to backend/webhook and grant signed access tokens.
- Persist lead + payment records to a secure database.
- Add conversion analytics dashboard and funnel alerts.
