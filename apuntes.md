# NextJS

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

`clsx` is a library that lets you toggle class names based on some state. If an invoice status is `pending` or `paid`, then change the color accordingly.

`.ts` Files are Typescript files. This is the language used for modern web apps. It's statically typed Javascript.

`.tsx` Files are extended Typescript Files to enable React Components for Next.js. These files contain JSX which allows you to write HTML into React.

To run the App, run `pnpm dev`.

Fonts play a significant role in the design of a website, but using custom fonts in your project can affect performance if the font files need to be fetched and loaded.

- Next.js automatically optimizes fonts in the application when you use the next/font module. It downloads them at build time and stores them with other asset files to host them instead of users having to download them when visting your application.

Next.js also manages images from the `public/` folder that can be referenced in your app. 

- `next/image` component can be used to automatically optimize your images to make sure they work on different devices + screen sizes.


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
```