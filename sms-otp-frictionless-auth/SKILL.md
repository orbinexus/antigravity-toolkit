---
name: sms-otp-frictionless-auth
description: Implements frictionless SMS OTP authentication using WebOTP API, rate limiting, and automated code detection across mobile browsers.
---

# Frictionless Mobile WebOTP Authentication

This skill guides passwordless phone number authentication leveraging modern browser WebOTP APIs for zero-friction mobile checkouts.

## 1. WebOTP API Protocol

1. **Browser Auto-Detection**:
   ```javascript
   if ('OTPCredential' in window) {
     const ac = new AbortController();
     navigator.credentials.get({ otp: { transport: ['sms'] }, signal: ac.signal })
       .then(otp => { document.getElementById('otp-input').value = otp.code; submitAuth(); })
       .catch(err => console.log(err));
   }
   ```
2. **SMS Formatting Standards**:
   - The final line of the SMS must contain the WebOTP domain token:
     `@yourdomain.com #1234`
   - Android and iOS automatically detect the token and fill the input without requiring user copy-pasting.

## 2. Rate Limiting & Abuse Prevention
- Limit SMS dispatches to max 1 per 60 seconds per phone number and IP.
- Implement exponential backoff after 3 consecutive failed code submissions.
