# 🗄️ Database Setup Guide

## Quick Setup Options

### ⚡ Recommended: Supabase (Easiest & Free)

1. **Create Account**:
   - Go to https://supabase.com
   - Sign up with GitHub (fastest)

2. **Create Project**:
   - Click "New Project"
   - Name: `mandarinmind`
   - Database Password: Choose a strong password (save it!)
   - Region: Choose closest to you
   - Wait 2-3 minutes for provisioning

3. **Get Connection String**:
   - Go to Project Settings (gear icon) → Database
   - Scroll down to "Connection string"
   - Select "URI" tab
   - Copy the connection string
   - Replace `[YOUR-PASSWORD]` with your actual password
   - Add `?schema=public` at the end

4. **Update .env**:
   ```env
   DATABASE_URL="postgresql://postgres.xxxxx:[YOUR-PASSWORD]@aws-0-us-east-1.pooler.supabase.com:6543/postgres?schema=public"
   ```

5. **Run Migration**:
   ```bash
   npx prisma migrate dev --name init
   ```

---

### 🚂 Alternative: Railway

1. Go to https://railway.app
2. Sign in with GitHub
3. Click "New Project" → "Provision PostgreSQL"
4. Click on PostgreSQL service
5. Go to "Variables" tab
6. Copy the `DATABASE_URL` value
7. Paste it into your `.env` file
8. Add `?schema=public` at the end if not present

---

### 💻 Local PostgreSQL (If you prefer local development)

#### Windows:
1. Download PostgreSQL from https://www.postgresql.org/download/windows/
2. Install with default settings (remember the password you set!)
3. Default credentials:
   - Username: `postgres`
   - Password: (what you set during installation)
   - Port: `5432`

4. Update `.env`:
   ```env
   DATABASE_URL="postgresql://postgres:yourpassword@localhost:5432/mandarinmind?schema=public"
   ```

5. Create database (optional, Prisma will do it):
   ```bash
   # Open psql
   psql -U postgres
   
   # Create database
   CREATE DATABASE mandarinmind;
   
   # Exit
   \q
   ```

---

## After Setting Up Database

Once you have your `DATABASE_URL` configured:

```bash
# 1. Generate Prisma Client
npx prisma generate

# 2. Create database tables
npx prisma migrate dev --name init

# 3. (Optional) Open Prisma Studio to view your database
npx prisma studio

# 4. Start the NestJS server
npm run start:dev
```

You should see:
```
🚀 MandarinMind Backend is running on: http://localhost:3000/api
```

---

## Troubleshooting

### Error: "Can't reach database server"
- Check your internet connection (for cloud databases)
- Verify DATABASE_URL is correct
- Check if PostgreSQL is running (for local)

### Error: "Authentication failed"
- Double-check your password in DATABASE_URL
- Make sure there are no special characters that need encoding

### Error: "Database does not exist"
- Prisma will create it automatically during migration
- Or create it manually with `CREATE DATABASE mandarinmind;`

---

## Next Steps After Database Setup

1. ✅ Run migrations: `npx prisma migrate dev --name init`
2. ✅ Start server: `npm run start:dev`
3. ✅ Create seed data (coming soon)
4. ✅ Start building Auth module

---

**Need help?** Check `.env` file for more database options!
