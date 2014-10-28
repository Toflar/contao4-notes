# Routing

Routing is one of the core principles of delivering the correct content based on the request query string (and other conditions such as authentications, request method, hosts, languages etc.)

- foo/bar.html --> returns content "bar"
- foo/otherbar --> return content of otherbar

From Contao 4 on, we'll try to gradually migrate from our very own routing system to the Symfony routing component.

For now, there are only a few Symfony routes defined (matched against in this order [priority]):

- All Contao back end routes (`/contao/{foobar}`)
- The legacy route (`/{page_alias_and_more}`)

## How should I name my routes?

If you want to define your own Symfony routes you should make sure you do not interfere with the ones from the core.
Here are a few rules of thumb for you:

- Never use any `/contao/{foobar}` route. Even if they are not defined by the core bundle yet, they might be in the future.
- For internal or API routes, use the `_` prefix as well as your vendor name for route naming: e.g.: `_isotope_postsale` or `_company_blogpostbundle_pingback`

