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
After deciding to build EazyCars as a used-car community hub, the next challenge was deciding which requirements were essential for the prototype and which features should remain outside the project scope. A used-car platform can quickly become very large because it could include payments, reviews, live chat, saved searches, recommendation systems, vehicle history reports, and many other advanced features. However, the purpose of this prototype was not to build a complete commercial marketplace. It was to identify the core functions needed for buyers and sellers to complete the main interaction in a usable and responsible way.
The first essential requirement was browsing and filtering listings. For a used-car platform, simply showing all available cars would not be enough. Buyers usually search based on practical criteria such as make, model, year, price, and location. These filters were prioritised because they directly support the buyer’s decision-making process. If users cannot narrow down the listings, the application becomes difficult to use as the number of cars increases. For this reason, filtering was treated as part of the application’s core functionality rather than a visual enhancement.
The second essential requirement was allowing sellers to create listings. A marketplace cannot function unless sellers can add cars in a structured way. The “Sell Car” form needed to collect enough information to make each listing useful, including vehicle details and photos. I also decided that the listing title should be generated automatically from the year, make, and model. This reduces the amount of manual input required from the seller and keeps listing titles consistent across the website. This decision shows how a small functional requirement can also improve the quality and consistency of the data.
The third essential requirement was the enquiry system. I did not want the platform to display seller contact details directly because this would reduce privacy and make the website feel more like a public noticeboard than a managed platform. Instead, buyers send enquiries through the website. This requirement shaped the listing detail page because the page needed to support not only viewing car information, but also initiating safe communication.
I also identified several supporting requirements. Seller trust indicators, such as account age and number of active listings, were added to help buyers make more informed decisions. These indicators do not guarantee that a seller is trustworthy, but they provide useful context without requiring a complex review system. The “My Garage” page was another supporting requirement because sellers need a place to view and manage their own listings after posting them.
Some features were deliberately left out of scope. I did not prioritise payment processing, live chat, public reviews, or recommendation algorithms. These features could improve a future version of EazyCars, but they would also introduce additional technical, ethical, and moderation challenges. For example, reviews would require fake-review prevention and moderation, while payments would involve security and legal responsibilities beyond the scope of this prototype.
Overall, prioritising requirements helped keep EazyCars realistic and focused. The final scope was based on the minimum set of features required for the main buyer and seller journeys: browse, filter, view details, enquire, create a listing, and manage listings. This approach allowed the prototype to demonstrate clear functional thinking while avoiding unnecessary complexity.
 
Figure 3. Functional Requirements Priority Matrix
┌──────────────────────────────┬──────────────┬────────────────────────────────────┐
│ Requirement                  │ Priority     │ Reason                             │
├──────────────────────────────┼──────────────┼────────────────────────────────────┤
│ Browse car listings          │ Essential    │ Buyers need to view available cars │
│ Filter by make/model/year    │ Essential    │ Helps buyers narrow choices        │
│ Filter by price/location     │ Essential    │ Matches real car-search behaviour  │
│ View listing detail          │ Essential    │ Buyers need complete car info      │
│ Send enquiry                 │ Essential    │ Enables buyer-seller interaction   │
│ Create car listing           │ Essential    │ Sellers must be able to add cars   │
│ My Garage                    │ Supporting   │ Helps sellers manage listings      │
│ Seller trust information     │ Supporting   │ Gives buyers more confidence       │
│ Image support                │ Supporting   │ Makes listings more informative    │
│ Cookie consent banner        │ Compliance   │ Supports responsible web design    │
│ Mobile navigation            │ Compliance   │ Supports responsive usability      │
│ Payment processing           │ Future       │ Too complex for this prototype     │
│ Reviews / ratings            │ Future       │ Requires moderation and trust rules│
│ Live chat                    │ Future       │ Expands scope beyond core inquiry  │
│ Recommendation algorithm     │ Future       │ Requires more data and complexity  │
└──────────────────────────────┴──────────────┴────────────────────────────────────┘
Figure explanation:
This matrix helped me separate essential requirements from supporting and future features. The core prototype needed to support the main buyer and seller journeys first. Features such as payments, reviews, and recommendations were useful ideas, but they would introduce complexity that was not necessary for demonstrating the core application.
 
Figure 4. Scope Decision Table
┌──────────────────────┬──────────────┬──────────────────────────────────────────┐
│ Feature Idea         │ Decision     │ Reason                                   │
├──────────────────────┼──────────────┼──────────────────────────────────────────┤
│ Basic search/filter  │ Included     │ Essential for buyer decision-making      │
│ Listing detail page  │ Included     │ Needed before buyers can enquire         │
│ Inquiry form         │ Included     │ Enables contact without exposing details │
│ Seller trust signals │ Included     │ Simple way to support buyer confidence   │
│ My Garage            │ Included     │ Completes the seller management flow     │
│ Message threads      │ Deferred     │ Useful, but too close to full chat system│
│ Reviews/ratings      │ Deferred     │ Requires moderation and fake review logic│
│ Payment system       │ Excluded     │ Security/legal complexity too high       │
│ Market price trends  │ Excluded     │ Requires external data source            │
│ Local file upload    │ Workaround   │ URL image support used due to save issue │
└──────────────────────┴──────────────┴──────────────────────────────────────────┘
Figure explanation:
The scope decision table shows that the prototype was intentionally limited. I prioritised features that were directly needed for the buyer and seller journeys, while deferring features that would require moderation, payment security, external data, or a much larger messaging system.
