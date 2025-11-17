## Table of Contents

- [Introduction](#introduction)
- [Dev Environment](#dev-environment)
- [New Next.js Project](#new-nextjs-project)
- [Understanding Project Architecture](#understanding-project-architecture)
- [React Server Components](#react-server-components)
- [Routing](#routing)
- [Route Handlers](#route-handlers)
- [Fetching Data](#fetching-data)
- [Server Actions](#server-actions)
- [Authentication](#authentication)
- [Next Steps](#next-steps)

## introduction

##### What is nextJS? 
- NEXTjs is a **React framework for building production ready web applications**.
- It provides additional features`(include routing, optimised rendering, data fetching, bundling, compiling)` that enable you to build production-ready applications.
-  No need to install additional packages as Nextjs provides you .
##### Why to learn NextJs? 
- It simplifies the process of building production-ready web applications - 
 1. Routing
 2. API routes
 3. Rendering
 4. server side and client side rendering
 5. Data fetching
 6. Styling
 7. Optimisation
 8. Dev and prod build system

##### **1. React vs Next.js: The Big Picture**

* **React** is a **library for building UI components**. It handles how your interface updates when data changes (the view layer).
* **Next.js** is a **framework built on top of React**. It adds features to handle things that React alone doesn’t cover out-of-the-box, especially for building full production-ready web apps.

Think of it like this:

* React = bricks and cement (UI building blocks)
* Next.js = full construction kit + blueprint + tools (routing, data fetching, SEO, optimization)

React itself **doesn’t tell you how to structure your app, handle routing, fetch data on the server, or optimize for SEO**. Next.js fills these gaps.

---

###### **2. Simplifying Production-Ready Apps**

**Next.js** comes with defaults and conventions that make it easier to go from dev → production:

* **React alone:** You have to configure Webpack, Babel, code splitting, SSR yourself if needed.
* **Next.js:** Comes with pre-configured build system, SSR, code splitting, and optimization automatically.

✅ This saves weeks of setup time.

---

###### **3. Routing**

* **React:** Needs a library like `react-router` for routing. You have to define routes manually and handle nested routes.
* **Next.js:** File-system-based routing. Any file inside `/pages` automatically becomes a route.

  * `/pages/about.js` → `/about`
  * `/pages/blog/[id].js` → dynamic route `/blog/123`

✅ Simplifies routing, especially for dynamic routes.

---

###### **4. API Routes**

* **React:** No backend by default. You need a separate server (Node, Express, etc.) to handle APIs.
* **Next.js:** Lets you create API endpoints inside `/pages/api`.

  * `/pages/api/hello.js` → `/api/hello` endpoint
* You can handle backend logic without a separate server.

✅ Simplifies building full-stack apps in one project.

---

###### **5. Rendering (SSR, CSR, SSG)**

* **React:** Client-side rendering only by default (the page is built in the browser). SEO can be a problem, and initial load can be slower.
* **Next.js:** Supports multiple rendering methods:

  * **CSR (Client-Side Rendering)** – like React
  * **SSR (Server-Side Rendering)** – renders on server for fast initial load & SEO
  * **SSG (Static Site Generation)** – pre-renders pages at build time for max performance
  * **ISR (Incremental Static Regeneration)** – update static pages after build

✅ Simplifies performance optimization and SEO without extra setup.

---

###### **6. Data Fetching**

* **React:** You fetch data manually inside `useEffect` or libraries like SWR/React Query.
* **Next.js:** Provides built-in methods:

  * `getStaticProps` (SSG)
  * `getServerSideProps` (SSR)
  * `getStaticPaths` (for dynamic routes)

✅ Makes data fetching predictable and tied to the rendering method.

---

###### **7. Styling**

* **React:** You choose: CSS, SCSS, CSS Modules, Styled Components, Tailwind, etc. No default.
* **Next.js:** Supports all React styling options and includes:

  * CSS Modules by default
  * Built-in support for global CSS
  * Easy integration with Tailwind, Sass, etc.

✅ Less configuration hassle.

---

###### **8. Optimization**

Next.js handles optimizations automatically:

* Image optimization (`next/image`)
* Automatic code splitting
* Smart caching
* Minification of JS and CSS

✅ Hard to replicate with plain React without lots of manual config.

---

###### **9. Dev & Prod Build System**

* **React:** `create-react-app` sets up dev/prod build, but limited features, harder to customize.
* **Next.js:** Comes with optimized dev & prod workflows:

  * Hot reload during dev
  * Optimized production builds
  * Automatic static & server builds

✅ Makes deploying apps faster and safer.

---

###### **Summary Table: React vs Next.js**

| Feature       | React                 | Next.js                                | How Next.js simplifies                |
| ------------- | --------------------- | -------------------------------------- | ------------------------------------- |
| Routing       | `react-router` needed | File-based `/pages` routing            | No manual routing setup               |
| API           | External backend      | Built-in `/pages/api`                  | Full-stack in one project             |
| Rendering     | CSR only              | CSR, SSR, SSG, ISR                     | Faster, SEO-friendly pages            |
| Data Fetching | `useEffect`           | `getServerSideProps`, `getStaticProps` | Tied to rendering, optimized          |
| Styling       | Any CSS lib           | Supports all + CSS Modules             | Easier integration                    |
| Optimization  | Manual                | Automatic                              | Faster pages, code splitting, caching |
| Build         | CRA/Webpack           | Next.js dev/prod system                | Ready-to-deploy setup                 |

---

