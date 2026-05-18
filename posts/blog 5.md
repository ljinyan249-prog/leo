---
title: "Evaluation, Accessibility, and Responsible Design in EazyCars"
date: "2026-05-14"
author: "Leo"
summary: "Evaluating EazyCars through usability, accessibility, privacy, compliance, and responsible design considerations."
tags:
  - Evaluation
  - Accessibility
  - Responsible Design
---
Write your content here.
After building the main buyer and seller features in EazyCars, I needed to consider how the application should be evaluated and what responsibilities come with building a used-car community platform. A car marketplace handles user-generated listings, buyer enquiries, seller information, and session-based identity, so the prototype could not only be assessed by whether the pages looked complete. It also needed to be evaluated in terms of usability, accessibility, privacy, and technical reliability.
One of my main usability goals was to make the core journeys easy to understand. For buyers, the main journey is to browse cars, apply filters, open a listing detail page, check seller information, and send an enquiry. For sellers, the journey is to create a listing and manage it later through “My Garage”. The homepage supports these journeys by presenting two clear call-to-action buttons: “Browse Cars” and “Sell Your Car”. This was important because users should not need to guess what the application is for when they first arrive. The featured listings and statistics on the homepage also help communicate that the site is an active marketplace rather than a static information page.
I also considered navigation as part of usability. The shared layout includes consistent navigation links for Buy, Sell, and My Garage across the site. This means users can move between the main sections without needing to return to the homepage. I added a mobile hamburger menu for smaller screens because the navigation would not fit comfortably on all device widths. This supports the requirement that the prototype should be usable on both desktop and mobile layouts.
Accessibility was another important evaluation area. The interface uses semantic structures such as navigation landmarks, labelled buttons, and ARIA attributes for the mobile menu and cookie banner. For example, the navigation includes an accessible label, the hamburger button uses an expanded state, and the cookie banner is presented as a dialog. These choices help make interactive elements more understandable to assistive technologies. I also considered keyboard interaction by allowing the mobile menu to close with the Escape key and returning focus to the hamburger button. These are small details, but they make the interface more responsible and easier to use.
Privacy was central to the design of EazyCars. I deliberately avoided showing seller contact details directly on listing pages. Instead, buyers send enquiries through the platform. This reduces unnecessary exposure of personal information and keeps communication inside the system. The inquiry structure supports this approach by storing messages in relation to listings and users rather than asking users to manually enter unnecessary contact details. This reflects the principle of data minimisation: the system should only collect what it needs to complete the enquiry.
Cookie consent was another responsibility I considered. The layout includes a cookie banner with accept and reject options. These buttons use HTMX to send the user’s choice without requiring a full page reload. This makes the consent interaction feel smoother while still giving users control. Although the prototype is not a production legal system, including this feature shows awareness that web applications need to consider compliance and user consent rather than treating them as afterthoughts.
For technical evaluation, I used seeded data to test the application with realistic examples. The seed script creates sample users, car makes, and listings, which makes it possible to test browsing, filtering, listing details, and seller flows without manually entering data every time. This helps evaluate whether the app still works when multiple cars exist in the database.
If I continued developing EazyCars, I would run more structured usability testing. I would ask users to complete tasks such as finding a car under a certain price, submitting an enquiry, creating a listing, and deleting a listing from My Garage. I would also test performance using browser DevTools and Lighthouse, especially on mobile or simulated slower connections. Overall, evaluation in EazyCars is not only about checking whether the code runs, but about whether the application is usable, accessible, privacy-aware, and responsible for its intended community context.
 
Figure 11. Homepage Wireframe
┌──────────────────────────────────────────────┐
│ NAV: EazyCars | Buy | Sell | My Garage | User│
├──────────────────────────────────────────────┤
│                                              │
│                 EazyCars                     │
│  Your trusted community for buying/selling   │
│                                              │
│        [ Browse Cars ]   [ Sell Your Car ]   │
│                                              │
├──────────────────────────────────────────────┤
│        Cars Listed        Featured This Week │
├──────────────────────────────────────────────┤
│              Featured Listings               │
│                                              │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐   │
│  │ Car Card │  │ Car Card │  │ Car Card │   │
│  │ Image    │  │ Image    │  │ Image    │   │
│  │ Price    │  │ Price    │  │ Price    │   │
│  │ Location │  │ Location │  │ Location │   │
│  │ [View]   │  │ [View]   │  │ [View]   │   │
│  └──────────┘  └──────────┘  └──────────┘   │
├──────────────────────────────────────────────┤
│ Why EazyCars?                                │
│ Privacy Protected | Trusted Sellers | Community│
├──────────────────────────────────────────────┤
│ Footer                                       │
└──────────────────────────────────────────────┘
Figure explanation:
The homepage wireframe shows that I wanted users to understand the purpose of the site immediately. The two main calls to action, Browse Cars and Sell Your Car, match the two main user groups. Featured listings and trust-related feature blocks support the idea that this is an active community marketplace, not just a static page.
 
