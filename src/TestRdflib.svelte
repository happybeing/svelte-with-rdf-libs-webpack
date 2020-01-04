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

console.log('Loading rdflib');
// TODO BUG: returns undefined
const store = rdflibx.parse(rdf.body, rdflibx.graph(), rdf.uri, rdf.mimeType);
console.log(store);

</script>

<div><h2>Rdflib OK</h2>
</div>