# 📘 MandarinMind Backend

A full-featured Chinese learning platform backend built with **NestJS**, **Prisma**, and **PostgreSQL**.

## 🎯 Features

- 🔐 JWT Authentication
- 📚 Vocabulary management with HSK levels
- 🧠 Spaced Repetition System (SRS)
- 📊 Progress tracking & gamification
- 🏆 Achievements & badges
- 🔥 Learning streaks (48-hour leniency)
- 🎴 Flashcard & quiz system
- 🔊 Audio support (TTS integration ready)
- 📦 Word packs & lessons

## 🚀 Quick Start

### Prerequisites

- Node.js 18+ 
- PostgreSQL 14+
- npm or yarn

### Installation

```bash
# Install dependencies
npm install

# Set up environment variables
cp .env.example .env
# Edit .env and add your PostgreSQL connection string

# Generate Prisma Client
npx prisma generate

# Run database migrations
npx prisma migrate dev --name init

# Seed database (optional)
npm run seed
```

### Running the App

```bash
# Development mode with hot-reload
npm run start:dev

# Production mode
npm run start:prod
```

The API will be available at `http://localhost:3000/api`

## 📋 Database Schema

The database includes the following main entities:

- **User** - User accounts and authentication
- **Vocabulary** - Chinese words with pinyin, meanings, HSK levels
- **Review** - SRS review history and scheduling
- **FailedWord** - Track incorrect answers
- **UserProgress** - XP, levels, streaks
- **Achievement** - Badges and milestones
- **WordPack** - Organized vocabulary collections
- **Lesson** - Structured learning units

### Prisma Commands

```bash
# Generate Prisma Client
npx prisma generate

# Create migration
npx prisma migrate dev --name migration_name

# Apply migrations
npx prisma migrate deploy

# Open Prisma Studio (database GUI)
npx prisma studio

# Reset database (DEV ONLY)
npx prisma migrate reset
```

## 🏗️ Project Structure

```
src/
├── auth/           # Authentication module
├── users/          # User management
├── vocabulary/     # Vocabulary CRUD
├── srs/            # Spaced repetition logic
├── progress/       # User progress & XP
├── achievements/   # Badges & achievements
├── quiz/           # Quiz generation
├── audio/          # TTS integration
├── prisma/         # Prisma service
└── main.ts         # Application entry point
```

## 🧪 Testing

```bash
# Unit tests
npm run test

# E2E tests
npm run test:e2e

# Test coverage
npm run test:cov
```

## 📦 API Endpoints (To be implemented)

```
POST   /api/auth/register
POST   /api/auth/login
GET    /api/vocabulary
GET    /api/vocabulary/:id
POST   /api/reviews
GET    /api/progress
GET    /api/achievements
POST   /api/quiz/submit
```

## 🛠️ Tech Stack

- **NestJS** - Progressive Node.js framework
- **Prisma** - Next-generation ORM
- **PostgreSQL** - Relational database
- **JWT** - Authentication
- **TypeScript** - Type-safe development

## 📝 License

MIT

---

Built with ❤️ for Chinese language learners

$ npm run test

# e2e tests
$ npm run test:e2e

# test coverage
$ npm run test:cov
```

## Deployment

When you're ready to deploy your NestJS application to production, there are some key steps you can take to ensure it runs as efficiently as possible. Check out the [deployment documentation](https://docs.nestjs.com/deployment) for more information.

If you are looking for a cloud-based platform to deploy your NestJS application, check out [Mau](https://mau.nestjs.com), our official platform for deploying NestJS applications on AWS. Mau makes deployment straightforward and fast, requiring just a few simple steps:

```bash
$ npm install -g @nestjs/mau
$ mau deploy
```

With Mau, you can deploy your application in just a few clicks, allowing you to focus on building features rather than managing infrastructure.

## Resources

Check out a few resources that may come in handy when working with NestJS:

- Visit the [NestJS Documentation](https://docs.nestjs.com) to learn more about the framework.
- For questions and support, please visit our [Discord channel](https://discord.gg/G7Qnnhy).
- To dive deeper and get more hands-on experience, check out our official video [courses](https://courses.nestjs.com/).
- Deploy your application to AWS with the help of [NestJS Mau](https://mau.nestjs.com) in just a few clicks.
- Visualize your application graph and interact with the NestJS application in real-time using [NestJS Devtools](https://devtools.nestjs.com).
- Need help with your project (part-time to full-time)? Check out our official [enterprise support](https://enterprise.nestjs.com).
- To stay in the loop and get updates, follow us on [X](https://x.com/nestframework) and [LinkedIn](https://linkedin.com/company/nestjs).
- Looking for a job, or have a job to offer? Check out our official [Jobs board](https://jobs.nestjs.com).

## Support

Nest is an MIT-licensed open source project. It can grow thanks to the sponsors and support by the amazing backers. If you'd like to join them, please [read more here](https://docs.nestjs.com/support).

## Stay in touch

- Author - [Kamil Myśliwiec](https://twitter.com/kammysliwiec)
- Website - [https://nestjs.com](https://nestjs.com/)
- Twitter - [@nestframework](https://twitter.com/nestframework)

## License

Nest is [MIT licensed](https://github.com/nestjs/nest/blob/master/LICENSE).
