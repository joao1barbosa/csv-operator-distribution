# 📊 CSV Operator Distribution

> A full-stack technical challenge: bulk-register clients from a CSV upload and distribute them across operators — with CSV import/export and a per-layer tested NestJS API. TypeScript end to end.

## 📋 Overview

Solution to a full-stack technical challenge. The app lets you view operators and the
clients assigned to them, register clients in bulk by uploading a CSV (each client is
distributed to an operator on upload), and export all clients back to CSV.

- View operators and their assigned clients.
- Upload a CSV to register clients immediately, distributed across operators (round-robin).
- Export all clients to a CSV file.
- Redistribute existing clients across operators.

## 🚀 Tech Stack

| Layer | Technology |
|-------|-----------|
| **Frontend** | TypeScript, React, Next.js, React Query, React Hook Form, Zod, Tailwind, shadcn/ui |
| **Backend** | NestJS, Multer, csv-parser, fast-csv |
| **ORM / DB** | Prisma · MySQL |
| **Testing** | Jest |
| **Runtime** | Docker / Docker Compose |

## 📷 Demo

<div align="center">
  <img src="./docs/dashboard.gif" alt="Dashboard"><br/>
  <img src="./docs/upload.gif" alt="CSV upload"><br/>
  <img src="./docs/responsivite.gif" alt="Responsive layout">
</div>

Database schema:

<p align="center"><img src="./docs/db.png" alt="Database schema"></p>

## 🏗 Architecture

A NestJS API with clear layering — **controllers → services → repositories**, with DTOs,
entities, and validators per module (`clients`, `operators`) — behind a Next.js frontend.
CSV parsing is streamed; client distribution is a round-robin over the available operators.

## 🧪 Testing

Unit tests with Jest, **one spec per layer** (service, controller, validator):

```bash
cd backend && yarn test
```

## 🔧 How to Run Locally

**Prerequisites:** Docker + Docker Compose V2.

The `.env.example` ships pre-filled (this is not a production app) — just copy it to `.env`.

```bash
docker compose up --build -d
```

## 📡 API Reference

**Operators** — `POST /operators`, `GET /operators`, `GET /operators/:id`,
`PATCH /operators/:id`, `DELETE /operators/:id`.

**Clients** — `GET /clients`, `GET /clients/:id`, `POST /clients`, `PATCH /clients/:id`,
`DELETE /clients/:id`, `POST /clients/upload` (CSV, form-data `file`),
`GET /clients/download` (CSV export), `GET /clients/redistribute`.

## 👤 Author

**João Barbosa** — Software Engineer (backend / platform).
[LinkedIn](https://www.linkedin.com/in/joao1barbosa/) · [GitHub](https://github.com/joao1barbosa)
