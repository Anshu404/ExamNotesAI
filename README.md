# ExamNotes AI

**Author:** Anshu Kumar Mandal

**Live app:** [examnotes-ai-web.vercel.app](https://examnotes-ai-web.vercel.app)

ExamNotes AI turns course material into exam-focused notes and study resources. It includes Google sign-in, AI-powered note generation, downloadable PDFs, and credit-based plans.

## Features

- Google sign-in with Firebase Authentication
- AI-generated exam and project notes
- Charts and diagrams for study material
- PDF downloads
- Credit balance and Stripe checkout
- Note history

## Tech stack

- React, Vite, Redux Toolkit, Tailwind CSS
- Express, Node.js, MongoDB, Mongoose
- Firebase Authentication
- Gemini API
- Stripe
- Vercel

## Run locally

Install dependencies in both apps:

```bash
cd server && npm install
cd ../client && npm install
```

Create `server/.env` with the backend settings:

```dotenv
PORT=8000
CLIENT_URL=http://localhost:5173
MONGODB_URL=<your MongoDB connection string>
JWT_SECRET=<a long random secret>
GEMINI_API_KEY=<your Gemini API key>
STRIPE_SECRET_KEY=<your Stripe secret key>
STRIPE_WEBHOOK_SECRET=<your Stripe webhook signing secret>
```

Create `client/.env.local`:

```dotenv
VITE_FIREBASE_APIKEY=<your Firebase web API key>
```

Start the backend and frontend in separate terminals:

```bash
cd server && npm run dev
```

```bash
cd client && npm run dev
```

The frontend runs at `http://localhost:5173` and expects the local backend at `http://localhost:8000`.

## Deploy on Vercel

The frontend and API are separate Vercel projects. Set each project's root directory to `client` or `server`, respectively. Add the environment variables above in the backend project's Production environment, and add `VITE_FIREBASE_APIKEY` in the frontend project's Production environment. Never commit actual environment values.

The Stripe webhook endpoint is:

```text
https://examnotes-ai-api.vercel.app/api/credits/webhook
```

Configure the webhook signing secret in the backend as `STRIPE_WEBHOOK_SECRET`.
