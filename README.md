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
