---
title: ”Interpreting the Brief: Why EazyCars Needed More Than a Listing Page“
date: ”2026-04-14“
author: ”Leo“
summary: “Defining EazyCars as a used-car community platform focused on buyer needs, seller privacy, trust, and functional scope”

tags:
  - Functional Requirements
  - Project Scope
  -  User Needs
---
Write your content here.
When I first interpreted the brief for my web application prototype, I wanted to avoid building a generic website that simply displayed items on a page. I decided to develop EazyCars, a used-car community hub where sellers can list vehicles and buyers can browse, filter, and send enquiries through the platform. The main reason for choosing this idea was that used-car marketplaces involve more than just showing products. Buyers often need to compare many listings, judge whether a seller appears trustworthy, and contact the seller without immediately exposing personal information.
The core problem I identified was uncertainty. A buyer may know their preferred make, model, year, price range, or location, but still struggle to find relevant cars quickly. They may also be unsure whether a listing or seller is reliable. Because of this, I treated browsing and filtering as essential requirements rather than optional interface features. The application needed to let users narrow listings by practical criteria such as make, model, year, price, and location. Without these filters, the site would become a passive catalogue rather than a useful decision-making tool.
Another important requirement was the enquiry system. Instead of displaying the seller’s contact details directly, EazyCars allows buyers to send enquiries through the platform. This decision changed the role of the application from a simple advertising board into a controlled communication layer between buyers and sellers. It also supports privacy because sellers do not need to expose personal contact details on every listing. This requirement influenced the structure of the listing detail page: it needed to show vehicle information, but also provide a safe path for buyers to ask questions.
I also considered the seller’s needs. If users can sell cars, they need a clear way to create listings and manage them afterwards. This led to the requirement for a “Sell Car” form and a “My Garage” area. The garage page makes the seller flow more complete because it gives sellers a place to review and manage their active listings. I also decided that listing titles could be generated from the year, make, and model entered in the form. This reduces unnecessary manual input and helps keep listing titles consistent across the site.
A key trade-off was deciding what not to include. Features such as payments, live chat, seller reviews, saved searches, or recommendation algorithms could make the platform more advanced, but they would also increase the complexity beyond the scope of this prototype. Instead, I focused on the minimum set of features needed for the main buyer and seller journeys: browse, filter, view details, enquire, list a car, and manage listings.
Overall, the brief pushed me to think about EazyCars as a functional system rather than a collection of pages. The most important requirement was not simply that the website looked complete, but that each feature supported a clear user need. By focusing on search, enquiries, seller trust indicators, and listing management, I could build a prototype that addressed the main problems of a used-car community platform while still remaining feasible within the technical limits of the assignment.
 
Figure 1. Initial Sitemap for EazyCars
EazyCars Home
│
├── Browse Cars
│   │
│   ├── Filter Listings
│   │   ├── Make
│   │   ├── Model
│   │   ├── Year Range
│   │   ├── Price Range
│   │   └── Location
│   │
│   └── Listing Detail
│       │
│       ├── Vehicle Information
│       ├── Listing Images
│       ├── Seller Trust Information
│       └── Send Enquiry
│
├── Sell Your Car
│   │
│   ├── Enter Vehicle Details
│   ├── Add Description
│   ├── Add Image / Image URL
│   └── Submit Listing
│
├── My Garage
│   │
│   ├── View My Listings
│   ├── View Inquiries
│   └── Delete / Manage Listing
│
├── Login / Logout
│
└── Privacy / Cookie Consent
Figure explanation:
This sitemap helped me define the scope of EazyCars. Instead of treating the prototype as a single listing page, I planned it around two main user journeys: buyers browsing and enquiring about cars, and sellers creating and managing their own listings. This structure also helped me identify which pages were essential and which could remain future improvements.
 
Figure 2. Stakeholder Map
                  ┌──────────────────────┐
                  │      EazyCars        │
                  │ Used Car Community   │
                  └──────────┬───────────┘
                             │
        ┌────────────────────┼────────────────────┐
        │                    │                    │
┌───────▼────────┐   ┌───────▼────────┐   ┌───────▼────────┐
│     Buyer      │   │     Seller     │   │   Platform     │
│                │   │                │   │ / BlaBla Corp  │
├────────────────┤   ├────────────────┤   ├────────────────┤
│ Find cars      │   │ Create listing │   │ Protect data   │
│ Compare price  │   │ Add details    │   │ Manage consent │
│ Check seller   │   │ Receive inquiry│   │ Support access │
│ Send inquiry   │   │ Manage garage  │   │ Maintain trust │
└────────────────┘   └────────────────┘   └────────────────┘
Figure explanation:
The stakeholder map shows that the application needed to support more than one type of user. Buyers needed search, comparison, trust signals, and a safe enquiry path. Sellers needed listing creation and management. The platform also had responsibilities around privacy, consent, and accessibility.
