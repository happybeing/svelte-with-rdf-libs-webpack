<script>
// 40K overhead:
// import * as readTtl from "@graphy/content.ttl.read";
const readTtl = require('@graphy/content.ttl.read');

console.log('Graphy...');

$: triples = [];

readTtl(`
    @prefix foaf: <http://xmlns.com/foaf/0.1/> .

    <#spiderman> a foaf:Person ;
        foaf:name "Spiderman" .
`, {
    data(y_quad) {
        console.log(JSON.stringify(y_quad));
        triples.push(y_quad);
        triples = triples;
    },

    eof(h_prefixes) {
        console.log('done!');
    },
})

</script>

<div><h2>Graphy</h2>
<ul>
	{#each triples as triple, i}
		<li>{triple}</li>
	{/each}
</ul>
</div>