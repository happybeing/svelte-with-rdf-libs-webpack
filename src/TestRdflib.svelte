<script>
// import * as rdflibx from 'rdflib';
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

console.log('rdflib...');

let newTriples = [];
$: triples = newTriples.map(d => Object.create(d));

const g = rdflibx.graph();
const store = rdflibx.parse(rdf.body, g, rdf.uri, rdf.mimeType);

g.match().forEach(quad => {
    newTriples.push(quad);
});

</script>

<div><h2>rdflib</h2>
<ul>
	{#each triples as triple, i}
		<li>{triple}</li>
	{/each}
</ul>
</div>