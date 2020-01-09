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

console.log('Comunica...');
// The query engine and its source
const queryEngine = new ComunicaEngine('https://ruben.verborgh.org/profile/');

console.log('LDFlex...');
// The object that can create new paths
const path = new PathFactory({ context, queryEngine });

const ruben = path.create({ subject: namedNode('https://ruben.verborgh.org/profile/#me') });
showPerson(ruben);

async function showPerson(person) {
  console.log(`This person is ${await person.name}`);

  console.log(`${await person.givenName} is interested in:`);
  for await (const name of person.interest.label)
    console.log(`- ${name}`);

  console.log(`${await person.givenName} is friends with:`);
  for await (const name of person.friends.givenName)
    console.log(`- ${name}`);
}

</script>

<div><h2>Comunica and LDFlex</h2>
{#await ruben}
  <p>Waiting for person...</p>
{:then result}
  {#await result.name}
    <p>Waiting for person.name...</p>
  {:then name}
    <p>person: {result} and person.name: {name}</p>
  {:catch error}
    <p style="color: red">{error.message}</p>
  {/await}
{:catch error}
  <p style="color: red">{error.message}</p>
{/await}

</div>