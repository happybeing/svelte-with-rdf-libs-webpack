<script>
import fetch from '@rdfjs/fetch';

const label = 'http://www.w3.org/2000/01/rdf-schema#label'

console.log('Loading Rdfjs');
fetch('http://www.w3.org/2000/01/rdf-schema')
  .then(res => res.dataset())
  .then(dataset => {
    for (const quad of dataset) {
      if (quad.predicate.value === label) {
        console.log(`${quad.subject.value}: ${quad.object.value}`)
      }
    }
  }).catch(err => console.error(err));
</script>

<div><h2>Rdfjs OK</h2>
</div>