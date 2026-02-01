**What is the difference between getStaticProps, getServerSideProps, and getStaticPaths?**
These are Next.js data fetching methods. getStaticProps fetches at build time, getServerSideProps fetches per request, and getStaticPaths works with dynamic routes to pre-render pages.

**What is the difference between dynamic routes and catch-all routes?**
Dynamic routes use [param], catch-all uses [...param]. Catch-all captures multiple segments.

**Difference between rewrite() and redirect()?**
- rewrite(): Changes the URL internally without changing the browser URL (used for masking routes).
- redirect(): Sends the user to a new URL and updates the browser address bar.

**cookies vs headers and SSR authentication.**
***Cookies***
- Stored in the browser
- Automatically sent with every request
- Best for SSR authentication (sessions, httpOnly cookies)

***Headers***
- Sent manually (e.g., Authorization header)
- Common in client-side API calls (JWT, tokens)

***SSR Authentication***
- Cookies are preferred because the server can read them directly during SSR.
- Headers are harder to manage in SSR since the browser controls requests.

**Explain serverless functions in Next.js.**
Serverless functions in Next.js are backend functions that run on demand without managing servers. API routes are deployed as serverless functions on Vercel or cloud providers.

***Key points (simple):***
- Automatically deployed as serverless endpoints
-  Scale automatically
- Used for API routes, SSR logic, auth
- Have cold starts and execution limits

**What is cold start issue and execution time limits issues?**
***Cold start issues*** : The delay that occurs when a serverless function starts for the first time after being idle.  

why it happens : The platform needs to spin up the runtime environment, load your code, and initialize dependencies.

***Execution time limits:*** The maximum time a serverless function is allowed to run before it times out.

why it happens : Serverless platforms limit execution to prevent excessive resource usage.

