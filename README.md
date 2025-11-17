## Table of Contents

- [Introduction](#introduction)
- [Prerequisites](#Prerequisites)
- [Dev Environment](#Dev-environment)
- [React Server Components](#react-server-components)
- [New Next.js Project](#new-nextjs-project)
- [Understanding Project Architecture](#understanding-project-architecture)

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

### Prerequisites

#### ✔ **1. HTML (HyperText Markup Language)**

**Why it's needed:**

* Next.js applications are ultimately rendered as HTML.
* You should understand elements, tags, attributes, forms, semantic HTML, accessibility basics.

**Key topics:**

* Headings, paragraphs, lists, images
* Forms & inputs
* Semantic tags (`<header>`, `<main>`, `<footer>`, `<section>`)
* SEO-related tags (`<title>`, `<meta>`)

---

#### ✔ **2. CSS (Cascading Style Sheets)**

**Why it's needed:**

* Next.js supports many styling methods (CSS Modules, Tailwind, styled-components).
* To style components and layouts effectively.

**Key topics:**

* Flexbox & Grid
* Responsive design (media queries)
* CSS Modules
* Basic animations
* Tailwind CSS (commonly used in Next.js projects)

---

#### ✔ **3. Modern JavaScript (ES6+ concepts)**

**Why it's needed:**

* Next.js uses modern JS features heavily.
* You must write functions, handle async operations, work with modules, etc.

**Key topics:**

* Let, const
* Arrow functions
* Template literals
* Destructuring
* Spread/rest operators
* Async/await
* Promises
* Modules (import/export)
* Array methods (`map`, `filter`, `reduce`)

---

#### ⭐ **Additional Important Prerequisites (Required in REAL projects)**

#### ✔ **4. React Fundamentals**

Next.js is built on top of React, so you must know:

* Components (functional)
* Props
* State (`useState`)
* Hooks (`useEffect`, `useContext`)
* JSX
* Component lifecycle
* React Router basics (helps understand Next.js routing differences)
* Event handling

---

#### ✔ **5. Understanding of Client-Server Architecture**

**You should know:**

* How APIs work
* What is front-end vs backend
* HTTP methods (GET, POST, PUT)
* JSON handling

Make sure you understand:

* Fetching data from APIs
* Client vs server execution

---

#### ✔ **6. Basic Node.js knowledge**

**Next.js runs on Node during SSR/SSG builds, so you should know:**

* What Node.js is
* Basic npm/yarn commands
* Environment variables
* Simple server concepts

You do NOT need advanced backend skills.

---

#### ✔ **7. Git & GitHub (Version control)**

* Branching
* Committing
* Pull requests
* Cloning/pushing

#### ⭐ Optional (But Very Helpful)

##### ✔ TypeScript basics

**Next.js has first-class TypeScript support. Knowing:**

* Types
* Interfaces
* Props typing
* API response typing
  will make you much more professional.

##### ✔ Familiarity with REST APIs or GraphQL

Since data fetching is a major part of building Next.js apps.

---

## Dev-environment
<details>

 **npm create next-app@latest my-app**
* This will install following 
Installing dependencies:
- next
- react
- react-dom

Installing devDependencies:
- @tailwindcss/postcss
- @types/node
- @types/react
- @types/react-dom
- eslint
- eslint-config-next
- tailwindcss
- typescript
<Summary>Project File Structure</Summary>
<details>
## 1️⃣ `layout.tsx` — **Route Layout**

* **Purpose:** Wraps pages in a consistent structure. Think of it like the **frame** of your route.
* **Scope:** Applies to all `page.tsx` files inside the same folder or nested subfolders.
* **Nesting:** Layouts are **nested**, so child layouts can override or extend parent layouts.

**Example structure:**

```
app/
  layout.tsx        → root layout (applies to all pages)
  page.tsx          → homepage
  dashboard/
    layout.tsx      → wraps only dashboard pages
    page.tsx        → /dashboard
```

**Example layout.tsx:**

```tsx
export default function RootLayout({ children }: { children: React.ReactNode }) {
  return (
    <html lang="en">
      <body>
        <header>My Header</header>
        <main>{children}</main>
        <footer>My Footer</footer>
      </body>
    </html>
  );
}
```

* The `children` prop automatically renders the corresponding `page.tsx` inside this layout.

---

## 2️⃣ `page.tsx` — **Route Page**

* **Purpose:** Represents the **UI of a specific route**.
* **Scope:** One `page.tsx` per route.
* **Placement:** Its **folder location defines the URL path**.

**Example:**

```tsx
export default function HomePage() {
  return (
    <div>
      <h1>Welcome to Next.js 15!</h1>
      <p>This is the homepage content.</p>
    </div>
  );
}
```

* If placed under `app/`, it becomes `/`
* If placed under `app/dashboard/`, it becomes `/dashboard`

---

### 🔹 How they work together

1. The `layout.tsx` defines the **wrapper** (header, footer, nav).
2. The `page.tsx` defines the **content** of that route.
3. Next.js **automatically injects the page into the layout** via the `children` prop.

**Flow:**

```
layout.tsx
   └─> children
         └─> page.tsx content
```

So, in practice:

* `layout.tsx` = shared structure
* `page.tsx` = individual route content

</details>
</details>

### react-server-components
**React Server Components is a new architecture that was introduced by React team and quickly adopted by Next.js**
- This architecture introduces a new approach to create React components by dividing them into 2 distinct types: 
* **Server Components**
* Client Components  Server Components: 
* By default Next.js treats all components as Server Components
* These components can perform server-side tasks like reading files or fetching data directly from database
* The trade-offs is that they can’t use React hooks or handle user interaction

* **Client Components:**
* To create Client Component, you will need to add “use client”  on the top of your component file.
* While Client component can’t perform server side tasks like reading files but they can use hooks and handle the user interactions.
* Client components are the traditional React components that we are familiar with in using React  React Server Components & Routing
* As we get into routing, you will see practical examples of both  types
* Work with server components that wait for certain operations to complete before rendering the content
* Use client components to take advantage of hooks from the routing module.
