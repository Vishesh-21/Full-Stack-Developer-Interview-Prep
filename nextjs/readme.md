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

#### What’s the difference between getStaticProps, getServerSideProps, and getStaticPaths?

| Function               | Runs When       | Type                     | Use Case                               |
| ---------------------- | --------------- | ------------------------ | -------------------------------------- |
| **getStaticProps**     | Build time      | Static Generation        | Data rarely changes                    |
| **getServerSideProps** | On each request | Server-side rendering    | Data changes often                     |
| **getStaticPaths**     | Build time      | For dynamic static pages | Needed with dynamic routes (`[id].js`) |

#### How does ISR (Incremental Static Regeneration) work internally?

> ISR (Incremental Static Regeneration) allows you to update static pages after the site has been built, without rebuilding the entire site.
> When a page uses getStaticProps with a revalidate value, Next.js first generates that page at build time and serves it as a static HTML file.
> Whenever a user visits the page, Next.js serves the cached static version instantly. Then, it checks how much time has passed since the last generation.
> If the time exceeds the revalidate period, Next.js triggers a background regeneration — it runs getStaticProps again, creates a new HTML version, and replaces the old one in the cache once ready.
> This way, users always get a fast static response, while the content automatically updates in the background after a certain interval — without rebuilding the whole app.

#### What are the performance trade-offs between SSG and SSR?

| Feature / Factor                | **SSG (Static Site Generation)**            | **SSR (Server-Side Rendering)**               |
| ------------------------------- | ------------------------------------------- | --------------------------------------------- |
| **When HTML is generated**      | At build time                               | On every request                              |
| **Page load speed**             | ⭐ **Very fast** (static files)             | ⚡ **Slower** (server must render each time)  |
| **Server load**                 | 🔽 Low (CDN serves static files)            | 🔼 High (compute needed for rendering)        |
| **Cost**                        | 💰 Cheaper (less server work)               | 💸 More expensive (more compute)              |
| **Scalability**                 | 🚀 Extremely scalable (CDN-based)           | ⚠️ Limited by server capacity                 |
| **Content freshness**           | ❌ Stale until rebuilt (unless ISR)         | ✔ Always fresh                                |
| **Best for**                    | Blogs, docs, landing pages, marketing sites | Dashboards, authenticated pages, dynamic data |
| **SEO**                         | ✔ Good (pre-rendered)                       | ✔ Good (server-rendered HTML)                 |
| **Handling user-specific data** | ❌ Not possible directly                    | ✔ Possible                                    |
| **Caching**                     | ✔ Very effective (static CDN caching)       | ⚠ Harder (dynamic content per request)        |
| **Build time**                  | ⏳ Can be long for large sites              | ⏱ No build-time dependence                    |
| **Runtime performance**         | ⚡ Excellent                                | 🐢 Depends on server speed                    |
| **Fallback for errors**         | ⚠ Requires rebuild or ISR logic             | ✔ Can handle gracefully at runtime            |

#### In the App Router, how does data fetching with fetch() differ from the old data fetching methods?

> In the App Router, data fetching is server-first using the built-in fetch() API instead of page-level methods like getStaticProps and getServerSideProps. fetch() runs on the server, supports automatic caching, revalidation, deduplication, and integrates with React Server Components, enabling streaming and parallel rendering. SSG, SSR, and ISR are no longer separate mechanisms but are controlled through fetch caching options.

#### What are the caching options available in Next.js data fetching (like revalidate, no-store, etc.)?

> Next.js provides caching controls inside fetch() and Route Handlers, letting you choose between SSG, SSR, and ISR behavior.
> NextJs cache options :
>
> - cache: "force-cache" → SSG
> - cache: "no-store" → SSR
> - next.revalidate → ISR
> - next.revalidate: 0 → dynamic (SSR)
> - next.revalidate: false → static
> - next.tags + revalidateTag() → advanced cache invalidation
> - Route handler flags (dynamic, revalidate, fetchCache) give additional control.

#### How File-Based Routing Works Under the Hood in Next.js ?

> Next.js uses your filesystem as the source of truth for routing. Instead of manually defining routes, Next.js scans your folders, analyzes filenames, and automatically builds a routing tree during the build process.

#### How does file-based routing work under the hood in Next.js?

> Next.js implements file-based routing by scanning the filesystem and generating an internal routing manifest that maps file + folder names to URL patterns. For the App Router, it builds a nested React Server Component tree using layouts, pages, loading, and error files. During a request, it matches the URL against this manifest, resolves dynamic parameters, and renders the appropriate components. Dynamic and catch-all routes are implemented by converting filenames like [id] and [...slug] into matchers.

#### Explain parallel routes and intercepting routes in the App Router.

> Parallel routes allow you to define multiple independently rendered UI segments using named slots (like @orders, @customers). Next.js renders these segments in parallel and injects them into the parent layout, enabling split views, multiple panels, and dashboard-style layouts. You define parallel routes using named slots that start with @.

