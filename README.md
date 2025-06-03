# 🧠 Bitespeed Backend Task — Identity Reconciliation

This project implements the `/identify` API endpoint for Bitespeed's Identity Reconciliation task. Built with Node.js, TypeScript, Express, and Prisma.

## 🚀 Live Endpoint

> https://your-app-name.onrender.com/identify  
(Replace with your actual Render URL after deployment)

## 📦 Tech Stack

- Node.js + Express
- TypeScript
- Prisma ORM
- PostgreSQL
- Deployed on Render

## 🧪 API Usage

### Endpoint
```
POST /identify
Content-Type: application/json
```

### Request Body
```json
{
  "email": "mcfly@hillvalley.edu",
  "phoneNumber": "123456"
}
```

### Example Response
```json
{
  "contact": {
    "primaryContatctId": 1,
    "emails": ["lorraine@hillvalley.edu", "mcfly@hillvalley.edu"],
    "phoneNumbers": ["123456"],
    "secondaryContactIds": [23]
  }
}
```

## 🛠 Setup Locally

```bash
git clone https://github.com/your-username/bitespeed-backend-task
cd bitespeed-backend-task

npm install
npx prisma generate
npx prisma migrate dev --name init
npm run dev
```

Set your DB credentials in `.env`:
```
DATABASE_URL="your_postgres_connection_string"
```

## 🌐 Deploy to Render

1. Create new web service: **Render > New > Web Service**
2. Connect your GitHub repo
3. Use `npm install && npx prisma generate && npm run build` as build command
4. Use `npm start` as start command
5. Set environment variable: `DATABASE_URL`
6. Deploy!

## ✅ Submission

Submit your hosted endpoint link and GitHub repo on the [submission form](https://forms.gle/3j3KF6zJumemhMkQ9)

## 🧊 Example DB Record Format

Prisma Contact model:
```ts
model Contact {
  id             Int       @id @default(autoincrement())
  phoneNumber    String?
  email          String?
  linkedId       Int?
  linkPrecedence String    @default("primary")
  createdAt      DateTime  @default(now())
  updatedAt      DateTime  @updatedAt
  deletedAt      DateTime?
}
```