# Scaling & Infrastructure Strategy

This document outlines the technical path from launching on $0/month services to scaling to handle 10,000+ active profiles seamlessly.

## Phase 1: MVP (0 to 1,000 Profiles) - The "Free" Stack
*Goal: Launching rapidly with zero upfront cloud costs while ensuring we aren't locked in.*

### Architecture
- **Frontend Hosting:** Vercel or Netlify (Free Tier). Excellent global CDN, out-of-the-box CI/CD from GitHub.
- **Backend Hosting:** Render or Railway (Free/Hobby Tier). Will spin down on inactivity, but sufficient for beta testing.
- **Database:** Supabase (PostgreSQL - Free Tier) or Neon.tech (Serverless Postgres). Provides 500MB free storage (plenty for 1k users).
- **Image Storage:** Cloudinary (Free Tier - 25GB bandwidth/month). We *must* compress images on the frontend before uploading to save space.
- **Authentication:** Spring Security with JWTs stored in local Postgres (Free) OR Supabase Auth / Firebase Auth.
- **Emails:** SendGrid or Postmark (Free tier allows ~100 emails/day for OTPs and notifications).

## Phase 2: Growth (1,000 to 10,000 Profiles) - The "Migration" Stack
*Goal: As user activity increases (complex searches, chat), the free tiers will throttle us. We must migrate to reliable, paid infrastructure.*

### Triggers to Migrate
- If database hits 400MB space left.
- If backend experiences constant cold-start lags during peak hours (evenings/weekends).

### Architecture Transition
- **Frontend Hosting:** Keep on Vercel (Upgrade to Pro if bandwidth exceeds free limits).
- **Backend Hosting:** Move to a dedicated VPS (DigitalOcean Droplet or AWS EC2 `t3.micro`). Cost: ~$5 - $10/month.
- **Database:** Migrate from Supabase free tier to managed DigitalOcean Managed Database or AWS RDS. Cost: ~$15/month. Ensures automated backups and high availability.
- **Image Storage:** Move to AWS S3 + CloudFront CDN. Cost: Very cheap (pennies per GB).
- **Search Optimization:** Postgres `LIKE` queries will start to slow down. We must implement **Redis** caching for popular user feeds and consider **ElasticSearch** for complex, multi-faceted matchmaking queries.

## Phase 3: Real-Time Features (Post-10k Profiles)
- To handle real-time chat between 10,000 profiles, polling the REST API will crash the VPS.
- We must implement **WebSockets** (Spring Boot WebSockets + Redis Pub/Sub for horizontal scaling) or use a managed service like **Pusher**.
