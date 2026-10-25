---
name: transactional-email-architect
description: Designs high-deliverability transactional email pipelines, responsive HTML/React email templates, and DNS authentication records (SPF, DKIM, DMARC).
---

# Transactional Email & Deliverability Architect

This skill guides the construction of spam-proof, pixel-perfect transactional emails (welcome series, password resets, receipts) using modern React Email / MJML frameworks and verified DNS standards.

## 1. Deliverability & DNS Authentication

1. **SPF, DKIM, & DMARC**:
   - Ensure proper DNS TXT records are configured to prevent domain spoofing.
   - Configure DMARC policy with alignment (`v=DMARC1; p=quarantine; rua=mailto:...`).
2. **Spam Trigger Mitigation**:
   - Maintain optimal text-to-image ratios; avoid single large image emails.
   - Include clear unsubscription and physical address footers where applicable.

## 2. Responsive HTML & Client Rendering
- Use React Email or MJML to compile bulletproof nested tables that render consistently across desktop Outlook, web Gmail, and iOS Mail.
- Inline critical CSS styles (`display: inline-block`, fallback web-safe font stacks: Arial, Helvetica, sans-serif).
- Handle webhook events for delivery confirmations, bounces, and spam complaints.
