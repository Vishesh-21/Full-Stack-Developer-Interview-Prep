**What is the difference between getStaticProps, getServerSideProps, and getStaticPaths?**
These are Next.js data fetching methods. getStaticProps fetches at build time, getServerSideProps fetches per request, and getStaticPaths works with dynamic routes to pre-render pages.

---

**What is the difference between dynamic routes and catch-all routes?**
Dynamic routes use [param], catch-all uses [...param]. Catch-all captures multiple segments.

---

**Difference between rewrite() and redirect()?**

- rewrite(): Changes the URL internally without changing the browser URL (used for masking routes).
- redirect(): Sends the user to a new URL and updates the browser address bar.

---

**cookies vs headers and SSR authentication.**
**_Cookies_**

- Stored in the browser
- Automatically sent with every request
- Best for SSR authentication (sessions, httpOnly cookies)

**_Headers_**

- Sent manually (e.g., Authorization header)
- Common in client-side API calls (JWT, tokens)

**_SSR Authentication_**

- Cookies are preferred because the server can read them directly during SSR.
- Headers are harder to manage in SSR since the browser controls requests.

---

**Explain serverless functions in Next.js.**
Serverless functions in Next.js are backend functions that run on demand without managing servers. API routes are deployed as serverless functions on Vercel or cloud providers.

**_Key points (simple):_**

- Automatically deployed as serverless endpoints
- Scale automatically
- Used for API routes, SSR logic, auth
- Have cold starts and execution limits

---

**What is cold start issue and execution time limits issues?**
**_Cold start issues_** : The delay that occurs when a serverless function starts for the first time after being idle.

why it happens : The platform needs to spin up the runtime environment, load your code, and initialize dependencies.

**_Execution time limits:_** The maximum time a serverless function is allowed to run before it times out.

why it happens : Serverless platforms limit execution to prevent excessive resource usage.

---

**How Next.js Handles Mixed Rendering (SSR, SSG, ISR, CSR) in the Same App**
Next.js allows per-route rendering strategy, not app-wide.

In Pages Router (old way) : Rendering is determined by data-fetching methods:
| Method | Rendering Type |
| ----------------------------- | ----------------------- |
| `getStaticProps` | SSG |
| `getStaticProps + revalidate` | ISR |
| `getServerSideProps` | SSR |
| No data fetching | Static (auto-optimized) |
| Fetch inside useEffect | CSR |

In App Router (modern Next.js): Rendering is determined by:dynamic config, Route segment behavior, fetch() options.

---

**Difference b\w layouts, template, pages.**
**_Pages :_** Represent route, Render content, Re-render when navigating
**_Layout :_** Shared UI, Persist across navigation, Do NOT re-render when child route changes.
**_Templates :_** Re-render on every navigation, Do not preserve state

> Layout = persistent, Template = fresh instance each time

---

**Why Server Components Are Faster?**

- Zero JS sent for that component
- No hydration cost
- Can access DB directly
- Smaller bundle size

---

**NOTE**
If you use:
cookies(), headers(), searchParams, request-specific data, no-store
👉 Next.js switches to dynamic rendering (SSR) automatically.
