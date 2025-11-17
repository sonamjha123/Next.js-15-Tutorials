## Table of Contents

- [Introduction](#introduction)
- [Prerequisites](#Prerequisites)
- [Dev Environment](#Dev-environment)
- [React Server Components](#react-server-components)
- [Understanding Project Architecture](#understanding-project-architecture)
- [Routing](#routing)
- [NotFoundPage](#NotFoundPage)
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

## routing
- **Next.js has File-System based Routing**
- URLs you can access based on how you organize your files and folders in your code.

  ##### Routing conventions
  - All routes must live inside the app folder
  - Route files must be named eoith page.tsx or page.jsx
  - Each folder represent a segment of the URL path
  **When these conventions are followed it becomes automatically available as route.**
  
##### Scenarios of creating Routing Files:
 - **Scenario 1:** create /Home---> app/page.tsx
 - **Scenario 2:** create 2 additional routes -->/about, /profile: app>about>page.tsx , app>profile>page.tsx
 - **Scenario 3:** **create nested routes** :` /blog, /blog/firstpage`
 - **Scenario 4:** **Dynamic Routes** : /products has 3 Products like Product 1 , Product 2, Product 3, next if we type  `/products/1` - should show product 1 page content and so on, `/products/2` - should show product 2 page content and so on, `/products/3` - should show product 3 page content and so on.
 - **Scenario 5:** **Nested Dynamic Routes**: `/products/1/reviews/1`
 Here’s a **.md file structure** summarizing your requested Next.js 15 App Router scenarios, **focusing only on folder/file structure**, no code included:

```markdown
# Next.js 15 App Router - File Structure Examples

## Scenario 1: Home Page
```

app/
└── page.tsx

```

---

## Scenario 2: Additional Routes (/about, /profile)
```

app/
├── page.tsx        # Home page
├── about/
│   └── page.tsx    # About page
└── profile/
└── page.tsx    # Profile page

```

---

## Scenario 3: Nested Routes (/blog, /blog/firstpage)
```

app/
├── page.tsx        # Home page
└── blog/
├── page.tsx        # /blog
└── firstpage/
└── page.tsx    # /blog/firstpage

```

---

## Scenario 4: Dynamic Routes (/products/1, /products/2, /products/3)
```

app/
└── products/
├── [productId]/
│   └── page.tsx    # /products/1, /products/2, /products/3

```

---

## Scenario 5: Nested Dynamic Routes (/products/1/reviews/1)
```

app/
└── products/
├── [productId]/
│   └── reviews/
│       └── [reviewId]/
│           └── page.tsx    # /products/1/reviews/1

```
```

 ###### Expalin Routes based on Example
 Perfect! Let's break this down into a **full, working example** for Next.js 15 App Router, **then summarize with key points** you can use in an interview.

---

## **1. Full Next.js 15 App Router Example**

### **Folder Structure**

```
/app
  /dashboard
    layout.tsx
    page.tsx
    /settings
      page.tsx
  /blog
    /[id]
      page.tsx
  layout.tsx
  page.tsx
```

### **Root Layout (`app/layout.tsx`)**

```tsx
import Link from 'next/link';

export default function RootLayout({ children }: { children: React.ReactNode }) {
  return (
    <html>
      <body>
        <nav>
          <Link href="/">Home</Link> | <Link href="/dashboard">Dashboard</Link> | <Link href="/blog/1">Blog 1</Link>
        </nav>
        <hr />
        {children}
      </body>
    </html>
  );
}
```

### **Home Page (`app/page.tsx`)**

```tsx
export default function HomePage() {
  return (
    <main>
      <h1>Welcome Home</h1>
    </main>
  );
}
```

### **Dashboard Layout (`app/dashboard/layout.tsx`)**

```tsx
export default function DashboardLayout({ children }: { children: React.ReactNode }) {
  return (
    <div style={{ border: '1px solid blue', padding: '10px' }}>
      <h2>Dashboard Layout</h2>
      {children}
    </div>
  );
}
```

### **Dashboard Page (`app/dashboard/page.tsx`)**

```tsx
export default function DashboardPage() {
  return <p>This is the main Dashboard page.</p>;
}
```

### **Dashboard Settings Page (`app/dashboard/settings/page.tsx`)**

```tsx
export default function DashboardSettings() {
  return <p>This is the Dashboard Settings page.</p>;
}
```

### **Dynamic Blog Page (`app/blog/[id]/page.tsx`)**

```tsx
import { useParams } from 'next/navigation';

export default function BlogPost() {
  const { id } = useParams();
  return (
    <main>
      <h1>Blog Post {id}</h1>
      <p>This is a dynamic route in the App Router.</p>
    </main>
  );
}
```

✅ **How routes map:**

* `/` → `app/page.tsx`
* `/dashboard` → `app/dashboard/page.tsx`
* `/dashboard/settings` → `app/dashboard/settings/page.tsx`
* `/blog/1` → `app/blog/[id]/page.tsx`

This shows **nested layouts, dynamic routes, and reusable layouts**.

 ###### Routing_Cheat_Sheet

| Feature                  | **App Router (`app/`)**                             | **Page Router (`pages/`)**                               |
| ------------------------ | --------------------------------------------------- | -------------------------------------------------------- |
| **Directory**            | `app/`                                              | `pages/`                                                 |
| **Routing**              | File-based + nested layouts                         | File-based                                               |
| **Layouts**              | Nested layouts (`layout.tsx`) per route             | Only global layout (`_app.tsx`)                          |
| **Dynamic Routes**       | `[param]` syntax                                    | `[param]` syntax                                         |
| **Data Fetching**        | Server-first, async/`fetch`, `generateStaticParams` | `getStaticProps`, `getServerSideProps`, `getStaticPaths` |
| **Server Components**    | Fully supported by default                          | Optional via React 18 support                            |
| **Nested Routing**       | True nested routing                                 | Limited                                                  |
| **Streaming / Async UI** | Supported                                           | Not native                                               |
| **Use Case**             | Large apps, reusable layouts, dynamic pages         | Simple apps, backward compatibility                      |

---

###### **Key Talking Points for Interview**

1. **App Router is modern**: built for React Server Components, nested layouts, async UI.
2. **Page Router is legacy**: simpler, file → route mapping, no nested layouts.
3. **Dynamic routing** works similarly in both: `[id]` → `/blog/1`.
4. **Data fetching differs**: App Router favors server async functions; Page Router uses `getStaticProps`/`getServerSideProps`.
5. **Layouts**: App Router allows route-specific layouts; Page Router only global layout.
6. **Best practice**: Use App Router for **large, modern apps**; Page Router for **small/simple or legacy apps**.

### Nested Routes

### Dynamic Routes 

##### **1. Typing route parameters (`params`)**

In App Router, when you have a dynamic route like:

```
app/products/[productId]/page.tsx
```

Next.js passes **route params** to your component as a prop. TypeScript lets you type them:

```ts
export default function ProductDetails({
  params,
}: {
  params: { productId: string }; // TypeScript type for route params
}) {
  return <p>{params.productId}</p>;
}
```

✅ Key points:

* `params` is an object.
* Keys of `params` correspond to the **dynamic segments** in your file/folder name.
* Example: `[productId]` → `params.productId`.

---

##### **2. Async components typing**

If your component is **async**, TypeScript automatically infers that it returns a `Promise<JSX.Element>`:

```ts
export default async function ProductDetails({
  params,
}: {
  params: { productId: string };
}): Promise<JSX.Element> {
  const product = await fetch(`/api/products/${params.productId}`).then(r => r.json());
  return <p>{product.name}</p>;
}
```

* Async component → return type = `Promise<JSX.Element>`
* Optional: you can **explicitly type** it, but TS can infer it.

---

##### **3. Typing dynamic route arrays (optional)**

If you have **catch-all routes** like `[...slug]`:

```ts
app/docs/[...slug]/page.tsx
```

The `params` type looks like this:

```ts
params: { slug: string[] } // always an array
```

* Example: `/docs/a/b/c` → `params.slug = ["a","b","c"]`

---

##### **4. Typing fetched data**

When you fetch product details, always type the data:

```ts
type Product = {
  id: string;
  name: string;
  price: number;
};

export default async function ProductDetails({
  params,
}: {
  params: { productId: string };
}) {
  const product: Product = await fetch(`/api/products/${params.productId}`).then(res => res.json());
  return <p>{product.name} - ${product.price}</p>;
}
```

✅ Benefits: TypeScript helps with **autocompletion** and **avoids runtime errors**.

---

##### **5. Cheat list of TypeScript you should know here**

1. **Object types for `params`**

   ```ts
   { productId: string } // simple dynamic route
   { slug: string[] }    // catch-all route
   ```
2. **Async function return type**

   ```ts
   async function Component(): Promise<JSX.Element>
   ```
3. **Typing fetched data**

   ```ts
   type Product = { id: string; name: string; price: number; }
   ```
4. **Optional: typing props**

   ```ts
   interface Props { params: { productId: string } }
   export default async function Page({ params }: Props) {}
   ```
5. **Type inference**
   TypeScript can often infer types, especially for async functions in App Router, but explicit types are **better for clarity**.

---

💡 **Memory trick:**

Think of it as **“params are props, fetched data are objects, async components return Promise<JSX>”**. That’s literally all the TypeScript you need to know to be confident in interviews for this pattern.

### What is a Catch-All Segment?

In **Next.js routing**, a **catch-all segment** lets a single route **match multiple nested paths**, instead of defining a separate page for each URL.

It’s like saying:

> “I don’t know how many URL segments there will be, but I want this page to handle them all.”

---

##### **2️⃣ Syntax**

There are two types:

##### **a) Regular Catch-All (`[...param]`)**

* Matches **1 or more segments**.
* Returns an **array** in `params`.

Example:

```
pages/blog/[...slug].js
```

Matches:

```
/blog/post-1            → params.slug = ['post-1']
/blog/2025/11/17/post   → params.slug = ['2025','11','17','post']
```

> Key: `params.slug` is always an **array** of segments.

---

##### **b) Optional Catch-All (`[[...param]]`)**

* Matches **0 or more segments**.
* Works even if the segment is missing.
* Returns **undefined** if no segments.

Example:

```
pages/docs/[[...slug]].js
```

Matches:

```
/docs                   → params.slug = undefined
/docs/getting-started    → params.slug = ['getting-started']
/docs/2025/11/tutorial   → params.slug = ['2025','11','tutorial']
```

> Optional catch-all is great for routes like **docs**, where `/docs` and `/docs/something` should use the same page.

---

##### **3️⃣ How to Use It in Code**

Example: `pages/blog/[...slug].js`

```javascript
import { useRouter } from 'next/router';

export default function BlogPage() {
  const router = useRouter();
  const { slug } = router.query;

  return (
    <div>
      <h1>Blog Page</h1>
      <p>Slug segments: {slug ? slug.join(' / ') : 'No slug'}</p>
    </div>
  );
}
```

**Testing:**

```
/blog/post-1           → Slug segments: post-1
/blog/2025/11/17/post  → Slug segments: 2025 / 11 / 17 / post
```

---

##### **4️⃣ Use Cases**

1. **Blog posts with nested categories**
   `/blog/tech/nextjs/intro` → handled by `[...slug].js`

2. **Docs websites**
   `/docs` or `/docs/guide/setup` → handled by `[[...slug]].js`

3. **Metaverse-style dynamic routing**
   `/world/zone/area/room` → single page handles all nested paths

---

##### **5️⃣ Key Points**

| Feature                  | `[...slug]` | `[[...slug]]`      |
| ------------------------ | ----------- | ------------------ |
| Matches                  | 1+ segments | 0+ segments        |
| Missing segment allowed? | ❌           | ✅                  |
| `params.slug`            | array       | array or undefined |

---

Catch-all segments are **very powerful for dynamic nested paths**, which is very common in **metaverse / NFT / multi-level routing apps**.

---
## NotFoundPage

#### **1. File location**

Create a file named **`not-found.tsx`** inside the `app` directory (or a specific route folder if you want a route-specific 404):

```
app/
└── not-found.tsx
```

---

#### **2. Example content**

```tsx
export default function NotFound() {
  return (
    <main>
      <h1>404 - Page Not Found</h1>
      <p>Sorry, the page you are looking for does not exist.</p>
    </main>
  );
}
```

---

#### **3. How it works**

* **Next.js automatically renders `not-found.tsx`** when:

  1. A dynamic route returns `notFound()` from a Server Component.
  2. The user navigates to a URL that does not exist.

* **Optional usage in a dynamic route:**

```ts
import { notFound } from 'next/navigation';

export default async function ProductPage({ params }: { params: { productId: string } }) {
  const product = await fetchProduct(params.productId);

  if (!product) {
    notFound(); // Triggers the `not-found.tsx` page
  }

  return <div>{product.name}</div>;
}
```

---

#### **Key Points**

1. File: `app/not-found.tsx`
2. Returns **JSX** for 404 page.
3. Can be **triggered manually** using `notFound()` inside a Server Component.
4. Automatically shown for unmatched routes if placed in `app/`.

---

### usePathname Hook - handling error messages for multiple routes
Got it! If you want **one error/Not Found page** but show **different messages based on the route**, here’s the **straightforward approach** in **Next.js 15 App Router** using `usePathname`.

---

## **1. Import `usePathname`**

`usePathname` is a **Next.js hook** from `next/navigation` that gives you the current URL path.

```ts
import { usePathname } from 'next/navigation';
```

---

## **2. Example: Dynamic Not Found Page**

```tsx
'"use client";

import { usePathname } from "next/navigation";
export default function NotFound() {
    const pathname = usePathname();
    const productId = pathname.split("/")[2];   
    const reviewId = pathname.split("/")[4];

    return (
        <>
            <h1>Review {reviewId} of Product {productId} Page Not Found</h1>
            
        </>
    );
}
```

---

## **3. How it works**

1. `usePathname()` returns the current URL as a string, e.g. `/products/1`.
2. You can **conditionally change the message** based on the path.
3. This allows **one Not Found page** to work for multiple routes.
4. Remember: `usePathname` works **only in Client Components**, so add `'use client'` at the top.

---

### ✅ **Key Points**

* One `not-found.tsx` can handle **all routes**.
* `usePathname` lets you **customize the message dynamically**.
* Must be a **client component** if using `usePathname`.
* Works well with **dynamic and nested routes**.

---




 