> Intercepting routes allow you to load another route without fully navigating to it. This is done through special patterns like (.), (..), and (…). They are ideal for modal-based navigation—showing a deeper route inside a modal while keeping the current page in the background.

#### What’s the difference between useRouter() in the pages router vs the App Router?

> In the Pages Router, useRouter() (from next/router) gives you full routing info like router.query, pathname, and route events because everything runs on the client. In the App Router, useRouter() (from next/navigation) is much simpler—it only provides client-side navigation methods like push, replace, back, and refresh. Route params and search params must be accessed separately using useParams() and useSearchParams().

#### What’s the difference between Server Components and Client Components?

| Feature / Capability                                        | **Server Components**                                   | **Client Components**                     |
| ----------------------------------------------------------- | ------------------------------------------------------- | ----------------------------------------- |
| **Where they run**                                          | Server                                                  | Browser (client-side)                     |
| **Default type**                                            | ✔ Yes                                                   | ❌ No (must use `"use client"`)           |
| **Can use React hooks (useState/useEffect/useRef)?**        | ❌ No                                                   | ✔ Yes                                     |
| **Can handle events (onClick, onChange)?**                  | ❌ No                                                   | ✔ Yes                                     |
| **Can access browser APIs (localStorage, window)?**         | ❌ No                                                   | ✔ Yes                                     |
| **Can access server resources (DB, filesystem, env vars)?** | ✔ Yes                                                   | ❌ No                                     |
| **Adds JavaScript to bundle?**                              | ❌ No                                                   | ✔ Yes                                     |
| **Rendering mode**                                          | Rendered on server                                      | Hydrated + rendered on client             |
| **Best for**                                                | Data fetching, backend logic, SEO content, static pages | Interactive UI, forms, modals, animations |
| **Bundle size impact**                                      | Minimal (no client JS)                                  | Higher (JS sent to browser)               |
| **Can be imported into**                                    | Server or Client Components                             | Only Client Components                    |
| **Performance impact**                                      | Very fast (no hydration)                                | Slower due to hydration                   |
| **Security**                                                | High (logic stays on server)                            | Lower (code exposed in browser)           |

> Client Components are heavier because they require shipping and running JavaScript in the browser, whereas Server Components render fully on the server and ship only HTML.

> A Client Component can live inside a Server Component, BUT a Server Component cannot be imported inside a Client Component.

#### How nextjs handle the image optimization and lazy loading?

| Feature               | How Next.js Handles It                                    |
| --------------------- | --------------------------------------------------------- |
| **Optimization**      | Compresses, resizes, and serves in modern formats (WebP). |
| **Lazy Loading**      | Enabled by default using IntersectionObserver.            |
| **Responsive Images** | Generates multiple sizes and picks the best one.          |
| **Priority Loading**  | `priority` attribute for above-the-fold images.           |
| **Remote Images**     | Allowlisting remote domains for optimization.             |

#### How Automatic Static Optimization Works in Next.js

> Automatic Static Optimization (ASO) is a feature in Next.js (Pages Router) where a page becomes automatically pre-rendered as static HTML if it does not require per-request data.

#### When Should You Use Dynamic Imports in Next.js?

> Use dynamic imports in Next.js when a component is heavy, only needed on the client, depends on browser APIs, or is not needed during the initial render. They help reduce bundle size, speed up page load, and improve performance.

#### How Next.js Manages Caching & Revalidation on the Edge/CDN

> Next.js (especially on Vercel) uses a full-stack caching model that combines:
>
> - CDN-level (edge) caching
> - Server Component caching
> - Route segment caching
> - Fetch request caching
> - ISR-style revalidation
>   Together, these ensure fast delivery + fresh data across the globe.

#### Data fetching in nextJs.

> Data fetching depends on when and where you want the data. Next.js data fetching is server-first by default, supports static, dynamic, and incremental rendering, and minimizes client-side JavaScript while improving SEO and performance. NextJs multiple data fetching strategies.
>
> - Server-side (default & recommended)
> - Build-time (static)
> - Request-time (dynamic)
> - Client-side (browser)
> - Mutations (Server Actions)

> **Data fetching in Server component** -> SSG, SSR, ISR

#### What is Partial Pre-Rendering (PPR)?

> Partial Pre-Rendering = part of the page is static, part is dynamic

#### When to use server actions and then to use api architecture?

| Feature            | Server Actions                               | API Routes                     |
| ------------------ | -------------------------------------------- | ------------------------------ |
| Best for           | UI-triggered server logic (forms, mutations) | Reusable backend endpoints     |
| Accessed by        | Only inside Next.js app                      | Web, mobile, external          |
| Network cost       | No network call (runs server-side)           | Client → server fetch          |
| Boilerplate        | Minimal                                      | Higher                         |
| Security           | DB stays on server                           | Must secure endpoints manually |
| Good for DB writes | Yes                                          | Yes                            |
| Good for REST APIs | No                                           | Yes                            |


**SSR Flow in Next.js:**

Server renders HTML ➡️ HTML sent to browser ➡️ Browser displays content immediately ➡️ React JS loads ➡️ Hydration happens ➡️ Page becomes interactive