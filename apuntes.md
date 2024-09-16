# Next.js

Next.js is an open source JavaScript framework built on top of react to build web apps. Some of the most important features include:

- Enables Server Side Rendering to improve performance and SEO
- Allows you to generate static HTML at build time to improve page loads
- Ability to mix Server Side Rendering and Static Site Generation together
- File based routing to automatically create routes for you based on the folder and file structure within the `pages/` directory.
  - This is different from a traditional React SPA, where the browser loads all your application code on initial load.
  - Splitting code by routes means that pages become isolated. If a certain page throws an error, the rest of the application will still work.
- First class support for TypeScript


`clsx` is a library that lets you toggle class names based on some state. If an invoice status is `pending` or `paid`, then change the color accordingly.

`.ts` Files are Typescript files. This is the language used for modern web apps. It's statically typed Javascript.

`.tsx` Files are extended Typescript Files to enable React Components for Next.js. These files contain JSX which allows you to write HTML into React.

Next.js also manages images from the `public/` folder that can be referenced in your app. 

- `next/image` component can be used to automatically optimize your images to make sure they work on different devices + screen sizes.

You can create APIs in Next.js via route handlers. These APIs often interact with a Database to store & retrieve data, and use an ORM to manage connecting to the database and making the various queries needed to serve requests.

- If you are using React Server Components (fetching data on the server), you can skip the API layer, and query your database directly without risking exposing your database secrets to the client.
- By default, Next.js applications use React Server Components. Fetching data with Server Components is a relatively new approach and there are a few benefits of using them:
- Server Components support promises, providing a simpler solution for asynchronous tasks like data fetching. You can use async/await syntax without reaching out for useEffect, useState or data fetching libraries.
- Server Components execute on the server, so expensive data fetches and logic can happen there and results can just be sent to the client
- Because they execute on the server, you can query database directly without an additional API layer

Whenever a user visits your application, the cached result is served. There are a couple of benefits of static rendering:

- Faster Websites - Prerendered content can be cached and globally distributed. This ensures that users around the world can access your website's content more quickly and reliably.
- Reduced Server Load - Because the content is cached, your server does not have to dynamically generate content for each user request.
- SEO - Prerendered content is easier for search engine crawlers to index, as the content is already available when the page loads. This can lead to improved search engine rankings.

Static rendering is useful for UI with no data or data that is shared across users, such as a static blog post or a product page. It might not be a good fit for a dashboard that has personalized data which is regularly updated.

With dynamic rendering, content is rendered on the server for each user at request time (when the user visits the page). There are a couple of benefits of dynamic rendering:

- Real-Time Data - Dynamic rendering allows your application to display real-time or frequently updated data. This is ideal for applications where data changes often.
- User-Specific Content - It's easier to serve personalized content, such as dashboards or user profiles, and update the data based on user interaction.
- Request Time Information - Dynamic rendering allows you to access information that can only be known at request time, such as cookies or the URL search parameters.

Streaming is a data transfer technique that allows you to break down a route into smaller "chunks" and progressively stream them from the server to the client as they become ready.

- By streaming, you can prevent slow data requests from blocking your whole page. This allows the user to see and interact with parts of the page without waiting for all the data to load before any UI can be shown to the user.
- Streaming works well with React's component model, as each component can be considered a chunk.

Streaming can be implemented either via:

- At the page level, with `loading.tsx` file
- For specific components, you can use `<Suspense>`
- `loading.tsx` is a special Next.js file built on top of Suspense, it allows you to create fallback UI to show as a replacement while page content loads.\
- Since <SideNav> is static, it's shown immediately. The user can interact with <SideNav> while the dynamic content is loading.
- The user doesn't have to wait for the page to finish loading before navigating away (this is called interruptable navigation).
- Since loading.tsx is a level higher than /invoices/page.tsx and /customers/page.tsx in the file system, it's also applied to those pages.

You can implement "Loading Skeletons" which are basically empty versions of your UI that will be populated once the streaming components are completed for the page load

