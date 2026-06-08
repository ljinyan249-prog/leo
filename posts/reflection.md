
---
title: "Final Reflection: Evaluating EazyCars as a Web Application Prototype"

summary:"A final reflection on the performance, user experience, accessibility, functional requirements, and devel opment lessons from the EazyCars web application prototype."
tags:
  - Evaluation
  - User Experience
  - Reflection
---

# Final Reflection: Evaluating EazyCars as a Web Application Prototype

## Evidence Used

The evidence below was gathered from Lighthouse reports, Axe DevTools screenshots, a manual task walkthrough, and a review of the application’s code and database structure. The walkthrough was not a formal usability study, but it helped identify practical issues that could affect real users when completing the main buyer and seller tasks.

| Evidence Type           | What was evaluated                                     | Main observation                                                                                                                                                                       |
| ----------------------- | ------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Lighthouse report       | Performance, accessibility, best practices, SEO        | Simpler pages such as Browse Cars and My Garage performed more strongly, while image-heavy pages such as Home and Listing Detail were more affected by loading behaviour.              |
| Axe DevTools report     | Automated accessibility issues                         | The tested pages did not show major automatic accessibility failures, but manual testing is still needed because automated tools cannot detect every usability or screen reader issue. |
| Manual task walkthrough | Buyer and seller flows                                 | Core tasks were mostly successful, but feedback, validation, and mobile layout details need improvement.                                                                               |
| Code/schema review      | Functional requirements and responsible implementation | The application supports listings, enquiries, seller management, cookie consent, and privacy-focused communication.                                                                    |

## Manual Task Walkthrough

| Manual Task           | Result                      | Issue / Reflection                                                                   |
| --------------------- | --------------------------- | ------------------------------------------------------------------------------------ |
| Browse available cars | Successful                  | The Browse page was clear and supported the buyer journey.                           |
| Apply filters         | Successful with minor issue | Filtering worked, but a clearer “reset filters” button would improve usability.      |
| Open listing detail   | Successful                  | The detail page was useful, but large images affected perceived speed.               |
| Send enquiry          | Partially successful        | The function worked, but the success feedback was not obvious enough.                |
| Create listing        | Successful with minor issue | The form worked, but field-specific error messages should be clearer.                |
| Use My Garage         | Successful                  | Sellers could manage listings, but delete actions should have stronger confirmation. |
| Use mobile layout     | Mostly successful           | Navigation worked, but the cookie banner could cover too much vertical space.        |

## Reflection

After completing EazyCars, I can evaluate it more clearly as a working web application prototype rather than only as a planned idea. My original aim was to build a used-car community hub for the Bla+Bla platform where buyers could browse relevant listings, check basic seller trust information, and contact sellers without exposing personal contact details. Looking back at the final prototype, I think the strongest part of the project is that it delivers a clear core journey for both buyers and sellers. However, the evaluation process also showed that a technically working feature is not always the same as a polished user experience.

The most distinctive value of EazyCars was not simply that it displayed used-car listings. Its main value was the combination of privacy-first enquiries and seller trust indicators inside a community platform. This matched the Bla+Bla brief because the prototype needed to show a tailored feature that made the community different from a generic listing site. In practice, this requirement was mostly met: buyers could inspect listings, check seller context, and contact sellers through the platform. However, the evaluation also showed that the value of this feature depends on small interaction details. If the enquiry confirmation is not obvious, users may not fully trust that the privacy-first communication flow has worked.

In terms of performance, EazyCars worked reliably at prototype scale. The Browse Cars page, My Garage page, and form-based pages were generally responsive because they are mostly structured around text, database records, and simple controls. This showed that the technical stack was suitable for the scope of the project. MojoJS, SQLite, and HTMX gave the application enough structure to support routes, database-backed listings, and partial interactions without needing a full front-end framework. The filtering experience felt especially appropriate for a used-car marketplace because buyers can narrow down listings without the interface feeling overly complex.

The main performance weakness was related to images. The homepage and listing detail page depend heavily on vehicle images to make the marketplace feel active and trustworthy. This is useful from a user experience perspective because buyers expect to see cars before deciding whether to enquire. However, the same images also increased the amount of visual content the browser needed to load, which affected perceived speed. This showed me that performance and visual trust are connected rather than separate design concerns. If I continued development, I would compress images, create smaller thumbnails for listing cards, set consistent image dimensions, and add lazy loading. These improvements would keep the visual value of images while reducing their performance cost.

The user experience was mostly successful because the application has a clear structure. The homepage introduces EazyCars with two main actions: browsing cars and selling a car. This supports the two main user groups immediately. Buyers can move from the homepage to the Browse page, apply filters, open a listing detail page, and send an enquiry. Sellers can create a listing and then manage their listings through My Garage. This structure matched the functional requirements I identified earlier and avoided turning the prototype into a collection of disconnected pages.

