# Proof of concept for a blogging CMS based on strapi and Hugo

In the past I've created several blogs and websites with Wordpress. It was my go to way for creating websites. Since Wordpress is getting a bit rusty, I was searching for a new go to solution. Unfortunately I haven't found any out-of-the-box that could fit to my needs. But I was highly impressed by the simplicity of strapi and the speed of Hugo. So I gave it a little shot to see how these both could work together.

## Requirements
- git
- Node.js
- yarn
- hugo

## Setup
1. Clone this repository
2. `yarn install` from the backend directory
3. Change to the fronted directory and install the noteworthy theme: `git clone https://github.com/kimcc/hugo-theme-noteworthy.git themes/`

## Run
1. `yarn develop` from the backend directory
2. Add the strapi api base url as environment variable, like `export HUGO_BACKEND_API_BASE_URL=http://localhost:1337/api`
3. Generate an strapi api token and add it as environment variable, like `export HUGO_BACKEND_API_TOKEN=1f40fc92da241694750979ee6cf582f2d5d7d28e18335de05abc54d0560e0f5302860c652bf08d560252aa5e74210546f369fbbbce8c12cfc7957b2652fe9a75`
4. `hugo -s remote --ignoreCache && hugo server` from the frontend directory

## Features

- Backend based on strapi and TypeScript
- Frontend based on Hugo with the Noteworthy theme
- Based on the official strapi blog template, migrated to TypeScript
- Installed and configured strapi SEO plugin

## Opportunities and advantages of this solution

During my research of a new CMS / blogging solution I've set a large variety of criteria to fit many use cases. Besides the default criteria of such solutions, the following opportunities came to my mind:

1. Hugo is currently one of the fastest static site generators out there. It comes with a really fast internal webserver as well as a really fast generation of the static files.
2. The static files can be minimized by hugo.
3. Hugo is open-source, growing in popularity and already bullet-proof
4. The generated files can even be deployed in a cloud service like AWS S3 (see also https://github.com/szsascha/vue-s3-cdn)
5. strapi is a headless CMS, meaning it is completely independend from the frontend
6. strapi doesn't face the client in any way since all files are generated static
7. The client doesn't care at all what happens with the backend. Even if there is a longer downtime. So not even a load balancing for strapi is necessary. It could simply run on a self-hosted server.
8. strapi is also open-source, growing in popularity and bullet-proof. Even if it doesn't need to in this architecture.
9. strapi has a growing base of plugins.
10. strapi is really easy to use.

## Some more details
The goal of this PoC was to get a feeling of how good strapi and Hugo are able to work together.

All the articles are managed in the headless backend, based on strapi. These are fetched by Hugo during build time. Hugo stores a copy of them locally in the Markdown format. These Markdown files are used to generate the blog in form of static files.

Most of the magic is happening in the Hugo templates. See `frontend/remote/layouts/index.html`

### Backend

The strapi app has been created with the following command:
`yarn create strapi-app backend --template blog --ts`

### Frontend

Hugo has been initialized with the following command:
`hugo new site frontend`

## Credits
I got highly inspired by the following blog post since it was the solution that fits the best to my needs. 
https://www.thenewdynamic.com/article/toward-using-a-headless-cms-with-hugo-part-2-building-from-remote-api/

This PoC uses the Hugo Noteworthy theme. I'm not affiliated with the creator in any way. But I really liked the simple style, so it was the best available free theme for this PoC.
https://github.com/kimcc/hugo-theme-noteworthy

## Disclaimer

Please keep in mind that this is just a proof of concept and not ready for production use in any way. Even the configuration isn't production ready.
