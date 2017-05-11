# pinto

### Context

Pinto is an [NCATS Translator Knowledge Beacon](https://github.com/STARInformatics/translator-knowledge-beacon/tree/master/api).

It broadcasts the availability of concepts to the federated Translator knowledgebase.

It wraps a [chem2bio2rdf](http://cheminfov.informatics.indiana.edu:8080/c2b2r/) data service.

The underlying service is the [RENCI Stars Blazegraph](http://stars-blazegraph.renci.org/blazegraph/#query) instance.

### Pinto Challenges

1. Pinto is a fork of Garbanzo, a knowledge beacon wrapping Wikidata. While Wikidata has significant ontological
structure, especially around the notion of concepts, chem2bio2rdf is an earlier linked data effort and has very little
structure representing conceptual abstractions. So for the beacon to tell a client what concepts it is able to serve, it
must query a number of different structures, and those structures must be addressed independently in the beacon implementation.

2. Similarly related to this low level of structure, the data is highly denormalized. So, to know where the string "Aspirin" occurs,
there's not one rdfs:label that's referenced from lots of places. Neither are all strings predicates of an rdfs:label. Many are 
targets of an arbitrary identifier. Again, to answer where that string occurs requires manually addressing a number of locations in
the data selected by a relatively manual, curatorial process.

### Usage
```
pip install -r requirements.txt
python app.py
```
Then go to the Swagger [endpoint](http://localhost:5000/#!/concepts/get_get_concepts).