- ![image](https://github.com/user-attachments/assets/879c686c-9440-4301-9fcc-0876be9c1c39)

If you see `(overview)` Folder names that are in parantheses, these are related to Route Groups.

- Route Groups allow you to organize files into logical groups without affecting the URL path structure.
- `/dashboard/(overview)/page.tsx` becomes `/dashboard`
- In this app, this is done to only apply the `loading.tsx` file to the dashboard overview page
- In larger apps, you can also use route groups to separate your application into sections (e.g. (marketing) routes and (shop) routes) or by teams

![image](https://github.com/user-attachments/assets/7ff8b2d5-d6f7-49e0-ad9b-a20847e37001)

- Now a few of the cards can be instantly loaded, while others still retrieve their data
- Typically good practice to move data fetches down to the components that need it


## The App

The App has the following structure:

- `/app` - Contains all routes, components, and logic for the app.
- `/app/lib` - Contains functions used in the app such as reusable utility ones + data fetching ones
- `/app/ui` - Contains all UI components for the app such as cards, tables, and forms.
- `/public` - Contains public assets for the app such as image
- `/app/lib/defintions.ts` - Contains the Schema for all the Database Tables
- `/app/lib/placeholder-data.ts` - Contains dummy data for the project, because users won't have a Remote Database available yet
- `/app/ui/global.css` - Contains CSS rules. This file uses `tailwind` which is a CSS framework that offers pre-existing classes directly in your HTML so you don't have to write tons of CSS.
  - More examples are in `/app/page.tsx`
  - If you prefer writing traditional CSS rules or keeping your styles separate from your JSX - CSS Modules are a great alternative.

To run the App, run `pnpm dev`.

Fonts play a significant role in the design of a website, but using custom fonts in your project can affect performance if the font files need to be fetched and loaded.

- Next.js automatically optimizes fonts in the application when you use the next/font module. It downloads them at build time and stores them with other asset files to host them instead of users having to download them when visting your application.

Next.js also manages images from the `public/` folder that can be referenced in your app. 

- `next/image` component can be used to automatically optimize your images to make sure they work on different devices + screen sizes.


The layout file is the best way to create a shared layout that all pages in your application can use.

Optimizing Navigation is important because you don't want to do full page refreshes everytime you navigate around a website if you can avoid it.

- Next.js uses the `<Link />` Component to link between pages in your application. It allows you to do client side navigation with JavaScript
- Whenever <Link> components appear in the browser's viewport, Next.js automatically prefetches the code for the linked route in the background. By the time the user clicks the link, the code for the destination page will already be loaded in the background, and this is what makes the page transition near-instant!

## Node.js background

Node.js is a runtime environment that allows you to run JavaScript on the server side, outside of a web browser. Traditionally, JavaScript was used only in browsers to build interactive websites, but with Node.js, developers can use JavaScript to write server-side applications, APIs, and even command-line tools.

Node.js comes with npm, which is the default package manager for JavaScript. npm allows you to easily install, manage, and share libraries and tools for your Node.js projects. It's one of the largest software registries in the world.

JavaScript is natively supported by all web browsers, so you don't need Node.js to run JavaScript code in the browser.

While Node.js is a popular choice for running JavaScript on the server, it is not the default for every use case. Other programming languages (e.g., Python, Java, Ruby, Go) are commonly used for backend development as well. However, Node.js is widely adopted due to its performance, simplicity for JavaScript developers, and large ecosystem.


## Installation

This command uses create-next-app, a Command Line Interface (CLI) tool that sets up a Next.js application for you. In the command above, you're also using the --example flag with the starter example for this course.


``` sh
# install nodejs to get npm
asdf plugin-add nodejs https://github.com/asdf-vm/asdf-nodejs.git
asdf list all nodejs
asdf install nodejs 22.8.0
asdf global nodejs 22.8.0

# use npm to install pnpm package manager, which is faster and more efficient than npm or yarn
npm install -g pnpm
npx create-next-app@latest nextjs-dashboard --example "https://github.com/vercel/next-learn/tree/main/dashboard/starter-example" --use-pnpm

pnpm i
pnpm dev

# this will install the vercel postgres sdk
pnpm i @vercel/postgres
```

## Vercel

Vercel is a company that maintains the Next.js framework and they also offer a cloud platform where you can host your Next.js Apps on Cloud Infra. It integrates seamlessly w/ GitHub and can automatically sync after code changes to `main`.
