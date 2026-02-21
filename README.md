# Course_V1

Simple static landing funnel for the Excel course offer.

## Current flow
1. User lands on `index.html` and fills lead details.
2. User completes Razorpay payment.
3. User verifies purchase email on `check_email.html`.
4. User accesses materials on `Excel_success_v3.html`.

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
- Use server-side analytics storage with daily conversion reports.
