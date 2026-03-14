# CareConnect SG — AI Dementia Support Platform

## Overview
An AI-powered dementia support platform for Singapore families with three integrated modules:

1. **CogniScreen** — Multilingual cognitive screening with AI-driven Alzheimer's risk scoring
2. **CareConnect** — AI resource finder chatbot + smart family care coordination
3. **SafeHome** — Smart HDB safety monitor with sensor simulation and AI alert analysis

## Architecture

### Backend (Express + TypeScript)
- `server/index.ts` — Entry point; registers routes, seeds DB
- `server/routes.ts` — All API routes + AI endpoints + seed data
- `server/storage.ts` — Database storage interface (IStorage)
- `server/db.ts` — Drizzle ORM connection

### Frontend (React + Vite)
- `client/src/pages/dashboard.tsx` — Overview of all modules
- `client/src/pages/cogni-screen.tsx` — 4-step screening wizard with SSE AI chat
- `client/src/pages/resource-finder.tsx` — AI chatbot for Singapore caregiver resources
- `client/src/pages/care-coordination.tsx` — Task management + AI workload suggestions
- `client/src/pages/safety-monitor.tsx` — Sensor simulation + AI alert analysis
- `client/src/components/app-sidebar.tsx` — Navigation sidebar
- `client/src/components/page-header.tsx` — Reusable page header
- `client/src/components/circular-progress.tsx` — SVG-based risk score display

### Shared
- `shared/schema.ts` — All Drizzle table definitions + Zod insert schemas
- `shared/routes.ts` — Typed API route definitions used by both frontend and backend
- `shared/models/chat.ts` — Generic conversation/message tables

## Database Tables
- `cognitive_assessments` — Saved screening results with risk scores
- `resource_conversations` + `resource_messages` — AI chatbot history
- `family_members` — Care team members with load tracking
- `care_tasks` — Care task assignments with status/priority
- `home_sensors` — IoT sensor definitions
- `safety_alerts` — AI-analyzed safety events
- `conversations` + `messages` — Generic AI chat tables

## AI Features
- **Cognitive Screening Chat**: SSE streaming, multilingual (EN/CN/MS/TA), gpt-5.2
- **Risk Score Algorithm**: Weighted scoring from Kaggle Alzheimer's dataset features (age, family history, symptoms, MMSE, lifestyle)
- **Resource Finder**: SSE streaming chatbot with Singapore-specific resources (AIC, Dementia Singapore, subsidies)
- **Task Redistribution**: AI suggestions for fair workload distribution among family members
- **Alert Analysis**: One-sentence AI caregiver recommendations per safety event

## Key Technologies
- **Backend**: Express, Drizzle ORM, PostgreSQL, OpenAI (via Replit AI Integrations)
- **Frontend**: React, Vite, Tailwind CSS v3, shadcn/ui, TanStack Query, Framer Motion, Recharts
- **AI**: Uses `AI_INTEGRATIONS_OPENAI_API_KEY` + `AI_INTEGRATIONS_OPENAI_BASE_URL` env vars

## Design System
- Theme: Calming medical teal/slate (primary: `173 80% 36%`)
- Typography: Plus Jakarta Sans (body), Outfit (headings)
- Custom CSS variables in `client/src/index.css`
- Tailwind v3 with shadcn components

## Running the App
The "Start application" workflow runs `npm run dev` which starts both the Express API and Vite dev server on port 5000.
