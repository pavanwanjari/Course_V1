# Course_V1

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

## Analytics dashboard (private)
- Shared tracker script: `analytics.js`
- Dashboard page: `analytics_dashboard.html`
- Dashboard is protected by user login (`owner` / `partner`) and session-based access.
- Clear analytics is double-protected:
  1. Requires typing `CLEAR ALL`
  2. Requires re-entering valid access key

## Next production improvements
- Move payment verification fully to backend/webhook and grant signed access tokens.
- Persist lead + payment records to a secure database.
- Move dashboard auth and analytics storage to server-side (best security).
