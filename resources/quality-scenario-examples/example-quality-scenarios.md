# Example Quality Scenarios for User-Related Quality Attributes

This page contains sample quality scenarios for user-related quality attributes. The scenarios follow the format suggested by Lenn Bass in the book ['Software Architecture in Practice'](https://amzn.to/3YwabRD).

## Performance Efficiency

### Fast Page Load Time for Viewing the Deal of the Day

- **Stimulus**: A user clicks on "View the deal of the day" on the webshop.
- **Stimulus Source**: A first-time user accessing the webshop homepage.
- **Environment**: The system is accessed from a mobile device over a 4G connection (10–30 Mbps).
- **Artifact**: The "Deal of the Day" page.
- **Response**: The page must load quickly to display the promotional deal, preventing user abandonment.
- **Response Measure**: Largest Contentful Paint (LCP) is under 2.5 seconds.

#### Frontend Architecture impact
- **Preferred Rendering Technique**: Static Site Generation (SSG) with Client-Side Rendering (CSR).
- **Architecture Assumption**: Pre-generate static pages for high-traffic promotions like the "Deal of the Day" and use CSR for dynamic content (e.g., live updates or stock availability).

### Quick Search Results Display

- **Stimulus**: A user types a product keyword in the search bar.
- **Stimulus Source**: A user actively searching for products in the webshop.
- **Environment**: The system is accessed on a desktop device with a high-speed broadband connection (100 Mbps).
- **Artifact**: The search results page and sorting of results.
- **Response**: The application must display search results and sorting options with minimal delay.
- **Response Measure**: Interaction to Next Paint (INP) is below 200 ms for responsive sorting, and search results display with LCP under 2 seconds.

#### Frontend Architecture impact
- **Preferred Rendering Technique**: Client-Side Rendering (CSR).
- **Architecture Assumption**: CSR ensures fast in-browser interactions, allowing for quick sorting and filtering without a full-page reload.

### Reducing Perceived Latency When Navigating Between Pages

- **Stimulus**: A user navigates between different sections of the application.
- **Stimulus Source**: A user frequently switches between views (e.g., overview to detailed section).
- **Environment**: The system is accessed on a desktop browser with an average-speed internet connection (10–30 Mbps).
- **Artifact**: The experience of moving between pages and loading new content.
- **Response**: The application must ensure quick and seamless transitions, minimizing perceived delay.
- **Response Measure**: Interaction remains responsive with INP below 200 ms, and main content is rendered within 2.5 seconds.

#### Frontend Architecture impact
- **Preferred Rendering Technique**: Client-Side Rendering (CSR).
- **Architecture Assumption**: CSR enables fast transitions without reloading the page. Prefetching, lazy loading, and caching strategies can be used to optimize performance.

### Efficient Page Rendering Under High Traffic for a Dynamic Web Application

- **Stimulus**: A large number of users (e.g., 10,000 simultaneous users) access dynamic content during a peak event (e.g., flash sale).
- **Stimulus Source**: Multiple users simultaneously request dynamic content.
- **Environment**: The system operates in a high-traffic production environment.
- **Artifact**: The performance and responsiveness of pages that load personalized or updated content.
- **Response**: The application must deliver pages quickly and remain responsive during high traffic.
- **Response Measure**: Pages are served with LCP under 2.5 seconds and server resource utilization remains below 80%.

#### Frontend Architecture impact
- **Preferred Rendering Technique**: Combination of Static Site Generation (SSG) and Client-Side Rendering (CSR) or Server-Side Rendering (SSR) based on content dynamism.
- **Architecture Assumption**: Incorporate server-side or edge caching for frequently accessed content, and efficient client-side data handling for real-time updates.

## Usability

### Responsive Interaction for Adding a Product to the Cart

- **Stimulus**: A user clicks "Add to Cart" after viewing a product’s details.
- **Stimulus Source**: A user ready to purchase.
- **Environment**: The system is accessed on a mobile device over a 4G connection.
- **Artifact**: The responsiveness of adding a product to the cart.
- **Response**: The application must provide instant feedback that the product has been added.
- **Response Measure**: INP is below 100 ms for immediate action feedback.

#### Architecture
- **Preferred Rendering Technique**: Client-Side Rendering (CSR).
- **Architecture Assumption**: CSR allows immediate feedback without a full-page reload.

### Ease of Finding Products in Search Results

- **Stimulus**: A user initiates a product search using a keyword.
- **Stimulus Source**: A user searching for a specific product.
- **Environment**: The system is accessed on both mobile and desktop devices.
- **Artifact**: The search results page with sorting and filtering options.
- **Response**: The application must display clear, well-organized results with easy-to-apply filters.
- **Response Measure**: Users identify relevant products within 5 seconds and apply filters within 3 seconds.

#### Frontend Architecture impact
- **Preferred Rendering Technique**: Client-Side Rendering (CSR).
- **Architecture Assumption**: CSR enables responsive interactions with cached search results to avoid frequent API calls.

### Intuitive Product Detail Page Navigation

- **Stimulus**: A user clicks on a product from search results to view details.
- **Stimulus Source**: A user reviewing a product before purchase.
- **Environment**: The system is accessed on a mobile device.
- **Artifact**: The product detail page.
- **Response**: The page must display detailed information clearly, with key actions visible without scrolling.
- **Response Measure**: Users locate critical information within 3 seconds of page load.

#### Frontend Architecture impact
- **Preferred Rendering Technique**: A combination of SSR for SEO optimization and CSR for interactive elements (e.g., reviews) ensures quick loading with dynamic elements.
- **Architecture Assumption**: CSR for dynamic elements like reviews; SSR for initial page load.

### Simple and Clear Checkout Process

- **Stimulus**: A user initiates the checkout process.
- **Stimulus Source**: A user ready to complete a purchase.
- **Environment**: The system is accessed on a desktop device.
- **Artifact**: The checkout flow, including payment and shipping forms.
- **Response**: The checkout must be simple with clear steps and real-time form validation.
- **Response Measure**: The process is completed in fewer than 4 steps, with form validation feedback under 1 second.

#### Frontend Architecture impact
- **Preferred Rendering Technique**: Server-Side Rendering (SSR).
- **Architecture Assumption**: SSR ensures secure processing of sensitive data, with real-time client-side validation for non-sensitive fields.

## Reliability

### Reliable Loading Times Under High Traffic

- **Stimulus**: 10,000 simultaneous users access the website during a peak event.
- **Stimulus Source**: Users (e.g., during a promotional event).
- **Environment**: The system operates in a production environment under high traffic.
- **Artifact**: The entire web application, especially page load times.
- **Response**: The application must load pages reliably and quickly, even under heavy load.
- **Response Measure**: Pages load within 2 seconds with an error rate below 1%.

#### Frontend Architecture impact
- **Preferred Rendering Technique**: Static Site Generation (SSG).
- **Architecture Assumption**: Pre-generate and cache pages at the edge using a CDN to ensure reliability under peak demand.

### Reliable User Experience with Poor Network Conditions

- **Stimulus**: Poor network conditions cause latency or instability when loading content.
- **Stimulus Source**: A user in a region with unreliable internet connectivity.
- **Environment**: The system is accessed via mobile in a low-connectivity environment.
- **Artifact**: Content load times and interaction responsiveness.
- **Response**: The application must deliver content reliably even under unstable conditions.
- **Response Measure**: Content loads within 3 seconds, even with network latency over 500 ms.

#### Frontend Architecture impact
- **Preferred Rendering Technique**: Client-Side Rendering (CSR).
- **Architecture Assumption**: CSR with caching and local storage strategies (e.g., Service Workers) improves reliability in low-connectivity environments.

### Reliable Data Integrity in Real-Time Applications

- **Stimulus**: Market data changes in real-time and must be reflected immediately.
- **Stimulus Source**: Financial markets or real-time data sources.
- **Environment**: The system operates in a production environment with continuously updating data.
- **Artifact**: The display and processing of real-time data.
- **Response**: The application must update data within 1 second without requiring a page reload.
- **Response Measure**: Data is updated within 1 second of a change.

#### Frontend Architecture impact
- **Preferred Rendering Technique**: SSR with Hydration.
- **Architecture Assumption**: WebSockets or Event Streams enable real-time communication, ensuring immediate updates without full page reloads.

## Security

### Preventing Unauthorized Access to User Accounts

- **Stimulus**: A malicious actor attempts to hijack user sessions via cookies or session data.
- **Stimulus Source**: A third-party attacker.
- **Environment**: The system is accessed via desktop and mobile devices.
- **Artifact**: User session management and authentication mechanisms.
- **Response**: The application must prevent unauthorized access by securing session data.
- **Response Measure**: Secure session cookies with HttpOnly and Secure flags are enforced, and sessions expire after 15 minutes of inactivity.

#### Frontend Architecture impact
- **Preferred Rendering Technique**: Server-Side Rendering (SSR).
- **Architecture Assumption**: SSR handles session management server-side, reducing the risk of session hijacking.

### Secure Handling of Payment Information

- **Stimulus**: A user enters their payment information during checkout.
- **Stimulus Source**: A legitimate user completing a purchase.
- **Environment**: The system is accessed on a desktop device.
- **Artifact**: Payment data (credit card details and billing information).
- **Response**: The application must securely process and transmit payment information.
- **Response Measure**: Payment data is encrypted and processed server-side, complying with PCI DSS standards.

#### Frontend Architecture impact
- **Preferred Rendering Technique**: Server-Side Rendering (SSR).
- **Architecture Assumption**: SSR ensures secure payment processing, with no sensitive data handled by the client side.

### Protecting Against Cross-Site Scripting (XSS)

- **Stimulus**: A malicious user injects a script into a user-generated content field (e.g., product reviews).
- **Stimulus Source**: A malicious actor attempting to inject code via input fields.
- **Environment**: The system is accessed via desktop and mobile browsers.
- **Artifact**: User input fields and output display mechanisms.
- **Response**: The application must sanitize user input to prevent malicious script injection.
- **Response Measure**: All user input is sanitized, with no XSS vulnerabilities.

#### Frontend Architecture impact
- **Preferred Rendering Technique**: Server-Side Rendering (SSR).
- **Architecture Assumption**: SSR mitigates XSS risks by rendering HTML server-side and sanitizing input before sending it to the client.
