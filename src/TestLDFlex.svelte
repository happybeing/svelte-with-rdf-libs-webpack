<script>
const { PathFactory } = require('ldflex');

// Comunica is needed for SPARQL queries
const { default: ComunicaEngine } = require('ldflex-comunica');
const { namedNode } = require('@rdfjs/data-model');

// The JSON-LD context for resolving properties
const context = {
  "@context": {
    "@vocab": "http://xmlns.com/foaf/0.1/",
    "friends": "knows",
    "label": "http://www.w3.org/2000/01/rdf-schema#label",
  }
};

console.log('Loading Comunica');
// The query engine and its source
const queryEngine = new ComunicaEngine('https://ruben.verborgh.org/profile/');

console.log('Loading LDFlex');
// The object that can create new paths
const path = new PathFactory({ context, queryEngine });

</script>

<div><h2>Rdflib OK</h2>
</div>