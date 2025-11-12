#### How does Next.js differ from client-side React applications in terms of rendering and architecture?

| **Feature**              | **React (CRA)**                                                | **Next.js**                                                                                               |
| ------------------------ | -------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| **Rendering**            | Everything happens in the **browser** (Client-side Rendering). | Can render on the **server** (Server-side Rendering), **build time** (Static Generation), or **browser**. |
| **Speed**                | Slower first load (browser builds the page after JS loads).    | Faster first load (HTML is ready before JS runs).                                                         |
| **SEO (Google ranking)** | Not great — content appears after JS runs.                     | Very good — HTML is ready for search engines.                                                             |
| **Routing**              | You create routes manually with libraries like `react-router`. | Routes are **automatic** — based on the file names in the project.                                        |
| **Data fetching**        | Done in components using `useEffect()` or APIs.                | Built-in functions like `getServerSideProps`, `getStaticProps`.                                           |
| **Backend/API**          | Needs a separate backend.                                      | Has built-in API routes — can act like a small backend.                                                   |
| **Deployment**           | Static site (frontend only).                                   | Supports **serverless** and **edge** deployments.                                                         |

#### What are the different rendering strategies in Next.js and when would you use each (SSR, SSG, ISR, CSR)?

> - SSR (Server-Side Rendering) : The page is built on the server every time someone visits it — users always get fresh data.
> - SSG (Static Site Generation) : The page is built once at build time, and the same pre-made HTML is served to everyone — very fast but not updated automatically.
> - ISR (Incremental Static Regeneration) : The page is built once, but it can auto-refresh after some time — gives speed + updated content.
> - CSR (Client-Side Rendering) : The page loads first, then fetches data in the browser using JavaScript — slower first load, not good for SEO.

#### How does Next.js handle hydration between server and client?

###### Hydration is the process where React links the static HTML (from the server) with React components (in the browser) to make the page interactive.

> Server renders the page (SSR or SSG)
>
> - Next.js runs React components on the server.
> - It creates a ready-to-view HTML page (so users and search engines can see content immediately).

> Browser receives the HTML + React JavaScript bundle
>
> - The user first sees the static HTML instantly.
> - Then Next.js sends JavaScript files that include your React components and logic.

> Hydration starts
>
> - React takes over the static HTML.
> - It “hydrates” the HTML — meaning it attaches event listeners, state, and interactivity to the existing content without re-rendering it from scratch.

> Page becomes interactive
>
> - After hydration, the page works like a normal React app — buttons, forms, and other dynamic parts now respond to user actions.

#### Difference Between pages/ and app/ Directories in Next.js

| **Feature**         | **`pages/` Directory (Old Router)**                                | **`app/` Directory (New App Router)**                                         |
| ------------------- | ------------------------------------------------------------------ | ----------------------------------------------------------------------------- |
| **Introduced in**   | Next.js (before v13)                                               | Next.js 13+                                                                   |
| **Routing System**  | **File-based routing** (each file = one route)                     | **React Server Components** + **nested layouts**                              |
| **Rendering Type**  | Uses **`getStaticProps`, `getServerSideProps`, `getInitialProps`** | Uses **Server Components**, `fetch()`, and async components for data fetching |
| **Component Type**  | All components are **client components** (run in browser)          | Components are **server by default**, unless marked `"use client"`            |
| **Layouts**         | No built-in layout system — you repeat layout on every page        | Has **nested layouts** with shared UI (e.g. navbar, sidebar)                  |
| **Data Fetching**   | Must use special functions like `getServerSideProps`               | Can use **`async` components** and native **`fetch()`** directly              |
| **Loading UI**      | Needs manual loading state                                         | Has built-in **`loading.js`** and **`error.js`** files per route              |
| **Head Management** | Use `<Head>` from `next/head`                                      | Use built-in **`<head>`** export or `metadata` API                            |
| **File Examples**   | `pages/index.js`, `pages/about.js`                                 | `app/page.js`, `app/about/page.js`, `app/layout.js`                           |
| **Status**          | Still supported (for older apps)                                   | Recommended for **new projects**                                              |

#### What happens during the Next.js build process?

> The Next.js build process compiles your React code, pre-renders pages, optimizes assets, and creates a production-ready app in the .next folder.
> | Step | Description |
> | ---------------------------- | ------------------------------------------- |
> | **1. Compile** | Transpile and bundle JS/CSS. |
> | **2. Detect Routes** | Scan `pages/` or `app/` for routes. |
> | **3. Pre-render Pages** | Generate HTML (SSG/ISR) or mark for SSR. |
> | **4. Create `.next` Folder** | Store optimized output. |
> | **5. Optimize** | Compress, split, and minify code. |
> | **6. Deploy** | Ready for production (static + serverless). |

#### How Next.js Handles Bundling and Code Splitting Automatically
| Feature            | What It Does                    | Benefit                |
| ------------------ | ------------------------------- | ---------------------- |
| **Bundling**       | Combines and optimizes all code | Smaller, faster builds |
| **Code Splitting** | Loads only what each page needs | Faster page loads      |
| **Prefetching**    | Loads next page in background   | Instant navigation     |
| **Shared Bundles** | Common code reused across pages | Less duplicate JS      |

