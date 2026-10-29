# Souqora Web Platform

## Overview

Souqora Web Platform is a full-stack, enterprise-grade multi-vendor e-commerce and marketplace application built on modern web standards. The platform serves as an all-in-one digital commerce portal supporting general merchandise, consumer electronics, automotive listings, and real estate properties.

The system is designed from the ground up with native Right-to-Left (RTL) language architecture, dynamic bilingual switching (Arabic and English), role-based identity management, and high-performance server-rendered routing.

---

## Technical Stack

### Core Frameworks and Runtime
- Framework: Next.js 16 (App Router architecture with Turbopack support)
- Frontend Library: React 19
- Programming Language: TypeScript 5
- Runtime: Node.js (v20.x or higher)

### Styling and User Interface
- CSS Framework: Tailwind CSS v4
- Theme System: next-themes (Light and Dark mode support)
- Icons: Lucide React
- CSS Utilities: clsx, tailwind-merge, class-variance-authority
- URL State Management: Nuqs (Type-safe query parameter sync)

### Identity and Data Layers
- Authentication: NextAuth.js v5 (JWT sessions, credentials provider, password hashing with bcryptjs)
- Database ORM: Prisma ORM v6
- Form Validation: Zod v3
- Localization: next-intl (Full Arabic RTL and English LTR layouts)

---

## System Architecture and Directory Layout

```text
Web_Page_App/
|-- prisma/
|   |-- schema.prisma             Database definitions (User, Store, Product, Vehicle, Property, Order)
|   +-- seed.ts                   Initial seed script for categories, demo merchants, and catalogs
|-- public/                       Static assets, brand marks, and Web App manifest
|-- scripts/
|   +-- verify-integrity.ts       Data integrity and model validation script
|-- src/
|   |-- app/                      Next.js App Router root
|   |   |-- layout.tsx            Root layout (HTML structure, RTL/LTR setup, font injection, providers)
|   |   |-- page.tsx              Storefront homepage (Hero carousels, category grid, top sellers)
|   |   |-- account/              Customer profile and security preferences
|   |   |-- admin/                Administrative management console
|   |   |-- auth/                 Sign in, registration, and credential recovery
|   |   |-- cart/                 Shopping cart state review and price calculations
|   |   |-- checkout/             Delivery address selection and checkout completion
|   |   |-- compare/              Side-by-side product specification comparison
|   |   |-- favorites/            Customer wishlist and saved listings
|   |   |-- portal/               Unified portal switcher for customers, sellers, and admins
|   |   |-- product/[slug]/       Detailed product page with image galleries and reviews
|   |   |-- property/[slug]/      Real estate listing details with broker inquiry modal
|   |   |-- real-estate/          Property marketplace directory with specialized filters
|   |   |-- sell/                 Merchant application and vendor onboarding flow
|   |   |-- seller/               Seller dashboard (Orders, Products, Listings, Analytics)
|   |   |-- stores/               Directory of verified marketplace merchants
|   |   |-- vehicle/[slug]/       Automotive vehicle specifications and contact actions
|   |   +-- vehicles/             Vehicle showroom with filtering by make, year, and fuel type
|   |-- components/
|   |   |-- common/               Reusable components (ProductCard, InquiryModal, layouts)
|   |   |-- layout/               Header, Footer, Navigation, and Locale switcher
|   |   +-- providers/            React Context providers (Cart, Favorites, Auth, Theme)
|   |-- lib/
|   |   |-- auth/                 NextAuth configuration and credential handlers
|   |   |-- cart/                 Cart persistence hooks and calculation formulas
|   |   |-- data/                 Demo catalog, initial collections, and mock services
|   |   |-- db/                   Prisma client instance initialization
|   |   |-- favorites/            Wishlist context implementation
|   |   |-- i18n/                 Locale routing, messages, and direction helpers
|   |   +-- utils.ts              Currency formatting, date utilities, and class helpers
|   |-- messages/                 Bilingual dictionary definitions (ar.json, en.json)
|   |-- styles/                   Global CSS and theme variables (globals.css)
|   +-- types/                    TypeScript domain interfaces and NextAuth extensions
|-- next.config.ts                Next.js configuration file
|-- package.json                  Project manifest, scripts, and dependencies
+-- tsconfig.json                 TypeScript compiler configuration
```

---

## Functional Modules

### 1. Multi-Department Catalog
- General Products: Consumer electronics, home appliances, apparel, and perfumes.
- Automotive Showroom: Technical specifications (mileage, transmission, horsepower, fuel efficiency, engine capacity).
- Real Estate Directory: Property listings with room count, area measurements, licensing numbers, and broker communication.

### 2. Shopping and Order Fulfillment Flow
- Cart State: Client-side state managed via local storage persistence with real-time tax and delivery computation.
- Checkout Pipeline: Address verification, shipment method selection, and order reference generation.
- Order Management: Status tracking across Pending, Processing, Shipped, Delivered, and Cancelled phases.

### 3. Identity and Role-Based Access Control
- Customer Role: Browse listings, place orders, write reviews, manage personal profile.
- Merchant / Seller Role: Access dedicated Seller Dashboard, add and edit inventory, handle incoming customer orders, track revenues.
- Administrator Role: Platform-wide analytics, store approvals, listing moderation, and audit logs.

### 4. Internationalization and Directionality
- Full support for Right-to-Left (RTL) reading order for Arabic users.
- Full support for Left-to-Right (LTR) reading order for English users.
- Formatted local currency representation (SAR, USD) across all pricing nodes.

---

## Configuration and Environment Variables

Create a file named `.env` in the root of the project using the following template:

```env
# Authentication Secrets
AUTH_SECRET="your-generated-secret-key-32-chars-or-longer"
NEXTAUTH_SECRET="your-generated-secret-key-32-chars-or-longer"
NEXTAUTH_URL="http://localhost:3000"

# Application Metadata
NEXT_PUBLIC_APP_URL="http://localhost:3000"
NEXT_PUBLIC_APP_NAME="Souqora"
NEXT_PUBLIC_APP_NAME_EN="SOUQORA"
NEXT_PUBLIC_DEFAULT_LOCALE="ar"
NEXT_PUBLIC_DEFAULT_CURRENCY="SAR"

# Database Connection (Optional if using default SQLite)
# DATABASE_URL="file:./dev.db"
```

---

## Installation and Setup

### Prerequisites
- Node.js (version 20.x or higher)
- npm, pnpm, or yarn package manager

### Steps

1. Clone or copy the repository files:
   ```bash
   git clone https://github.com/AhmedAlheimiary/souqora-web.git
   cd souqora-web
   ```

2. Install node dependencies:
   ```bash
   npm install
   ```

3. Generate Prisma client bindings:
   ```bash
   npm run db:generate
   ```

4. Push schema migrations to the local database:
   ```bash
   npm run db:push
   ```

5. (Optional) Populate database with demo catalog data:
   ```bash
   npm run db:seed
   ```

---

## Development and Build Scripts

### Running Local Development Server
Execute the Next.js development server with Turbopack:

```bash
npm run dev
```

Navigate to `http://localhost:3000` in your web browser.

### Type Verification
Run TypeScript type-checking across all components and API routes:

```bash
npm run typecheck
```

### Production Build and Execution
Compile the project for production deployment:

```bash
npm run build
```

Start the compiled production server:

```bash
npm run start
```

### Data Integrity Verification
Run the built-in integrity validator:

```bash
npm run test:integrity
```

---

## License

This software is maintained by the Souqora development team. All rights reserved.
