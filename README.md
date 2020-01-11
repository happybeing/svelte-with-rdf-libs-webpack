# Getting RDF libs to work with Svelte (using webpack)

I created this template because I had problems with a standard Svelte rollup built template, and found that switching to 
webpack enabled me to use the RDF libraries I was trying out. This appears to be due to the libraries using outdated 
exports rather than default or named exports, though I have not verified that.

The result here is a test component for each of the libraries listed in src/App.svelte:
```
import TestRdfjs from "./TestRdfjs.svelte"; // Rdfjs adds 260K to bundle.js 1.4M to bundle.js.map
import TestGraphy from "./TestGraphy.svelte"; // graphy adds 360K to bundle.js 1.5M to bundle.js.map (using only the Turtle reader)
import TestRdflib from "./TestRdflib.svelte"; // rdflib.js adds 606K to bundle.js 2.6M to bundle.js.map
import TestLDFlex from "./TestLDFlex.svelte"; // LDFlex + Comunica add 1.4M to bundle.js 5.3M to bundle.js.map
```
## How to use RDF libraries in Svelte
To use any of the RDF libraries listed above you can probably just use a standard `webpack.config.js` or copy the one from this 
project, but note that to use rdflib.js you need to add the following 'externals' in your `webpack.config.js`:
```
  externals: {
    'node-fetch': 'fetch',
    'solid-auth-cli': 'null',
    'fs': 'null-fs'
  },
```
I expect other libaries will work with the same `webpack.config.js`.

## Get started
To create a new project based on this template using [degit](https://github.com/Rich-Harris/degit):

```bash
npx degit sveltejs/svelte-with-rdf-libs-webpack
 svelte-with-rdf-libs-webpack

cd svelte-with-rdf-libs-webpack
```

Install the dependencies...

```bash
cd svelte-app
yarn
```

...then start webpack:

```bash
yarn dev
```

Navigate to [localhost:8080](http://localhost:8080). You should see each component produce output in the browser (and the browser console). Edit a component file in `src`, save it, and the page should reload with your changes.


## Deploying to the web

### With [now](https://zeit.co/now)

Install `now` if you haven't already:

```bash
yarn global add now
```

Then, from within your project folder:

```bash
now
```

As an alternative, use the [Now desktop client](https://zeit.co/download) and simply drag the unzipped project folder to the taskbar icon.

### With [surge](https://surge.sh/)

Install `surge` if you haven't already:

```bash
yarn global add surge
```

Then, from within your project folder:

```bash
yarn build
surge public
```
