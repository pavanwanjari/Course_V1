# Course_V1

Simple static landing funnel for the Excel course offer.

## Current flow
1. User lands on `index.html` and fills lead details.
2. User completes Razorpay payment.
3. User verifies purchase email on `check_email.html`.
4. User accesses materials on `Excel_success_v3.html`.

## Analytics dashboard (private)
- Shared tracker script: `analytics.js`
- Dashboard page: `analytics_dashboard.html`
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

## Next production improvements
- Move payment verification fully to backend/webhook and grant signed access tokens.
- Persist lead + payment records to a secure database.
- Move dashboard auth and analytics storage to server-side (best security).
