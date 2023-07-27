yarn create strapi-app backend --template blog --ts
yarn develop

- Strapi with blog template and typescript
- Strapi SEO plugin
- Change Strapi templates to TS https://forum.strapi.io/t/unable-to-connect-to-strapi-end-points-404-not-found-error/23102/7


hugo new site frontend
git clone https://github.com/kimcc/hugo-theme-noteworthy.git themes/noteworthy
hugo server
hugo new posts/my-first-post.md

hugo -s remote --ignoreCache && hugo serve

- Hugo with noteworthy theme

https://www.thenewdynamic.com/article/toward-using-a-headless-cms-with-hugo-part-2-building-from-remote-api/

export HUGO_BACKEND_API_BASE_URL=http://localhost:1337/api
export HUGO_BACKEND_API_TOKEN=