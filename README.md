# Lobby Padel

A full-stack platform for seamless padel court booking. Built with a clean architecture split between a Next.js frontend and a NestJS backend, the system delivers efficient booking flow, role-based dashboards, and real-time availability checks.

## Table of Content

- [Project overview](#project-overview)
- [Live demo](#live-demo)
- [Repositories](#repositories)
- [Key features](#key-features)
  - [User features](#user-features)
  - [Admin features](#admin-features)
  - [System features](#system-features)
- [Tech stack](#tech-stack)
  - [Frontend](#frontend)
  - [Backend](#backend)
- [Installation](#installation)
  - [Frontend setup](#frontend-setup)
  - [Build for production](#build-for-production)
  - [Backend setup](#backend-setup)
- [API endpoints](#api-endpoints)
  - [Auth](#auth)
  - [Users](#users)
  - [Courts](#courts)
  - [Bookings](#bookings)
- [Environment variables](#environment-variables)
  - [Frontend](#frontend-env)
  - [Backend](#backend-env)
- [Database schema](#database-schema)
- [Deployment](#deployment)

## Live demo

| Description                                       | Link                                                                |
| ------------------------------------------------- | ------------------------------------------------------------------- |
| Frontend                                          | <https://final-project-fe-indra-nurfa.vercel.app>                   |
| Backend API documentation (currently unavailable) | <https://final-project-be-indranurfa-production.up.railway.app/api> |

## Repositories

| Description | Link                                                                             |
| ----------- | -------------------------------------------------------------------------------- |
| Frontend    | [Frontend Repository](https://github.com/IndraNurfa/final-project-fe-IndraNurfa) |
| Backend     | [Backend Repository](https://github.com/IndraNurfa/final-project-be-IndraNurfa)  |

## Project overview

Lobby Padel is designed to handle end-to-end padel court booking. Users can browse courts, check availability, manage bookings, and track history. Admins get a management dashboard for courts, bookings, users.

![Homepage](./homepage.png)
_Homepage - Welcome to Lobby Padel_ 

## Key features

### User features

- Registration and login with session-based auth
- Browse courts and check real-time availability
- Create, update, and cancel bookings
- View booking history and details
- Mobile-first interface

### Admin features

- Dashboard with analytics and charts
- Manage bookings with confirm and cancel actions
- Manage courts and court types
- Manage users
- Track revenue trends

### System features

- Real-time conflict prevention when creating bookings
- Role-based access control
- Dark mode support on the frontend
- Optimized API with caching and rate limiting
- Comprehensive Swagger documentation

## Tech stack

### Frontend

- React 19
- Next.js 15 (App Router, Server Components)
- TypeScript
- Tailwind CSS
- Shadcn/ui
- Axios
- NextAuth.js
- Recharts

### Backend

- NestJS
- TypeScript
- PostgreSQL
- Prisma ORM
- JWT authentication
- Swagger/OpenAPI
- Throttler (rate limiting)
- Cache manager
- Railway deployment

## Installation

### Frontend setup

1. Clone the repository

```bash
git clone https://github.com/revou-fsse-feb25/final-project-fe-IndraNurfa.git
cd final-project-fe-IndraNurfa
```

2. Install dependencies

```bash
npm install
# or
yarn install
# or
pnpm install
```

3. Environment Configuration

```bash
cp .env.example .env.local
```

Edit `.env.local` and configure the variables according to your needs:

```env
# Copy from .env.example and modify as needed
NEXTAUTH_URL=http://localhost:3000
NEXTAUTH_SECRET=your-secret-key
NEXT_PUBLIC_API_URL=your-backend-url
```

4. Run the development server

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
```

5. Open your browser
   Navigate to [http://localhost:3000](http://localhost:3000) to see the application.

### Build for Production

```bash
npm run build
npm run start
```

### Backend setup

1. Clone this repository

   ```bash
   git clone https://github.com/revou-fsse-feb25/final-project-be-IndraNurfa.git
   cd final-project-be-IndraNurfa
   ```

2. Install dependencies:

   ```bash
   pnpm install
   # or
   npm install
   ```

3. Environment Setup

   Copy `.env.example` to `.env` and configure your database and JWT settings:

   ```bash
   cp .env.example .env
   ```

4. Database Setup

   Run migrations and seed the database:

   ```bash
   npx prisma migrate dev --name init
   pnpm run seed
   ```

5. Start the application:

   ```bash
   # Development mode
   pnpm run start:dev

   # Production mode
   pnpm run start
   ```

6. Access the application:
   - API Documentation: [http://localhost:3000/api](http://localhost:8000/api)
   - Base URL: `http://localhost:8000`

## API endpoints

### Auth

- POST /auth/register

- POST /auth/login

- POST /auth/refresh

- POST /auth/logout

### Users

- GET /users/profile

- PATCH /users/profile

### Courts

- GET /courts

- GET /courts/master-court-types

- PATCH /courts/master-court-types/:id

- PATCH /courts/master-courts/:id

### Bookings

- POST /bookings

- GET /bookings/available

- GET /bookings/:uuid

- GET /bookings/admin

- GET /bookings/user

- PATCH /bookings/:uuid

- PATCH /bookings/confirm/:uuid

- PATCH /bookings/cancel/:uuid

## Environment variables

### Frontend Env

```env
NEXTAUTH_URL=http://localhost:8000
NEXTAUTH_SECRET=your-secret-key
NEXT_PUBLIC_API_URL=your-backend-url
```

### Backend Env

```env
DATABASE_URL="postgresql://username:password@localhost:5432/lobby_padel"
JWT_SECRET="your-super-secret-jwt-key"
ACCESS_TOKEN_EXP="15m"
REFRESH_TOKEN_EXP="7d"
PORT=8000
NODE_ENV="development"
```

## Database schema

The system uses PostgreSQL with Prisma. Main entities:

- Role

- User

- UserSession

- MasterCourtTypes

- MasterCourts

- Booking

- BookingDetail

- BookingHistory

ERD available in backend repo under docs/erd.png.

## Deployment

- Frontend deployed on Vercel

- Backend deployed on Railway

- Automatic builds from main branches

## License

This project is licensed under the MIT License.

<p align="right">GOD BLESS~ <br/>Indra Nurfa</p>
