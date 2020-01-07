<script>
import TestRdflib from "./TestRdflib.svelte";
// import TestLDFlex from "./TestLDFlex.svelte";
// import TestGraphy from "./TestGraphy.svelte";
import TestRdfjs from "./TestRdfjs.svelte";

</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Svelte with RDF using Webpack</h1>
<TestRdflib></TestRdflib>
<!-- <TestLDFlex></TestLDFlex> -->
<!-- <TestGraphy></TestGraphy><!--Not working in Firefox, ok in Chromium -->
<TestRdfjs></TestRdfjs>
