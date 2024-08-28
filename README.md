# The Frontend Architecture Map

The Frontend Architecture Map is a powerful collaboration technique that maps the user journey while integrating essential 
architectural considerations for next-generation web applications. It is ideal for cross-functional product teams and ensures the 
development of robust and user-friendly web experiences.

![Frontend Architecture Map](resources/example-frontend-architecture-map-en.png "The Frontend Architecture Map V1")

## Summary

- [How to Use](#how-to-use)
- [Tools](#tools)
- [Additional Resources](#additional-resources)

## How to Use

### Start with a user story map

In story mapping, a user's journey is broken down into the most important user activities and tasks and organized in a visual map. This map is organized horizontally by sequence of activities and vertically by priority or complexity, helping teams understand the flow and identify gaps or opportunities in the user experience. The goal is to agree on what needs to be built, in what order and to what extent.

This is a great starting point for the Frontend Architecture Map.

If you don't have experience with story mapping, you can learn more about it in the book [User Story Mapping: Discover the Whole Story, Build the Right Product](https://amzn.to/4dBS5mc) by Jeff Patton.

More resources:
- [User Story Mapping: A Quick Overview](https://jpattonassociates.com/story-mapping/) by Jeff Patton


### Discuss the interactivity factor

For each user task or activity, discuss the interactivity factor that will be required. This will help you identify the components that will be needed and how they will interact with each other.

Discuss if the interaction with the web app on this task will be:

* No interaction, just view (0)
    * View static content without any interaction. E.g. read a blog post.
* Low interaction (1)
    * Simple interactions like clicking a button or filling a form. E.g. a contact form.
* Medium interaction (2)
    * Partially dynamic feedback on interactions, e.g. a search form with results.
* High interaction (3)
    * Highly dynamic interactions with real-time answers, e.g. a chat application.


### Discuss the content update frequency (CUF)

For each user task or activity, discuss the content update frequency (CUF) that will be required. 

Discuss for each of this activity or task how often the content will be updated:

* Rare (0)
    * The content is updated very rarely, e.g. < once a month.
* Occasional (1)
    * The content is updated occasionally, e.g. 1-3 times a month.
* Regularly (2)
    * The content is updated regularly, e.g. 1-3 times a week.
* Frequent (3)
    * The content is updated frequently, e.g. > 3 times a week or on a daily basis.

### Go through the user expectations (user related quality attributes)

For each user task or activity, discuss the user related quality attributes that will be required.

* Performance efficiency
* Usability
* Reliability
* Security

Try to scale the expectation each of these quality attributes from low to high (0 - 4).

And check if the specific task is related to SEO.

### Do first architecture assumptions

The corresponding rendering technique does highly influence the architecture of the frontend and gives requirements for your technology. Therefore, it is important to define the rendering strategy for each user task or activity.

#### Rendering

> Rendering = Template ("preliminary markup") + Data = Displayed Web Page

Try to define the rendering strategy for each user task or activity.

* Client-side rendering (CSR)
* Server-side rendering (SSR)
* Static site generation (SSG)
* Combined rendering strategies
    * Server-side rendering with client-side hydration (SSR+CSR)
    * Static site generation with client-side hydration (SSG+CSR)
    * Incremental static site generation (SSR + SSG)


If you are not sure about the rendering strategy, you can use the following questions to help you decide:

* High interactivity: Potential client-side rendering
* Low interactivity: Potential server-side rendering or static site generation

* Content Update Frequency (CUF):
    * Rare: (incremental) static site generation
    * Occasional: Potential server-side rendering or static site generation
    * Regularly: Potential client-side rendering or server-side rendering
    * Frequent: Potential client-side rendering or server-side rendering

* Will the content be updated frequently?
    * Yes: Client-side rendering
    * No: Server-side rendering or static site generation
* Will the content be updated by the user?
    * Yes: Client-side rendering
    * No: Server-side rendering or static site generation
* Will the content be updated by the server?
    * Yes: Server-side rendering
    * No: Static site generation
* Will the content be updated by a third-party service?
    * Yes: Client-side rendering
    * No: Server-side rendering or static site generation   
* Will the content be indexed by search engines?
    * Yes: Server-side rendering or static site generation (or CSR with pre-rendering)
    * No: Client-side rendering

#### App Scope and Ownership

Try to define the app scope and ownership for each user task or activity.

The organisation of your company and the team structure will influence the architecture of your frontend. Therefore, it is important to define the app scope and ownership for each user task or activity.

Try to assume the app scope and ownership activity (or user task).