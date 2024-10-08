# Next.js and React for Web Application Stack

## Status

Accepted

## Context

ClearView will have a web interface for interacting with the system. For this we need a modern, responsive, maintainable stack. This has to be a modern technology stack that will be maintainable for the long term.

Aspects to consider:

1. Maintainable
2. Modern - appealing to development teams to work on
3. Flexibility on hosting
4. Supports component libraries for reuse
5. UI Components requirements
   1. Component reuse by component libraries
   2. Accessible by default
6. Various teams could eventually own parts of the UI

## Decision

We will use the following:

- Next.js
  - Supports server side rendering for a responsive UI
  - Supports front end frameworks like React
  - Ease of having path routes - this makes it easier to segregate UIs that different teams might eventually own.
- React
  - Most-used front end framework
  - Broadly supported
- TBD: Component library

## Consequences

We will need a Node.js backend server to host this on. This also means that our business logic will initially exist within the Next.js app but can easily be moved out to other microservices later.
