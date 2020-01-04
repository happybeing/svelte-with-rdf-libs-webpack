<script>
// 40K overhead:
// import * as readTtl from "@graphy/content.ttl.read";
const readTtl = require('@graphy/content.ttl.read');

console.log('Loading Graphy');
readTtl(`
    @prefix foaf: <http://xmlns.com/foaf/0.1/> .

    <#spiderman> a foaf:Person ;
        foaf:name "Spiderman" .
`, {
    // whew! simplified inline events style  ;)
    data(y_quad) {
        console.dir(y_quad);
    },

    eof(h_prefixes) {
        console.log('done!');
    },
})


// const rdf = '';

// try {
//   readTtl(rdf, {
//       // whew! simplified inline events style  ;)
//       data(y_quad) {
//           console.dir(y_quad);
//       },

//       eof(h_prefixes) {
//           console.log('done!');
//       },
//     });

// } catch (err) {
//   console.log(err);
// }

</script>

<div><h2>Graphy OK</h2>
</div>