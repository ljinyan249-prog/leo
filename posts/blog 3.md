---
title: "Prioritising Functional Requirements in EazyCars"
date: "2026-04-20"
author: "Leo"
summary: "Prioritising the essential requirements of EazyCars and explaining the trade-offs behind excluding complex future features."
tags:
  - Requirement Prioritisation
  - Scope Management
  - Trade-offs
---
Write your content here.
One of the most important parts of EazyCars was the buyer journey. Although the application also supports sellers, the buyer experience determines whether the platform is actually useful as a car marketplace. A buyer does not simply want to see a list of cars. They need to narrow the options, compare relevant details, judge the reliability of the seller, and contact the seller safely. For this reason, I designed the buyer flow around three main requirements: search and filtering, listing detail, and privacy-first enquiry.
The first requirement was search and filtering. Used-car listings can become difficult to browse if every vehicle is shown in the same undifferentiated list. I therefore treated filters such as make, model, year, price, and location as core functionality. These criteria reflect how buyers usually think when comparing cars: they may have a preferred brand, a maximum price, a suitable location, or an acceptable year range. In the database design, the listing data stores information such as make, model, year, price, mileage, transmission, description, location, and status. This made the filtering system technically possible because each listing has structured fields rather than relying only on unstructured text.
I also included reference data such as car makes, transmission types, conditions, and listing statuses. These support consistency in the application. For example, using a make dropdown helps avoid inconsistent spelling of car brands, while structured values for transmission and condition make the data easier to filter and display. This decision connects the user requirement to a technical decision: if buyers need reliable filtering, then the data must be stored in a predictable structure.
Another important part of the buyer flow was trust. Buying a used car can involve uncertainty, especially when the buyer does not know the seller personally. Instead of building a full rating or review system, I used simpler seller trust indicators. The system can show information such as account age and number of active listings. These indicators do not prove that a seller is completely trustworthy, but they give the buyer useful context before making contact. This was a deliberate trade-off. A review system would require moderation, fake-review prevention, and more complex user interactions. Seller profile indicators were more feasible for a prototype while still addressing the trust problem.
The enquiry system was also designed around privacy. I chose not to display seller contact details directly on the listing page. Instead, buyers send enquiries through the platform. This allows buyers to contact sellers while reducing the need to expose personal contact details publicly. The inquiry model connects each message to a listing and buyer account, which means the form only needs to collect the message content rather than unnecessary extra personal information.
A further design decision was to keep the enquiry system simple. A full message thread feature would be useful in a future version, but it would add complexity to the prototype. The essential requirement was allowing an initial enquiry, not building a complete messaging platform. By focusing on a single-message inquiry model, the prototype still supports the main buyer action while avoiding unnecessary scope expansion.
Overall, the buyer flow in EazyCars was designed to reduce uncertainty. Filtering helps buyers find relevant listings, structured listing data supports comparison, seller indicators provide basic trust signals, and the inquiry system protects contact information. These decisions show that the buyer experience was not only a visual design problem, but also a functional and data design problem.
 
Figure 5. Buyer User Flow
Start
  │
  ▼
Home Page
  │
  ├── User clicks "Browse Cars"
  │
  ▼
Browse Listings Page
  │
  ├── Apply filters:
  │     - Make
  │     - Model
  │     - Min / Max Price
  │     - Min / Max Year
  │     - Location
  │
  ▼
Updated Results List
  │
  ├── User selects a listing
  │
  ▼
Listing Detail Page
  │
  ├── View vehicle information
  ├── View images
  ├── Check seller account age
  ├── Check seller active listings
  │
  ▼
Send Enquiry
  │
  ├── Message is sent through platform
  ├── Seller contact details remain hidden
  │
  ▼
End
Figure explanation:
This user flow shows that the buyer journey is not only about browsing. The buyer needs to filter results, inspect a listing, evaluate basic seller trust information, and then send an enquiry through the platform. This helped me design the listing detail page as both an information page and an action page.
 
Figure 6. HTMX Filtering Interaction Flow
Buyer changes filter
        │
        ▼
Filter form sends request
        │
        ▼
Server receives filter values
        │
        ▼
Listings model builds SQL conditions
        │
        ▼
SQLite returns matching listings
        │
        ▼
Only listing results section updates
        │
        ▼
Page does not fully reload
Figure explanation:
This interaction flow explains why HTMX was useful for EazyCars. Filtering is a core buyer requirement, but reloading the whole page after every search would make the experience feel slower. By updating only the results section, the interface can feel more responsive while still using a server-rendered architecture.
 
Figure 7. Buyer Trust Decision Flow
Buyer views listing
        │
        ▼
Check vehicle details
        │
        ▼
Check seller trust indicators
        │
        ├── Account age
        ├── Active listings count
        └── Verified seller status / future option
        │
        ▼
Does the listing seem worth contacting?
        │
        ├── Yes → Send enquiry through platform
        └── No  → Return to search results
Figure explanation:
Seller trust indicators were not designed to guarantee safety, but to provide useful context before contact. I chose simple signals such as account age and active listings instead of a full review system because reviews would require moderation and fake-review prevention.
 
