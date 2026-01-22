---
name: shopify-remix-template
description: Guide for developing Shopify apps using the official Shopify Remix Template. Covers structure, authentication, API usage, and deployment.
---

# Shopify Remix Template Guide

This skill provides a guide for building Shopify apps using the official **Shopify Remix App Template**. This template is the recommended starting point for most new Shopify embedded apps (though React Router is the future direction, Remix is still widely used and supported).

## 🚀 Getting Started

To create a new app using the Remix template, run:

```bash
npm init @shopify/app@latest
# Select "Start with Remix" when prompted.
```

## 📂 Project Structure

A typical Remix app structure:

*   `app/`
    *   `routes/`: File-system based routing.
        *   `app._index.tsx`: The main dashboard page.
        *   `app.tsx`: The root layout for the authenticated app.
        *   `webhooks.tsx`: Webhook handler.
    *   `shopify.server.ts`: **Critical**. Initializes the Shopify API client, authentication, and session storage.
    *   `db.server.ts`: Database connection (Prisma by default).
    *   `root.tsx`: The root component for the entire application.
*   `prisma/`: Database schema (`schema.prisma`) and migrations.
*   `shopify.app.toml`: Main app configuration file.

## 🔐 Authentication & Sessions

The template uses `@shopify/shopify-app-remix` to handle authentication automatically.

### `shopify.server.ts`
This file exports an `authenticate` object used in loaders and actions.

```typescript
import { shopifyApp } from "@shopify/shopify-app-remix/server";
// ...
const shopify = shopifyApp({
  apiKey: process.env.SHOPIFY_API_KEY,
  apiSecretKey: process.env.SHOPIFY_API_SECRET,
  appUrl: process.env.SHOPIFY_APP_URL,
  scopes: process.env.SCOPES?.split(","),
  // ...
});
export const authenticate = shopify.authenticate;
```

### Usage in Loaders (Data Fetching)
Protect routes and get the session context:

```typescript
import { json } from "@remix-run/node";
import { authenticate } from "../shopify.server";

export const loader = async ({ request }) => {
  const { admin, session } = await authenticate.admin(request);
  
  // Use admin API
  const response = await admin.graphql(`...`);
  
  return json({ data: response });
};
```

## 📡 Webhooks

Webhooks are handled in `app/routes/webhooks.tsx` (or individual route files). The template automatically registers webhooks defined in `shopify.server.ts`.

To add a webhook:
1.  Add configuration in `shopify.server.ts`.
2.  Handle the topic in the `action` of `app/routes/webhooks.tsx`.

## 🗄️ Database (Prisma)

The template defaults to **Prisma** with **SQLite** for local dev.
*   **Schema:** `prisma/schema.prisma`.
*   **Session Storage:** `PrismaSessionStorage` is used to store Shopify sessions in the database.

> **Tip:** For production, switch the Prisma provider to PostgreSQL or MySQL.

## 🎨 UI & Design (Polaris)

The template comes pre-configured with **Polaris**, Shopify's design system.
*   Wrap your pages in `<Page>` components.
*   Use `<Layout>`, `<Card>`, and other Polaris components for a native feel. 
*   App Bridge is initialized automatically in `app.tsx`.

## 🛠️ Common Tasks

### 1. Adding a Navigation Item
Update `app/routes/app.tsx`:
```typescript
<ui-nav-menu>
  <Link to="/app">Home</Link>
  <Link to="/app/settings">Settings</Link>
</ui-nav-menu>
```

### 2. Fetching Data from Shopify
Use the `admin` object from `authenticate.admin(request)` to make GraphQL calls.

### 3. Deploying
*   **Hosting:** Remix apps can be hosted on Vercel, Fly.io, Heroku, or Cloudflare.
*   **Database:** Ensure you have a persistent database (e.g., Postgres) for production.
*   **Environment Variables:** Set `SHOPIFY_API_KEY`, `SHOPIFY_API_SECRET`, `SCOPES`, `SHOPIFY_APP_URL`.

## 📚 References

*   [Shopify Remix App Template (GitHub)](https://github.com/Shopify/shopify-app-template-remix)
*   [@shopify/shopify-app-remix package](https://www.npmjs.com/package/@shopify/shopify-app-remix)
*   [Remix Documentation](https://remix.run/docs/en/main)
