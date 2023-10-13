https://dev.to/btopro/part-1-how-penn-state-unbundles-web-components-for-cdn-deployments-20di -- Blog series about this technology
This is an optimized workflow for those implementing unbundled builds for web components. The goal is to provide the easiest integration for unbundled builds, made popular by CDNs in large organizations. You have to use yarn because it supports `"flat": true,` which is required for unbundling to work

[![#HAXTheWeb](https://img.shields.io/badge/-HAXTheWeb-999999FF?style=flat&logo=data:image/svg%2bxml;base64,PHN2ZyBpZD0iZmVhMTExZTAtMjEwZC00Y2QwLWJhMWQtZGZmOTQyODc0Njg1IiBkYXRhLW5hbWU9IkxheWVyIDEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgdmlld0JveD0iMCAwIDE4NC40IDEzNS45NyI+PGRlZnM+PHN0eWxlPi5lMWJjMjAyNS0xODAwLTRkYzItODc4NS1jNDZlZDEwM2Y0OTJ7ZmlsbDojMjMxZjIwO308L3N0eWxlPjwvZGVmcz48cGF0aCBjbGFzcz0iZTFiYzIwMjUtMTgwMC00ZGMyLTg3ODUtYzQ2ZWQxMDNmNDkyIiBkPSJNNzguMDcsODMuNDVWNTVIODYuMnY4LjEzaDE2LjI2djQuMDdoNC4wN1Y4My40NUg5OC40VjY3LjE5SDg2LjJWODMuNDVaIi8+PHBvbHlnb24gcG9pbnRzPSIxNTMuMTMgNjMuNyAxNTMuMTMgNTEuMzkgMTQwLjU0IDUxLjM5IDE0MC41NCAzOS4wOSAxMjcuOTUgMzkuMDkgMTI3Ljk1IDI2Ljc5IDEwMi43OCAyNi43OSAxMDIuNzggMzkuMDkgMTE1LjM2IDM5LjA5IDExNS4zNiA1MS4zOSAxMjcuOTUgNTEuMzkgMTI3Ljk1IDYzLjcgMTQwLjU0IDYzLjcgMTQwLjU0IDc2IDEyNy4zNiA3NiAxMjcuMzYgODguMyAxMTQuNzggODguMyAxMTQuNzggMTAwLjYxIDEwMi4xOSAxMDAuNjEgMTAyLjE5IDExMi45MSAxMjcuMzYgMTEyLjkxIDEyNy4zNiAxMDAuNjEgMTM5Ljk1IDEwMC42MSAxMzkuOTUgODguMyAxNTIuNTQgODguMyAxNTIuNTQgNzYgMTY1LjcyIDc2IDE2NS43MiA2My43IDE1My4xMyA2My43Ii8+PHBvbHlnb24gcG9pbnRzPSIzMy4xMyA2My43IDMzLjEzIDUxLjM5IDQ1LjcyIDUxLjM5IDQ1LjcyIDM5LjA5IDU4LjMxIDM5LjA5IDU4LjMxIDI2Ljc5IDgzLjQ4IDI2Ljc5IDgzLjQ4IDM5LjA5IDcwLjg5IDM5LjA5IDcwLjg5IDUxLjM5IDU4LjMxIDUxLjM5IDU4LjMxIDYzLjcgNDUuNzIgNjMuNyA0NS43MiA3NiA1OC44OSA3NiA1OC44OSA4OC4zIDcxLjQ4IDg4LjMgNzEuNDggMTAwLjYxIDg0LjA3IDEwMC42MSA4NC4wNyAxMTIuOTEgNTguODkgMTEyLjkxIDU4Ljg5IDEwMC42MSA0Ni4zMSAxMDAuNjEgNDYuMzEgODguMyAzMy43MiA4OC4zIDMzLjcyIDc2IDIwLjU0IDc2IDIwLjU0IDYzLjcgMzMuMTMgNjMuNyIvPjwvc3ZnPg==)](https://haxtheweb.org/)

# HAX
The authoring experience of HAX and the ability to make fast, static file backed websites rapidly.
Get all the details you want on [HAXTheWeb.org](https://haxtheweb.org/haxcms-1)!
HAX seeks to be the smallest possible back-end CMS to make HAX work and be able to build websites with it. Leveraging JSON Outline Schema, HAX is able to author multiple pages, which it then writes onto the file system. This way a slim server layer is just for basic authentication, knowing how to save files, and placing them in version control.

Watch and Read more about HAX here:
- Youtube channel - https://www.youtube.com/@haxtheweb
- HAXCellence https://oer.hax.psu.edu/bto108/sites/haxcellence/what-is-hax

# Issues / Support / Community
- Discord Channel - https://bit.ly/hax-discord
- Unified issue queue - https://github.com/elmsln/issues/issues
- Using Merlin directly in any HAX spaces and type "Issue" to jump start a report!

## Example from the advanced.html file
[Check out the advanced HTML file](https://github.com/elmsln/unbundled-webcomponents/blob/master/app/advanced.html) to see what's happening. Your site hydrates based on finding tags that are undefined. You'd put these in your application or on a CDN and then the integration methodology is the same every time regardless of app!

## Using this repo in anything
This is a starting point to do a build. Here's how to fork and customize it to be your own:
- Install [yarn](https://classic.yarnpkg.com/en/docs/install/)
- `git clone https://github.com/elmsln/unbundled-webcomponents.git` this repo
- `cd unbundled-webcomponents/app` to move into the directory
- `yarn add` to add / install new elements or edit `app/package.json` directly
- reference all the elements you want to import in `app/dist/app.js` or reference them in `app/dist/index.html`
- `yarn install` to install dependencies
- run `yarn run build` which will generate a build
- copy the `/app/dist/` folder to your server / app location
- add `<script src="./dist/build.js"></script>` to the bottom of your app / CMS or review `app/index.html` or `app/advanced.html` for more complete examples

### Adding assets not caught by the bundler
`app/polymer.json` has a `extraDependencies` property that accepts GLOBs to match files / assets not going to be caught by the bundler. The bundler will find anythign directly referenced (like `import "whatever.js";`) but will miss dynamically created things such as `style.css` file references in the HTML of a component. Adding to this array the specific additional assets to include helps ensure that everything is included in the output of the bundler.

> Wait... I didn't think this was a bundler?!
Well, polymer.json happens to do unbundled builds. It is a bundler / compiler but we're leveraging it just for the compiling capabilites and multiple output targets it provides. As a result, it does have some bundler-isms like having to define additional assets to include in the output, though they are left unbundled as well :)

### Using this repo in Drupal CMS (as an example of implementation, works with anything though)
- download this repo
- add new web components via `yarn add @lrnwebcomponents/h-a-x`
- add `import "@lrnwebcomponents/h-a-x/h-a-x.js";` to the `app/src/app.js` file
- do the build routine spelled out above
- after `yarn run build`, rename the `app/dist/` folder to `webcomponents`
- place this in `sites/all/libraries/`
- You should now have everything in place for this to be wired up

### Why unbundled
- If you are using a CDN approach where elements power multiple sites
- If you build your app as if there is unbundled references and want to leverage optimizations as a result
- If you are using a CMS or application that controls its own JS via a different workflow, this is probably the safer option
- This is a stepping stone to the future. In the next few years unbundling will be possible without tooling thanks to importmaps
- Your running an HTTP/2 server / CDN and know it's faster!

### Why not to unbundle
- anti-pattern in the JS community of today
- still uses `polymer build` to keep things separate
- webpack / rollup by themselves will make smaller asset bundles and your shipping 1 stand alone app as opposed to several sites across a CDN

## Tools in here
This has a configuration of polymer.json, a format used by the polymer CLI in order to create 2 builds of your assets.
- es6+ - This is labeled es6 but is running es8 capable build which all Evergreen browsers support.

### Polymer? We don't want no stinkin..
This uses the polymer CLI for the time being. Once other plugins are written to do in-place, unbundled file building we'll update but for now it does a great job and has no requirement on using polymer in your project as it's just for commandline.

## How does it work?
The file in `/build.js` does feature detection in order to establish if this is an ESM capable platform or needs a different build at run time. This reduces the integration with your platform / CMS / application down to two lines of `<script>` tags. The 1st adds support for CDNs as well as an option for `forceUpdate` which if the browser can't serve the build.js file it will force the user to a page asking them to upgrade.

We feature detect `import()` which 90+% of traffic supports as of end of 2019 and inject ES module based `<script type="module">` imports. From there we try and detect which polyfills are needed based on the platform.

It has been heavily battle tested and is used in production in mutliple domains and websites.

## Who dis
This approach was developed by Penn State and tested by The US National Archives for accuracy.
