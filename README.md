# # Drapely

**Discover and compare clothes from 10+ fashion brands in one place.**

Drapely is a web-based multi-brand fashion aggregation platform. Instead of opening a separate website for every brand, users can browse, search, filter and compare clothing from several brands on one site, save favourites to a wishlist, get recommendations based on their preferences and size, and preview how an outfit might look on them using an AI virtual try-on.

Drapely is an aggregator, not a marketplace. When a user decides to buy, they are redirected to the original brand's website. Payments, delivery and order fulfilment stay with the brand.

> **Course:** Software Construction Lab (SEL-311), BSE-5 (Morning)
> **Instructor:** Engr. Saad Mazhar Khan
> **Department of Software Engineering, Bahria University, H-11 Campus, Islamabad**

---

## Project Status

🚧 **In development.** This is the initial project skeleton. Features are listed below as planned and will be marked done as they are built. See [`PROGRESS_LOG.md`](PROGRESS_LOG.md) for weekly progress.

---

## The Problem

Shoppers who buy clothes online have to visit many brand websites to compare products, prices, sizes and styles. Sizes differ from brand to brand, and there is no easy way to see how an item will look before buying it. This makes online clothes shopping slow and confusing.

## Objectives

1. Build a central platform for discovering clothing from multiple fashion brands.
2. Provide efficient search and filtering of clothing products.
3. Let users compare products and prices across brands.
4. Provide personalised clothing recommendations.
5. Integrate an AI-powered virtual try-on feature.
6. Provide brand-specific size information so users choose the right size.
7. Build secure user authentication and account management.
8. Apply software construction concepts: object-oriented design, database design, testing and version control.

---

## Planned Features

| # | Feature | Description | Status |
|---|---------|-------------|--------|
| 1 | Registration and login | Sign up, log in and manage an account, with JWT authentication | ⬜ Planned |
| 2 | User roles | **Customer** and **Administrator**, each with their own permissions | ⬜ Planned |
| 3 | Multi-brand catalogue | Products from supported brands via permitted APIs or product feeds, with a sample catalogue where no integration is available | ⬜ Planned |
| 4 | Search and filtering | Filter by brand, gender, category, size, price range, colour, season and occasion | ⬜ Planned |
| 5 | Product comparison | Compare products from different brands by price, category, available sizes and details | ⬜ Planned |
| 6 | Wishlist | Save favourite products and view them later | ⬜ Planned |
| 7 | Recommendations | Suggestions based on the user's preferences, categories, budget and season | ⬜ Planned |
| 8 | Brand size charts | Brand-specific size information to help users pick the right size | ⬜ Planned |
| 9 | AI virtual try-on | Upload a photo, pick an item and generate a preview through an external try-on API | ⬜ Planned |
| 10 | Brand redirection | Link to the original brand's product page to complete the purchase | ⬜ Planned |
| 11 | Admin management | Manage brand connections, review product data and fix catalogue sync or classification issues | ⬜ Planned |

**Real-time / dynamic behaviour:** product availability, prices and sizes update when brand catalogues are synchronised, and try-on sessions show a live status (processing → ready / failed).

---

## Technology Stack

| Layer | Technology |
|-------|------------|
| Language | JavaScript |
| Front end | React.js |
| Styling | Tailwind CSS |
| Back end | Node.js, Express.js |
| Database | PostgreSQL |
| Authentication | JSON Web Tokens (JWT) |
| AI virtual try-on | FASHN AI API (or a similar service) |
| Version control | Git and GitHub |
| Development environment | Visual Studio Code |

---

## Project Structure

```
drapely/
├── client/              # React front end (pages, components, styles)
├── server/              # Node.js + Express back end (models, services, controllers, routes)
├── database/            # PostgreSQL schema and seed scripts
├── docs/                # SRS, SDS, prototypes and diagrams
│   └── screenshots/     # Screenshots of the running website
├── .env.example         # Template for environment variables (no real secrets)
├── .gitignore
├── PROGRESS_LOG.md      # Weekly progress record
└── README.md
```

---

## Object-Oriented Design (Planned)

The back end is organised into separate layers: **models**, **services** (business rules), **controllers** and **routes**, so each class has one responsibility and layers depend on each other as little as possible.

Planned classes:

- `User` (parent class), with subclasses `Customer` and `Administrator`
- `Brand`, `Product`, `Category`, `SizeChart`
- `Wishlist`, `Recommendation`, `TryOnSession`

**Inheritance and polymorphism:** `Customer` and `Administrator` extend `User` and override shared methods (for example, the permissions each role has), which are then called through the `User` type.

---

## Database Design (Planned)

PostgreSQL, with related tables linked through primary and foreign keys:

| Table | Purpose |
|-------|---------|
| `users` | Account details and role |
| `brands` | Supported fashion brands |
| `products` | Clothing items from each brand |
| `categories` | Clothing categories |
| `sizes` | Available sizes per product |
| `size_charts` | Brand-specific size measurements |
| `wishlists` | Products saved by users |
| `user_preferences` | Preferred styles, sizes, budget and season |
| `try_on_sessions` | Virtual try-on requests and results |
| `product_images` | Product image links |

The full ER diagram will be in the SDS under `docs/`.

---

## Getting Started

> These steps will be finalised as the code is added.

### Prerequisites

- [Node.js](https://nodejs.org/) (LTS version) and npm
- [PostgreSQL](https://www.postgresql.org/)
- Git

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/drapely.git
cd drapely
```

### 2. Set up the database

```bash
# Create the database
createdb drapely

# Create the tables and load sample data
psql -d drapely -f database/schema.sql
psql -d drapely -f database/seed.sql
```

### 3. Configure environment variables

Copy the template and fill in your own values. **Never commit the real `.env` file.**

```bash
cp .env.example server/.env
```

### 4. Run the back end

```bash
cd server
npm install
npm run dev
```

### 5. Run the front end

```bash
cd client
npm install
npm run dev
```

---

## Testing

Planned: a test table of at least 15 cases (including invalid input, wrong login and rule violations), a bug log of real faults with the commits that fixed them, and automated tests. These will be documented in the project report.

---

## Screenshots

Screenshots of the running website will be added to `docs/screenshots/` as features are completed.

---

## Team Members

| Name | Roll Number |
|------|-------------|
| Muhammad Umer Abid | 09-131242-069 |
| Hasan Shakeel | 09-131242-029 |

---

## Project Scope

- Drapely focuses on fashion discovery and product aggregation. It does **not** handle payments, inventory, shipping or order fulfilment.
- The first version supports a limited number of brands to keep the project manageable.
- Where a brand has no accessible API or product feed, sample product data is used for demonstration.
- The virtual try-on feature depends on the availability of an external AI service.
