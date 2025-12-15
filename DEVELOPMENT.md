# MandarinMind Backend - Project Structure & Next Steps

## ✅ What's Been Set Up

### 1. Core Framework
- ✅ NestJS installed and configured
- ✅ TypeScript setup
- ✅ Development environment ready

### 2. Database Layer
- ✅ Prisma ORM installed
- ✅ PostgreSQL configured
- ✅ Complete database schema designed with:
  - User authentication
  - Vocabulary management (with HSK levels)
  - Spaced Repetition System (SRS)
  - Progress tracking
  - Achievements & gamification
  - Streaks
  - Failed words tracking
  - Lessons & word packs

### 3. Configuration
- ✅ Environment variables setup (.env)
- ✅ Global validation pipes
- ✅ CORS enabled
- ✅ Global API prefix (/api)
- ✅ Prisma service & module (Global)
- ✅ Config module (Global)

### 4. Dependencies Installed
- `@nestjs/config` - Environment configuration
- `@nestjs/jwt` & `@nestjs/passport` - Authentication
- `passport-jwt` - JWT strategy
- `@prisma/client` - Database ORM
- `bcrypt` - Password hashing
- `class-validator` & `class-transformer` - DTO validation

---

## 🚀 Next Steps

### Phase 1: Database & Authentication (Priority)

#### 1.1 Database Setup
```bash
# Update .env with your PostgreSQL credentials
DATABASE_URL="postgresql://username:password@localhost:5432/mandarinmind?schema=public"

# Run migration to create tables
npx prisma migrate dev --name init

# Open Prisma Studio to view database
npx prisma studio
```

#### 1.2 Auth Module
Create authentication system with:
- User registration (POST /api/auth/register)
- User login (POST /api/auth/login)
- JWT token generation
- Auth guards
- Password hashing

**Files to create:**
```
src/auth/
├── auth.module.ts
├── auth.controller.ts
├── auth.service.ts
├── strategies/
│   └── jwt.strategy.ts
├── guards/
│   └── jwt-auth.guard.ts
└── dto/
    ├── register.dto.ts
    └── login.dto.ts
```

---

### Phase 2: Core Vocabulary System

#### 2.1 Vocabulary Module
CRUD operations for vocabulary:
- GET /api/vocabulary (with filters: HSK level, difficulty)
- GET /api/vocabulary/:id
- POST /api/vocabulary (Admin only)
- PUT /api/vocabulary/:id (Admin only)
- DELETE /api/vocabulary/:id (Admin only)

**Files to create:**
```
src/vocabulary/
├── vocabulary.module.ts
├── vocabulary.controller.ts
├── vocabulary.service.ts
└── dto/
    ├── create-vocabulary.dto.ts
    ├── update-vocabulary.dto.ts
    └── query-vocabulary.dto.ts
```

#### 2.2 Seed Data
Create seed script to populate initial vocabulary:
```
prisma/
└── seed.ts  # HSK 1-3 vocabulary for testing
```

---

### Phase 3: Learning System

#### 3.1 SRS Module
Implement spaced repetition algorithm:
- Review scheduling (1 → 2 → 4 → 7 → 14 days)
- GET /api/srs/due-reviews (words due for review)
- POST /api/srs/submit-review (record answer, update intervals)
- SRS algorithm with ease factor

**Files to create:**
```
src/srs/
├── srs.module.ts
├── srs.controller.ts
├── srs.service.ts
├── srs-algorithm.service.ts  # Pure SRS logic
└── dto/
    └── submit-review.dto.ts
```

#### 3.2 Quiz Module
Generate quizzes and track results:
- POST /api/quiz/generate (create quiz session)
- POST /api/quiz/submit-answer
- GET /api/quiz/results/:sessionId
- Track failed words automatically

**Files to create:**
```
src/quiz/
├── quiz.module.ts
├── quiz.controller.ts
├── quiz.service.ts
└── dto/
    ├── generate-quiz.dto.ts
    └── submit-answer.dto.ts
```

---

### Phase 4: Progress & Gamification

#### 4.1 Progress Module
Track user learning progress:
- GET /api/progress (user stats)
- XP calculation
- Level-up logic
- Streak management (48-hour leniency)

**Files to create:**
```
src/progress/
├── progress.module.ts
├── progress.controller.ts
├── progress.service.ts
└── streak.service.ts
```

#### 4.2 Achievements Module
Badge system:
- GET /api/achievements (all available)
- GET /api/achievements/user (user's unlocked)
- Auto-unlock based on milestones

**Files to create:**
```
src/achievements/
├── achievements.module.ts
├── achievements.controller.ts
├── achievements.service.ts
└── achievement-triggers.service.ts
```

---

### Phase 5: Content Organization

#### 5.1 Lessons Module
Structured learning paths:
- GET /api/lessons (all lessons)
- GET /api/lessons/:id
- GET /api/word-packs (HSK packs, themes)

**Files to create:**
```
src/lessons/
├── lessons.module.ts
├── lessons.controller.ts
└── lessons.service.ts
```

---

### Phase 6: Audio Integration

#### 6.1 Audio Module
TTS integration:
- POST /api/audio/generate (generate TTS audio)
- Integration with Google TTS or Azure TTS
- Cache audio files

**Files to create:**
```
src/audio/
├── audio.module.ts
├── audio.controller.ts
├── audio.service.ts
└── tts.service.ts
```

---

### Phase 7: Admin Features

#### 7.1 Admin Module
Content management:
- Bulk vocabulary upload
- Content moderation
- User management
- Analytics dashboard

---

## 📊 Database Migration Commands

```bash
# Create a new migration after schema changes
npx prisma migrate dev --name <migration_name>

# Apply migrations in production
npx prisma migrate deploy

# Reset database (DEV ONLY - deletes all data)
npx prisma migrate reset

# Generate Prisma Client after schema changes
npx prisma generate

# Open Prisma Studio (visual database editor)
npx prisma studio
```

---

## 🧪 Testing Strategy

1. **Unit Tests**: Service logic (SRS algorithm, XP calculation)
2. **Integration Tests**: API endpoints
3. **E2E Tests**: Complete user flows

---

## 🔒 Security Checklist

- [ ] JWT secret in environment variable
- [ ] Password hashing with bcrypt
- [ ] Rate limiting on auth endpoints
- [ ] Input validation on all DTOs
- [ ] Role-based access control (Admin routes)
- [ ] SQL injection protection (Prisma handles this)

---

## 📝 Development Workflow

1. Create feature branch
2. Implement module (service → controller → DTOs)
3. Write tests
4. Test with Postman/Insomnia
5. Commit & push
6. Merge to main

---

## 🎯 Immediate Next Steps

1. **Set up PostgreSQL database** (local or cloud)
2. **Update .env** with real database URL
3. **Run first migration**: `npx prisma migrate dev --name init`
4. **Create Auth module** (registration & login)
5. **Create seed script** with sample HSK 1 vocabulary
6. **Test authentication** with Postman

---

## 🛠️ Useful Commands

```bash
# Start development server
npm run start:dev

# Generate new module
nest g module <module-name>

# Generate new controller
nest g controller <controller-name>

# Generate new service
nest g service <service-name>

# Generate complete resource (module + controller + service + DTOs)
nest g resource <resource-name>

# Build for production
npm run build

# Run tests
npm run test
```

---

**Ready to start building! 🚀**
