<script>
// 40K overhead:
// import * as readTtl from "@graphy/content.ttl.read";
const readTtl = require('@graphy/content.ttl.read');

console.log('Graphy...');

let newTriples = [];
$: triples = newTriples.map(d => Object.create(d));

readTtl(`
    @prefix foaf: <http://xmlns.com/foaf/0.1/> .

    <#spiderman> a foaf:Person ;
        foaf:name "Spiderman" .
`, {
    data(y_quad) {
        console.log(JSON.stringify(y_quad));
        newTriples.push(y_quad);
        newTriples = newTriples;
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