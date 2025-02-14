# Silent 404 Errors with next/router.push() in Next.js

This repository demonstrates a subtle bug in Next.js applications where attempting to navigate to a non-existent page using `router.push()` from `next/router` does not throw an error, instead, it silently renders a 404 page.  This can make debugging difficult as there are no error messages to guide the developer.

## The Problem

The `contact.js` file intentionally uses a route that does not exist.  The `about.js` file attempts to navigate to this missing route.  Instead of producing a clear error, Next.js displays a 404 page without any indication in the console that a route was not found.

## How to Reproduce

1. Clone this repository.
2. Run `npm install` to install dependencies.
3. Run `npm run dev` to start the Next.js development server.
4. Navigate to the `/about` page.
5. Click the "Go to Contact Page" button.
6. Observe that you are redirected to a 404 page, but the console does not show any errors related to the missing route.

## Solution

The best solution is to always check if the target route exists before redirecting. This requires a strategy to determine this, for example checking your `pages` directory at build time.
This specific example is addressed in `contactSolution.js`

This example is designed to illustrate a common but easily overlooked issue.  In a larger application, this kind of silent failure could create significant debugging challenges.