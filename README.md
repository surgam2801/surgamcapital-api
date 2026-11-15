# Surgam Capital API

Backend API service for Surgam Capital, built with Express, tRPC, and Drizzle ORM.

## Features
- End-to-end typesafe API procedures with tRPC v11
- Express HTTP middleware, secure cookies, and CORS support
- JWT session management
- System, notification, and financial routers

## Getting Started

### 1. Install dependencies
```bash
pnpm install # or npm install
```

### 2. Environment Variables
Create a `.env` file based on `.env.example`:
```env
PORT=3000
NODE_ENV=development
DATABASE_URL=mysql://user:password@localhost:3306/surgamcapital
```

### 3. Run development server
```bash
npm run dev
```

### 4. Build for production
```bash
npm run build
npm start
```
