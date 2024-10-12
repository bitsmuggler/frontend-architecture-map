# Example quality scenarios for user related quality attributes

This page contains sample quality scenarios for user-related quality attributes. The scenarios are structured according to the format suggested by Lenn Bass in the book ['Software Architecture in Practise'] (https://amzn.to/3YwabRD).

## Performance efficiency

### Fast Page Load Time for Viewing the Deal of the Day

**Stimulus**: A user visits the webshop and clicks on "View the deal of the day" to check the daily promotional item.

**Stimulus Source**: A first-time user accessing the webshop homepage.

**Environment**: The system is accessed from a mobile device over a 4G connection (10–30 Mbps).

**Artifact**: The "Deal of the Day" page.

**Response**: The application must load the page quickly to display the promotional deal and avoid users abandoning the page.

**Response Measure**: The Largest Contentful Paint (LCP) is under 2.5 seconds to ensure that the main content (the deal) is visible quickly.

**Preferred Rendering Technique**: Static Site Generation (SSG) with Client-Side Rendering (CSR)

**Architecture Assumption**: Pre-generate static pages for high-traffic promotions like the "Deal of the Day" and use CSR to handle dynamic content (e.g., if the deal has live updates or stock availability). This ensures fast delivery and SEO optimization, as noted by the SEO relevance indicator in the architecture map.

### Quick Search Results Display

* **Stimulus**: A user types a product keyword in the search bar and expects to see product search results immediately.

* **Stimulus Source**: A user actively searching for products in the webshop.

* **Environment**: The system is accessed on a desktop device with a high-speed broadband connection (100 Mbps).

* **Artifact**: The search results page and the sorting of results.

* **Response**: The application must present the search results quickly and allow sorting options with minimal delay to ensure smooth interaction.

* **Response Measure**: The Interaction to Next Paint (INP) is below 200 ms for responsive sorting, and search results are displayed with Largest Contentful Paint (LCP) under 2 seconds.

* **Preferred Rendering Technique**: Client-Side Rendering (CSR)

* **Architecture Assumption**: Since search results are dynamic and personalized, CSR ensures fast in-browser interactions, enabling users to type and see results with minimal delay. Using CSR allows for quick sorting and filtering without a full-page reload, keeping the interaction smooth for frequent actions like product searching.

### Reducing Perceived Latency When Navigating Between Pages

**Stimulus**: A user navigates between different sections of the application, where new content must be fetched from various sources.

**Stimulus Source**: A user frequently switches between different views, such as from an overview page to a detailed section.

**Environment**: The system is accessed on a desktop browser with a stable but average-speed internet connection (10 - 30 Mbps).

**Artifact**: The experience of moving between pages and loading new content.

**Response**: The application must ensure quick and seamless transitions between views, minimizing perceived delay and ensuring a smooth user experience.

**Response Measure**: The interaction remains responsive, with Interaction to Next Paint (INP) below 200 ms, and the main content on each new page is rendered within 2.5 seconds to meet user expectations for fast transitions.

**Preferred Rendering Technique**: Client-Side Rendering (CSR)

**Architecture Assumption**: Client-Side Rendering (CSR) enables fast transitions between views without reloading the entire page. To enhance performance, prefetching and lazy loading can be employed to load resources in the background before the user navigates. Caching strategies ensure that frequently accessed data is stored locally, reducing the need for repeated server requests. This architecture ensures responsiveness and fast page transitions.

## Efficient Page Rendering Under High Traffic for a Dynamic Web Application

* **Stimulus**: A large number of users (e.g., 10,000 simultaneous users) access dynamic content, such as product pages or user profiles, during a peak event (e.g., a flash sale).

* **Stimulus Source**: Multiple users simultaneously request dynamic content that must be personalized or updated in near real-time.

* **Environment**: The system is accessed in a high-traffic production environment, with concurrent requests for both static and dynamic data.

* **Artifact**: The performance and responsiveness of pages that dynamically load personalized or updated content.

* **Response**: The application must deliver pages that load quickly and remain responsive during high traffic, while also ensuring that dynamically generated content is up-to-date.

* **Response Measure**: Pages are served with a Largest Contentful Paint (LCP) under 2.5 seconds, even with 10,000 concurrent users, and server resource utilization (CPU and memory) does not exceed 80%, ensuring system stability and scalability under load.


* **Preferred Rendering Technique**: The preferred rendering technique will depend on balancing dynamic content generation with scalability and performance under load:

    * If the content is highly dynamic and personalized for each user, Server-Side Rendering (SSR) may be optimal to ensure the most up-to-date content is served.
    * If much of the content can be cached or pre-generated, a combination of Static Site Generation (SSG) for less dynamic content, supplemented by Client-Side Rendering (CSR) for dynamic updates, may offer better scalability and performance.
Architecture Assumption: The architecture must incorporate server-side or edge caching for frequently accessed content and efficient client-side data handling for real-time updates.

## Usability

### Responsive Interaction for Adding a Product to the Cart

**Stimulus**: A user views a product's details and clicks "Add to Cart" after reviewing the information.

**Stimulus Source**: A user who is ready to purchase a product after reviewing its details.

**Environment**: The system is accessed on a mobile device over a 4G connection.

**Artifact**: The responsiveness of adding a product to the cart.

**Response**: The application must provide instant feedback that the product has been added to the cart, ensuring that the interaction feels immediate and smooth.

**Response Measure**: The Interaction to Next Paint (INP) is below 100 ms, ensuring the user sees confirmation of the action right away.

**Preferred Rendering Technique**: Client-Side Rendering (CSR)

**Architecture Assumption**: The "Add to Cart" interaction benefits from CSR, allowing for immediate feedback without needing a full-page reload. The architecture should ensure smooth, responsive interactions for frequent actions like adding items to the cart.

### Ease of Finding Products in Search Results

* **Stimulus**: A user initiates a product search by typing a keyword and wants to quickly locate the desired product from the results.

* **Stimulus Source**: A user actively searching for a specific product using keywords.

* **Environment**: The system is accessed on both mobile and desktop devices.

* **Artifact**: The search results page, including sorting and filtering options.

* **Response**: The application must display search results in a clear and user-friendly way, with well-organized filters and sorting options, so the user can easily find relevant products.

* **Response Measure**: Users can identify the relevant product within 5 seconds of viewing the results, and they can easily apply filters or sorting options within 3 seconds of interaction.

* **Architecture Assumptions**:

    * Rendering Technique: Client-Side Rendering (CSR) would be preferred for interactive elements like sorting and filtering. CSR allows for immediate feedback without the need to reload the page, providing a seamless experience.
    * Caching Strategy: Search results should be cached to avoid frequent API calls, particularly when filtering or sorting. This can speed up interactions and ensure the interface responds quickly.
    * UI/UX: The architecture must support clear UI patterns, with prefetching for images or product details to minimize perceived load times when the user hovers or clicks on a product.

### Intuitive Product Detail Page Navigation

* **Stimulus**: A user clicks on a product from the search results and expects to easily find detailed product information, such as price, specifications, and reviews.

* **Stimulus Source**: A user reviewing the details of a product before making a purchase decision.

* **Environment**: The system is accessed on a mobile device.

* **Artifact**: The product detail page.

* **Response**: The product detail page must present information in a clear, well-structured manner, with visible buttons for key actions (e.g., "Add to Cart" and "Read Reviews"). The user should be able to easily navigate through different sections without confusion.

* **Response Measure**: Users can locate critical product information (price, specifications, reviews) within 3 seconds of loading the page, and key actions (e.g., "Add to Cart") should be visible and accessible without scrolling.

* **Architecture Assumptions**:

    * Rendering Technique: A combination of Server-Side Rendering (SSR) for SEO optimization and Client-Side Rendering (CSR) for interactive elements such as reviews or additional product options (e.g., size, color) would work best. This combination ensures the main content loads quickly, while dynamic elements can be loaded after the initial page render.
    * Lazy Loading: Non-critical content (such as product reviews) should be lazily loaded to avoid overwhelming the user with too much information immediately. This reduces the time to display core product details.
    * Responsive Design: The architecture must support a responsive layout, ensuring that the page adapts smoothly between mobile and desktop screens. CSS frameworks or media queries should be used to ensure consistency across device types.
    * Edge Caching: Frequently viewed product pages could be cached at the edge using a Content Delivery Network (CDN) to speed up delivery for popular products, minimizing server load and improving the user experience on the first visit.

### Simple and Clear Checkout Process

* **Stimulus**: A user adds items to their cart and initiates the checkout process by providing payment and shipping information.

* **Stimulus Source**: A user trying to complete a purchase.

* **Environment**: The system is accessed on a desktop device .

* **Artifact**: The checkout flow, including payment and shipping form fields.

* **Response**: The checkout process must be simple, with clear and concise form fields and a straightforward flow that minimizes the number of steps. Users should easily understand each required input (e.g., payment details, address) and have access to a summary before final confirmation.

* **Response Measure**: Users can complete the checkout process in fewer than 4 steps, and the form completion time is under 2 minutes, with clear feedback provided for any form errors within 1 second of submission.

* **Architecture Assumption**:
    * SSR provides greater control over data handling during the checkout process, ensuring that sensitive data like payment and shipping details are securely processed on the server. This also helps in preventing exposure of sensitive information to the client, minimizing potential attack vectors.
    * Real-Time Form Validation: While SSR will handle the main rendering, client-side JavaScript can still be used to provide real-time validation for non-sensitive form fields (e.g., checking if the postal code is in the correct format), but all critical validation (e.g., payment info) will happen server-side to comply with security standards.
    * Session Management: Secure session management will ensure that user state (e.g., items in cart) is properly handled server-side, reducing the risk of session hijacking or data manipulation.

## Reliability

### Reliable Loading Times Under High Traffic

* **Stimulus**: 10,000 simultaneous users access the website (high traffic).
* **Stimulus Source** Users (e.g., during a promotional event like Black Friday).
* **Environment**: The system operates in a production environment under high traffic.
* **Artifact**: The entire web application, especially the page load times.
* **Response**: The application delivers pages reliably and quickly, even under heavy server load, without crashing or slowing down.
* **Response Measure**: Pages load within 2 seconds under heavy traffic, even with 10,000 simultaneous requests, and the error rate (e.g., 500 errors) remains below 1%.


**Preferred Rendering Technique**: Static Site Generation (SSG)

**Possible resulting frontend architecture assumption**: With pre-generated and cached pages, the server doesn’t need to re-render for each request. SSG is ideal when content changes infrequently and high traffic is expected, as it minimizes server load and ensures reliability under peak demand. The architecture will leverage a Content Delivery Network (CDN) to distribute static pages across multiple servers, reducing bottlenecks and improving reliability.

## Reliable User Experience with Poor Network Conditions

* **Stimulus**: Poor network conditions cause latency or instability when loading content.
* **Stimulus Source**: A user in a region with slow or unreliable internet connectivity.
* **Environment**: The system is used in a mobile environment with poor internet connection.
* **Artifact**: The web application, especially content load times and user interaction.
* **Response**: The application reliably delivers content quickly and smoothly, even under unstable connections.
* **Response Measure**: Content loads within 3 seconds, even with network latency exceeding 500 ms.

**Preferred Rendering Technique**: Client-Side Rendering (CSR)

**Possible resulting frontend architecture assumption**: CSR is advantageous here as the page loads initially and then only fetches data via APIs, reducing the volume of data required and reliance on a stable connection. CSR allows more logic and data handling to occur on the client side, reducing the burden on the server. The architecture will include caching and local storage strategies (e.g., Service Workers or IndexedDB) to improve reliability in low-connectivity environments.

## Reliable Data Integrity in Real-Time Applications

* **Stimulus**: Market data changes in real-time and must be quickly reflected on the page.
* **Stimulus Source**: Financial markets or data sources providing real-time data.
* **Environment**: The system is used in a production environment with continuously updating data.
* **Artifact**: The web application, specifically the display and processing of real-time data.
* **Response**: The application reliably displays updated data without interruptions or data loss.
* **Response Measure**: Data is updated within 1 second of a change, without requiring the user to reload the page.


**Preferred Rendering Technique**: SSR with Hydration 

**Architecture Assumption**: CSR enables real-time data updates directly in the browser using WebSockets or similar technologies, without requiring full page reloads. Alternatively, SSR could be used with dynamic elements, but that would involve more frequent server-side page reloads. The architecture will employ WebSockets or Event Streams for real-time communication, ensuring a direct link between server and client for immediate updates. If SSR is used, WebSocket connections may be utilized for partial updates within the page.

## Security

### Preventing Unauthorized Access to User Accounts

* **Stimulus**: A malicious actor attempts to access a user’s account by tampering with cookies or session data.

* **Stimulus Source**: A third party attempting to hijack user sessions through cookie theft or session fixation attacks.

* **Environment**: The system is accessed via both desktop and mobile devices, and the user is logged into their account.

* **Artifact**: User session management and authentication mechanisms.

* **Response**: The application must prevent unauthorized access by securing session data and ensuring only authorized users can access their account.

* **Response Measure**: User sessions are protected with secure session cookies (with HttpOnly and Secure flags enabled) and session expiry is enforced within 15 minutes of inactivity. Any tampered cookies or session tokens must be detected and invalidated immediately.

* **Preferred Rendering Technique**: Server-Side Rendering (SSR)

* **Architecture Assumption**:
    * With SSR, session management is handled server-side, reducing the risk of exposing sensitive session data to the client. Server-side storage of session tokens (e.g., using HttpOnly cookies) helps protect against attacks like Cross-Site Scripting (XSS) or session hijacking.
    * Secure Authentication: The system should leverage secure authentication mechanisms such as OAuth2 or JWT, with tokens securely managed and verified on the server. Server-side session validation ensures that any tampering with session data results in immediate rejection.
    * TLS Encryption: All communication, including session tokens, should be transmitted over TLS to prevent man-in-the-middle attacks.


### Secure Handling of Payment Information

* **Stimulus**: A user enters their payment information (e.g., credit card details) during the checkout process.

* **Stimulus Source**: A legitimate user attempting to complete a purchase.

* **Environment**: The system is accessed on a desktop device during the checkout process.

* **Artifact**: Payment data, including sensitive credit card information and billing details.

* **Response**: The application must ensure that payment information is securely processed and transmitted without exposing sensitive data to the client-side or unauthorized third parties.

*  **Response Measure**: Payment data is encrypted and securely transmitted using TLS during the entire process. Payment information is never exposed to the client side, and any sensitive data is processed server-side to comply with PCI DSS standards.

* **Preferred Rendering Technique**: Server-Side Rendering (SSR)

* **Architecture Assumption**:
    * SSR allows sensitive data such as payment details to be processed on the server, keeping the client-side interaction minimal to reduce the risk of exposing payment information via the frontend.
    * PCI Compliance: The system must comply with PCI DSS standards, ensuring that no sensitive payment data is stored or transmitted insecurely. All payments should be processed server-side, and sensitive information should never be handled directly by the frontend.
    * Tokenization: Payment details can be tokenized, meaning sensitive data is converted into tokens that are meaningless if intercepted. This ensures that payment data remains secure even if transmitted over the network.

###  Protecting Against Cross-Site Scripting (XSS)

* **Stimulus**: A malicious user injects a script into a user-generated content field (e.g., product reviews or feedback forms) in an attempt to execute malicious JavaScript on other users’ browsers.

* **Stimulus Source**: A malicious actor attempting to inject code into user input fields to gain access to user data or compromise accounts.

* **Environment**: The system is accessed on both desktop and mobile browsers, with users submitting and viewing content (e.g., product reviews).

* **Artifact**: User input fields and output display mechanisms.

* **Response**: The application must sanitize all user input to prevent malicious scripts from being injected and executed on other users' browsers.

* **Response Measure**: All user input is sanitized and validated before being rendered. No XSS vulnerabilities are exploitable, and no malicious scripts are executed in user browsers. The application should pass security penetration tests for XSS attacks.

* **Preferred Rendering Technique**: Server-Side Rendering (SSR)

* **Architecture Assumption**:
    * SSR helps mitigate XSS risks by controlling how content is rendered on the server side. By rendering HTML on the server and sanitizing user inputs before sending them to the client, the risk of XSS attacks is minimized.
    * Input Sanitization: All user-generated content should be sanitized before being stored or rendered to the user. Libraries such as DOMPurify can be used on the server to strip malicious code from input fields.
    * Content Security Policy (CSP): The system should enforce a strict Content Security Policy (CSP) to prevent the execution of inline scripts or untrusted code. This further reduces the chances of malicious scripts being executed in the user's browser.