Figure 12. Browse Listings Wireframe
┌──────────────────────────────────────────────┐
│ NAV: EazyCars | Buy | Sell | My Garage       │
├──────────────────────────────────────────────┤
│ Browse Used Cars                             │
│                                              │
│ Filters                                      │
│ ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐ │
│ │ Make   │ │ Model  │ │ Price  │ │ Year   │ │
│ └────────┘ └────────┘ └────────┘ └────────┘ │
│ ┌──────────────┐                             │
│ │ Location     │        [Search / Filter]    │
│ └──────────────┘                             │
├──────────────────────────────────────────────┤
│ Results                                      │
│                                              │
│ ┌──────────────────────────────────────────┐ │
│ │ Car Image | Title | Price | Location     │ │
│ │ Mileage   | Transmission | [View Details]│ │
│ └──────────────────────────────────────────┘ │
│                                              │
│ ┌──────────────────────────────────────────┐ │
│ │ Car Image | Title | Price | Location     │ │
│ │ Mileage   | Transmission | [View Details]│ │
│ └──────────────────────────────────────────┘ │
└──────────────────────────────────────────────┘
Figure explanation:
The browse page wireframe places filters above the results because filtering is the main task on this page. This supports the functional requirement that buyers should be able to narrow listings quickly instead of scrolling through all cars.
 
Figure 13. Listing Detail Page Wireframe
┌──────────────────────────────────────────────┐
│ NAV                                          │
├──────────────────────────────────────────────┤
│ Listing Title: 2020 Toyota Camry             │
│                                              │
│ ┌─────────────────────┐ ┌──────────────────┐ │
│ │ Large Car Image     │ │ Price: $22,500   │ │
│ │ / Image Gallery     │ │ Location         │ │
│ │                     │ │ Mileage          │ │
│ └─────────────────────┘ │ Transmission     │ │
│                         │ Condition        │ │
│                         └──────────────────┘ │
│                                              │
│ Vehicle Description                          │
│ ┌──────────────────────────────────────────┐ │
│ │ Seller-written description               │ │
│ └──────────────────────────────────────────┘ │
│                                              │
│ Seller Trust Information                     │
│ ┌──────────────────────────────────────────┐ │
│ │ Account age: X months                    │ │
│ │ Active listings: X                       │ │
│ └──────────────────────────────────────────┘ │
│                                              │
│ Send Enquiry                                 │
│ ┌──────────────────────────────────────────┐ │
│ │ Message textarea                         │ │
│ │ [Send Enquiry]                           │ │
│ └──────────────────────────────────────────┘ │
└──────────────────────────────────────────────┘
Figure explanation:
The listing detail wireframe combines information and action. Buyers first inspect the vehicle, then check seller trust indicators, and finally send an enquiry through the platform. This order supports a safer decision-making process.
 
Figure 14. Mobile Navigation Wireframe
Closed State:

┌────────────────────────────┐
│ EazyCars              ☰    │
└────────────────────────────┘


Open State:

┌────────────────────────────┐
│ EazyCars              ☰    │
├────────────────────────────┤
│ Buy                        │
│ Sell                       │
│ My Garage                  │
│ Logged in as TestUser      │
│ Logout                     │
└────────────────────────────┘
Figure explanation:
The mobile navigation wireframe shows how the desktop navigation collapses into a hamburger menu on smaller screens. This was important because the main routes, Buy, Sell, and My Garage, still need to be accessible on mobile devices.
 
Figure 15. Accessibility Checklist
┌──────────────────────────────┬──────────────┬──────────────────────────────┐
│ Accessibility Area           │ Status       │ Evidence / Reasoning         │
├──────────────────────────────┼──────────────┼──────────────────────────────┤
│ Semantic navigation          │ Included     │ Main nav uses navigation role │
│ Mobile menu label            │ Included     │ Hamburger has aria-label      │
│ Expanded state               │ Included     │ aria-expanded changes on open │
│ Keyboard escape support      │ Included     │ Escape closes mobile menu     │
│ Focus return                 │ Included     │ Focus returns to hamburger    │
│ Cookie banner role           │ Included     │ Banner uses dialog role       │
│ Form labels                  │ Planned/Test │ Needed for all form inputs    │
│ Colour contrast              │ Checked      │ WCAG AA target                │
│ Responsive layout            │ Included     │ Mobile menu and clamp sizing  │
│ Screen reader testing        │ Future       │ NVDA/manual test planned      │
└──────────────────────────────┴──────────────┴──────────────────────────────┘
Figure explanation:
This checklist helped me evaluate accessibility as part of the design rather than as a final visual polish step. The application includes accessible navigation labels, mobile menu state, keyboard support, and a cookie dialog. Future evaluation should include manual screen reader testing and checking every form field label.
 
Figure 16. Evaluation Matrix
┌────────────────────┬────────────────────────────┬───────────────────────────┐
│ Evaluation Area    │ Test Task                  │ Success Criteria          │
├────────────────────┼────────────────────────────┼───────────────────────────┤
│ Buyer usability    │ Find a Toyota under $30k   │ User finds relevant result │
│ Filtering          │ Apply make/price filters   │ Results update correctly   │
│ Listing detail     │ Inspect a listing          │ User understands car info  │
│ Enquiry flow       │ Send enquiry message       │ Message is stored/sent     │
│ Seller usability   │ Create a listing           │ Listing appears in browse  │
│ Garage management  │ Delete own listing         │ Only seller can delete it  │
│ Privacy            │ Check seller contact info  │ Contact not publicly shown │
│ Cookie consent     │ Accept/reject cookies      │ Banner updates correctly   │
│ Mobile usability   │ Open mobile menu           │ Menu opens/closes properly │
│ Accessibility      │ Navigate with keyboard     │ All actions reachable      │
│ Performance        │ Load listing pages         │ Target below 3 seconds     │
└────────────────────┴────────────────────────────┴───────────────────────────┘
Figure explanation:
The evaluation matrix turns the prototype into testable tasks. Instead of only checking whether pages exist, I would test whether users can complete the main buyer and seller journeys, whether privacy is protected, whether mobile navigation works, and whether the site performs acceptably under realistic conditions.
