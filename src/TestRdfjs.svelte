<script>
import fetch from '@rdfjs/fetch';

const label = 'http://www.w3.org/2000/01/rdf-schema#label'

console.log('Rdfjs...');
$: triples = [];

const formats = require('@rdfjs/formats-common')
const Readable = require('stream').Readable

const input = new Readable({
  read: () => {
    input.push(`
    @prefix foaf: <http://xmlns.com/foaf/0.1/> .

    <#spiderman> a foaf:Person ;
        foaf:name "Spiderman" .
`)
    input.push(null)
  }
})

const output = formats.parsers.import('text/turtle', input)

output.on('data', quad => {
  console.log(`HEY quad: ${quad.subject.value} - ${quad.predicate.value} - ${quad.object.value}`)
  triples.push(quad);
  triples = triples;
})

output.on('prefix', (prefix, ns) => {
  console.log(`prefix: ${prefix} ${ns.value}`)
})

let newFetchedTriples = [];
$: fetchedTriples = newFetchedTriples.map(d => Object.create(d));

console.log('Rdfjs using fetch...')
fetch('http://www.w3.org/2000/01/rdf-schema')
  .then(res => res.dataset())
  .then(dataset => {
    for (const quad of dataset) {
      newFetchedTriples.push(quad);
      newFetchedTriples = newFetchedTriples;
      if (quad.predicate.value === label) {
        console.log(`${quad.subject.value}: ${quad.object.value}`)
      }
    }
  }).catch(err => console.error(err));

</script>

<div><h2>Rdfjs</h2>
<p>triples...</p>
<ul>
	{#each triples as triple, i}
		<li>{'<' + triple.subject.value + '> <' + triple.predicate.value + '> <' + triple.object.value + '> .'}</li>
	{/each}
</ul>
<p>fetch...</p>
<ul>
	{#each fetchedTriples as triple, i}
		<li>{'<' + triple.subject.value + '> <' + triple.predicate.value + '> <' + triple.object.value + '> .'}</li>
	{/each}
</ul>
</div>