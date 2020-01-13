<script>
import { onMount } from 'svelte';

const rdflibx = require('rdflib');

const rdf = {
  uri: 'https://example.org/resource.ttl',
  mimeType: 'text/turtle',
  body: `
    @prefix foaf: <http://xmlns.com/foaf/0.1/> .

    <#spiderman> a foaf:Person ;
        foaf:name "Spiderman" .
`
};

$: triples = [];

onMount (() => {
  console.log('rdflib...');
  const g = rdflibx.graph();
  const store = rdflibx.parse(rdf.body, g, rdf.uri, rdf.mimeType);

  g.match().forEach(quad => {
      triples.push(quad);
      triples = triples;
  });
});

</script>

<div><h2>rdflib</h2>
<ul>
	{#each triples as triple, i}
		<li>{triple}</li>
	{/each}
</ul>
</div>