However, the manual walkthrough also showed several user experience weaknesses. The most important one was enquiry feedback. The enquiry system supports the unique value of the application because it allows buyers to contact sellers through the platform instead of exposing personal contact details. Functionally, this meets the privacy-first requirement. But after submitting an enquiry, the feedback should be more obvious. A user may wonder whether the message was actually sent, especially if the page does not provide a strong confirmation state. In a future version, I would add a clear success message such as “Your enquiry has been sent,” possibly with a link back to the listing or a record of sent enquiries.

The forms also need better validation feedback. The Sell Car form collects structured vehicle information, which is important because the listing data supports filtering and comparison. But when required fields are missing or incorrect, general browser-level validation is not enough for a polished experience. Field-specific messages would help users understand exactly what to fix. For example, instead of only blocking submission, the interface could show “Please enter a price,” “Please select a make,” or “Year must be a valid number.” This would improve both usability and accessibility because users would receive clearer guidance.

Accessibility was considered throughout the project, but this is also an area where I would continue testing. The automated Axe DevTools evidence was useful because it showed that there were no major obvious issues in the tested pages. The layout also included accessibility-related decisions such as labelled navigation, focus styles, semantic structure, and a cookie banner with clear accept and reject actions. The mobile navigation was useful because it kept Buy, Sell, and My Garage accessible on smaller screens.

At the same time, automated accessibility testing has limits. It cannot fully judge whether the interaction flow makes sense, whether form errors are understandable, or whether a screen reader user receives enough context. If I had more time, I would run a full keyboard-only walkthrough for the main tasks: logging in, browsing, filtering, viewing a listing, sending an enquiry, creating a listing, and using My Garage. I would also test the pages with a screen reader and check every form label and error message. This would give a more realistic accessibility evaluation than relying only on automated tools.

The cookie banner is another example where responsibility and user experience need to be balanced. Including cookie consent was a responsible design decision because it gives users control and shows awareness of privacy and compliance. However, in testing, the banner could take up too much space at the bottom of the screen, especially on smaller devices. This means the feature solves one problem but creates another usability issue. A better version would make the banner more compact on mobile, avoid covering important actions, and disappear clearly once the user has accepted or rejected cookies.

Reflecting on the original functional requirements, I think the prototype met the most important ones. The requirements that were met include browsing listings, filtering cars, viewing listing details, creating listings, using My Garage, and sending enquiries. These features supported the main buyer and seller journeys and gave the prototype a clear structure.

Some requirements were only partially met. Seller trust information is useful, but it is not a full reputation system. It gives buyers basic context such as account age or active listings, but it cannot prove that a seller is reliable. This was still the right decision for the prototype because a full review system would require moderation, fake-review prevention, and real transaction history. Image support was also partially successful. Images improved the listings, but they created performance concerns. The cookie consent banner also worked functionally, but it needs better responsive layout treatment.

Other features were deliberately deferred. Reviews, payments, live chat, full message threads, and recommendation systems were not included because they would add moderation, security, legal, and technical complexity. Looking back, I think this was a good scope decision. The prototype needed to demonstrate the core interaction of a used-car community hub, not become a complete commercial marketplace.

The biggest lesson I learned is that scope control is part of good web development. At the beginning, it was tempting to imagine features such as payments, reviews, saved searches, live chat, and recommendations. During development, I realised that adding too many features would make the application less stable and harder to evaluate. A smaller number of well-connected features created a stronger prototype than a large number of unfinished features.

I also learned that technical decisions directly affect user experience. SQLite made the data structure manageable, HTMX made filtering feel more responsive, and structured models helped separate database logic from page behaviour. At the same time, small interface details such as confirmation messages, validation errors, and mobile spacing had a large impact on whether the application felt complete.

If I continued development, my improvement plan would be realistic and staged. First, I would optimise images through compression, thumbnails, and lazy loading. Second, I would add clearer enquiry confirmation after message submission. Third, I would improve form validation with field-specific error messages. Fourth, I would redesign the cookie banner so that it is less intrusive on mobile screens. Fifth, I would add a full keyboard-only and screen-reader testing process. Finally, if the number of listings increased, I would consider pagination, database indexing, and more structured performance testing under larger datasets.

Overall, EazyCars successfully demonstrates the core idea of a privacy-aware used-car community hub. It performs well enough for prototype scale, supports the main buyer and seller journeys, and includes responsible features such as seller trust indicators and cookie consent. The main improvements are not about completely changing the concept, but about refining the details that make a functional prototype feel trustworthy and usable. This project helped me understand that evaluating a web application means looking beyond whether it works technically. A strong web system also needs to be fast enough, understandable, accessible, responsible, and realistic about its own limitations.

## AI Acknowledgement

AI assistance was used to help structure and edit this reflection. The evaluation points, project evidence, and final responsibility for the writing remain my own.
