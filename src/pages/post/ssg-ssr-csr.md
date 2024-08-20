---
layout: ../../layouts/post.astro
title: "Understanding How Websites Load: SSG, CSR, and SSR Explained"
description: Explore the differences between Static Site Generation, Client-Side Rendering, and Server-Side Rendering, and how popular frameworks like React, Angular, Vue, Next.js, Nuxt.js, and Astro fit into these methods.
dateFormatted: Aug 14th, 2024
---

When building websites, you may come across terms like Static Site Generation (SSG), Client-Side Rendering (CSR), and Server-Side Rendering (SSR). These methods dictate how a website's content is delivered to users and how quickly it loads. Let’s break them down in simple terms.

First, let's understand the process. **Build time** is when your code is transformed into a format that the web server can understand, getting it ready for deployment. **Deployment** is the process of transferring this prepared code to the web server. On the **client side**, users interact with the web page in their browser. When a user performs an action, the browser sends a request to the **web server**, which processes this request and sends back an updated web page that the client then displays.

**Static Site Generation (SSG)** creates your website during the build time. This means that all pages are pre-generated as static HTML files during the build process and then transferred to the web server. When a user requests a page, the web server directly renders that page. This approach provides fast load times and high performance. SSG is ideal when the website's content doesn’t change often.

**Client-Side Rendering (CSR)** involves generating content in the browser after the page has loaded. In CSR, the browser fetches JavaScript files from the web server, which then dynamically creates the HTML. CSR is suitable for applications with dynamic content and interactive features, like [single-page applications (SPAs)](/post/spa-mpa), where user interactions need to be reflected immediately. A common example of CSR is **React, Angular, Vue**.

**Server-Side Rendering (SSR)** generates content on the server before sending it to the browser. When a client requests a page, the server processes the request, generates the HTML for that page, and then sends it to the client. SSR is excellent for sites where SEO and initial load performance are critical because users receive fully rendered pages right away. **Next.js and Nuxt.js** is an example of a framework that supports SSR.

To summarize: **SSG** is ideal for fast, static content; **CSR** offers a dynamic experience with client-side interactions; and **SSR** provides fast initial loads with server-generated content. Frameworks like **Astro** (SSG), **React**, **Angular**, **Vue** (CSR), and **Next.js** and **Nuxt.js** (SSR) help developers choose the best method based on the website’s needs.