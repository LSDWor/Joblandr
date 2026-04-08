# Joblandr

## Product Overview
AI Voice Interview Coach — practice interviews with AI, get real-time feedback

## Tech Stack
- **Frontend**: Next.js 14 + TypeScript + Tailwind CSS
- **Voice AI**: LiveKit (real-time voice) + OpenAI Realtime API OR ElevenLabs Conversational AI
- **Backend**: Next.js API Routes + WebSocket server
- **Database**: PostgreSQL
- **Auth**: NextAuth.js
- **Storage**: AWS S3 (for recordings)
- **Transcription**: Whisper API
- **Hosting**: Vercel + Railway (for WebSocket)

## Core Features

### 1. AI Voice Interviews
- Industry-specific interview modes (tech, healthcare, finance, retail)
- Behavioral (STAR method) practice
- Technical coding interviews (with code editor)
- Company-specific prep (FAANG, startups, etc.)
- Difficulty levels

### 2. Real-Time Feedback
- Speech analysis (pace, filler words, clarity)
- Answer quality scoring
- Content feedback (what you said well, what you missed)
- Body language tips (if video enabled)
- Confidence scoring

### 3. Practice Modes
- Quick 5-minute practice
- Full 30-minute mock interview
- Custom question sets
- Flashcard mode for common questions
- Record & review mode

### 4. Progress Tracking
- Interview history
- Improvement over time graphs
- Strength/weakness analysis
- Personalized tips
- Benchmark vs other users

### 5. Job-Specific Prep
- Paste job description → AI tailors questions
- Company research integration (Glassdoor, Levels.fyi)
- Salary negotiation practice

## Database Schema

```sql
-- Users
users: id, email, name, target_industry, experience_level, created_at

-- Interviews
interviews: id, user_id, type, company, role, duration, recording_url, transcript, score, created_at

-- Responses
responses: id, interview_id, question, user_answer, ai_feedback, score, created_at

-- Questions Library
questions: id, category, difficulty, industry, content, ideal_answer_outline

-- User Stats
user_stats: id, user_id, total_interviews, avg_score, strengths, weaknesses, last_practiced

-- Job Descriptions
job_descriptions: id, user_id, company, role, description_text, parsed_skills, created_at
```

## API Endpoints

```
POST   /api/interviews/start
POST   /api/interviews/:id/response
GET    /api/interviews/:id/feedback
GET    /api/questions?industry=X&difficulty=Y
POST   /api/jobs/analyze
GET    /api/stats
WS     /ws/interview (WebSocket for real-time)
```

## MVP Milestones

### Phase 1: Voice Core (Week 1-2)
- [ ] LiveKit + OpenAI integration
- [ ] Basic interview flow
- [ ] Transcription storage
- [ ] Simple feedback display

### Phase 2: Feedback System (Week 3-4)
- [ ] Speech analysis (pace, fillers)
- [ ] Answer scoring
- [ ] Improvement suggestions
- [ ] Interview history

### Phase 3: Content Library (Week 5)
- [ ] Question bank by industry
- [ ] Company-specific modes
- [ ] Difficulty levels
- [ ] Custom question sets

### Phase 4: Growth (Week 6)
- [ ] Job description parser
- [ ] Progress analytics
- [ ] Leaderboard
- [ ] Sharing results

## Pricing Tiers
- **Free**: 3 interviews/mo, basic feedback
- **Pro**: $19/mo — Unlimited interviews, all industries, detailed analytics
- **Premium**: $49/mo — Job description analysis, 1-on-1 AI coaching, mock negotiation

## Marketing Flywheel → Services
- "Your interview scores are improving — want resume optimization too?"
- "You're practicing for FAANG — let us connect you with a real coach"
- "You're interviewing well — let us optimize your LinkedIn profile"
