---
title: "Connecting Technical Decisions to Functional Requirements"
date: "2026-05-04"
author: "Leo"
summary: "Connecting EazyCars' technical stack and database structure to its functional requirements."
tags:
  - Technical Decisions
  - Database Design
  - System Architecture
---
Write your content here.
After defining the main functional requirements for EazyCars, I needed to make sure the technical structure of the project supported those requirements. The application was not intended to be a static catalogue of cars. It needed to support searching, filtering, listing creation, image handling, enquiries, seller management, and basic compliance features. Because of this, my technical decisions were guided by the needs of the application rather than by preference alone.
The main stack I used was MojoJS, SQLite, HTMX, and TypeScript. MojoJS provided the server-side structure for handling routes and rendering pages. This was important because EazyCars has several connected user journeys, including browsing listings, viewing listing details, creating a listing, sending an enquiry, and managing listings through the garage page. A route-based structure helped separate these behaviours into more manageable parts instead of placing all logic in one file.
SQLite was suitable for the prototype because the application needed persistent relational data but did not require the complexity of a large external database server. The database structure shows that EazyCars depends on several related entities, including users, listings, listing images, enquiries, seller information, cookie consent records, and audit-related ideas. This relational structure matches the functional requirements: listings belong to sellers, enquiries belong to listings and buyers, and seller information provides basic trust indicators.
HTMX was an important technical decision for the browsing experience. Filtering car listings by make, model, year, price, and location is a core requirement, but a full page reload after every filter change would make the interface feel slower and less responsive. HTMX allowed parts of the page, such as the results list or consent banner, to update without reloading the entire page. This supported the requirement of smoother interaction while keeping the implementation simpler than building a full front-end single-page application.
TypeScript was also useful because the project contains multiple models and routes that interact with database records. Stronger typing helped make the code easier to maintain as the application grew. Since the application handles structured data such as listings, users, enquiries, and images, TypeScript made the logic more predictable and reduced the chance of accidental mismatches between the code and the expected data.
The development scripts also supported the project. The build script compiles TypeScript, while the seed script creates the database with sample users, car makes, and sample listings. This was important because the prototype needed realistic data in order to test the buyer and seller flows. Seeded data made it easier to check whether browsing, filtering, listing details, and seller management worked properly without manually creating all data every time.
A deliberate design decision was to use plain CSS rather than a large CSS framework. EazyCars required a responsive layout, accessible contrast, and clear navigation, but the visual system was not complex enough to justify adding a framework. Plain CSS gave me more control and avoided extra framework-specific classes. This also made it easier to focus on the actual functional requirements instead of spending time overriding default styles.
Overall, the technical decisions in EazyCars were closely connected to the requirements of the application. SQLite supported relational data, MojoJS supported route-based page rendering, HTMX improved interaction, and TypeScript improved maintainability. These choices helped the prototype remain realistic, functional, and manageable within the scope of the assessment.
 
Figure 8. Simplified ERD for EazyCars
┌──────────────┐
│    users     │
├──────────────┤
│ user_id PK   │
│ profile_name │
│ created_at   │
└──────┬───────┘
       │ 1
       │
       │ many
┌──────▼───────────┐
│    listings      │
├──────────────────┤
│ listing_id PK    │
│ seller_id FK     │
│ title            │
│ make             │
│ model            │
│ year             │
│ price            │
│ mileage          │
│ transmission     │
│ condition        │
│ description      │
│ location         │
│ status           │
│ created_at       │
│ updated_at       │
└──────┬───────────┘
       │ 1
       │
       │ many
┌──────▼───────────┐
│ listing_images   │
├──────────────────┤
│ image_id PK      │
│ listing_id FK    │
│ image_path       │
│ is_primary       │
│ display_order    │
└──────────────────┘

┌──────────────┐          ┌──────────────┐
│    users     │          │   listings   │
└──────┬───────┘          └──────┬───────┘
       │                         │
       │ buyer_id                │ listing_id
       │                         │
       └──────────┬──────────────┘
                  ▼
          ┌──────────────┐
          │  inquiries   │
          ├──────────────┤
          │ inquiry_id PK│
          │ listing_id FK│
          │ buyer_id FK  │
          │ message      │
          │ sent_at      │
          │ is_read      │
          └──────────────┘

┌──────────────┐
│    users     │
└──────┬───────┘
       │ 1
       │
       │ 1
┌──────▼────────────┐
│ seller_profiles   │
├───────────────────┤
│ profile_id PK     │
│ user_id FK        │
│ account_age       │
│ active_listings   │
│ first_listing_date│
│ last_active_at    │
│ verified_seller   │
└───────────────────┘
Figure explanation:
The ERD shows that EazyCars needed a relational database rather than only static page content. Listings belong to sellers, listing images belong to listings, enquiries connect buyers with listings, and seller profiles provide trust-related information. This structure directly supports the main functional requirements of browsing, selling, enquiring, and evaluating seller context.
 
Figure 9. Technical Architecture Diagram
┌──────────────────────────┐
│        Browser           │
│ HTML + CSS + HTMX        │
└────────────┬─────────────┘
             │
             │ HTTP request / HTMX request
             ▼
┌──────────────────────────┐
│      MojoJS Routes       │
│ /listings                │
│ /listings/new            │
│ /listings/:id            │
│ /listings/:id/inquiry    │
│ /garage                  │
│ /consent                 │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│      Controllers         │
│ Handle page behaviour    │
│ Render templates         │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│        Models            │
│ Users                    │
│ Listings                 │
│ Uploads                  │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│     SQLite Database      │
│ users                    │
│ listings                 │
│ inquiries                │
│ listing_images           │
│ car_makes                │
└──────────────────────────┘
Figure explanation:
This architecture diagram helped me connect the technical implementation to the functional requirements. MojoJS routes manage the user journeys, models keep database operations separate from page rendering, and SQLite stores the persistent data needed for listings, users, images, and enquiries.
 
Figure 10. Seller Listing Creation Data Flow
Seller opens "Sell Your Car"
        │
        ▼
Form collects:
- Make
- Model
- Year
- Price
- Mileage
- Transmission
- Description
- Location
- Image / Image URL
        │
        ▼
Title generated:
"Year + Make + Model"
        │
        ▼
Server validates and creates listing
        │
        ▼
Listing record saved in SQLite
        │
        ▼
Image path saved in listing_images
        │
        ▼
Seller can view listing in My Garage
Figure explanation:
This data flow shows why the sell form needed structured fields. The listing title could be generated from year, make, and model, while fields such as price, mileage, and location could support browsing and filtering. This also reduced inconsistent user input.
