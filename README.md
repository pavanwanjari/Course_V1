# Course_V1

Simple static landing funnel for the Excel course offer.

## Current flow
1. User lands on `index.html` and fills lead details.
2. User completes Razorpay payment.
3. User verifies purchase email on `check_email.html`.
4. User accesses materials on `Excel_success_v3.html`.

## Next production improvements
- Move payment verification fully to backend/webhook and grant signed access tokens.
- Persist lead + payment records to a secure database.
- Add conversion analytics dashboard and funnel alerts.
