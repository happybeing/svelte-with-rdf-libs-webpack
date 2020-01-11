<script>
import TestRdfjs from "./TestRdfjs.svelte"; // Adds 260K to bundle.js 1.4M to bundle.js.map
import TestGraphy from "./TestGraphy.svelte"; // Adds 360K to bundle.js 1.5M to bundle.js.map (using only the Turtle reader)
import TestRdflib from "./TestRdflib.svelte"; // Adds 606K to bundle.js 2.6M to bundle.js.map
import TestLDFlex from "./TestLDFlex.svelte"; // Adds 1.4M to bundle.js 5.3M to bundle.js.map

</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Svelte with RDF using Webpack</h1>
<TestLDFlex></TestLDFlex>
<TestRdflib></TestRdflib>
<TestGraphy></TestGraphy>
<TestRdfjs></TestRdfjs>
