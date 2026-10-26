---
name: zero-cost-saas-stack
description: Architects and deploys production-grade, zero-dollar serverless SaaS systems using generous free-tier integrations (Cloudflare, Turso, Supabase, Resend).
---

# $0/Month Production SaaS Architect

This skill guides the construction and deployment of complete, scalable SaaS architectures supporting up to 50,000 monthly active users on legitimate $0 cloud free tiers.

## 1. Zero-Cost Cloud Ecosystem

1. **Edge Frontend & Compute**:
   - Cloudflare Pages / Workers: Unlimited requests for static hosting, 100,000 requests/day free edge compute with global CDN.
2. **Database & Storage**:
   - Turso (LibSQL / SQLite): 500 databases, 9GB storage, 1 billion row reads/month free.
   - Cloudflare R2: 10GB object storage, zero egress fees (no bandwidth billing surprises).
3. **Auth & Identity**:
   - Supabase Auth: 50,000 monthly active users (MAU) free with OAuth2 and email magic links.
4. **Transactional Email**:
   - Resend: 3,000 emails/month free with verified domain DKIM/SPF.

## 2. Hard Cost Safeguards
- Configure hard spending limits ($0 budget cap) across all cloud provider dashboards.
- Cache public API responses at the edge (`stale-while-revalidate`) to stay comfortably within free compute quotas.
