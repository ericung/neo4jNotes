# neo4jNotes

The intention to using neo4j is to write cleaner proofs but not so much as to make it so unambiguous that it loses intuition.

$FRIENDS$ in the space of $EDGES \in PERSON$

```cypher
CREATE (ee:Person {name: 'Emil', from: 'Sweden', kloutScore: 99})
```

```cypher
CREATE (js:Person { name: 'Johan', from: 'Sweden', learn: 'surfing' }),
(ir:Person { name: 'Ian', from: 'England', title: 'author' }),
(rvb:Person { name: 'Rik', from: 'Belgium', pet: 'Orval' }),
(ally:Person { name: 'Allison', from: 'California', hobby: 'surfing' }),
(ee)-[:KNOWS {since: 2001}]->(js),(ee)-[:KNOWS {rating: 5}]->(ir),
(js)-[:KNOWS]->(ir),(js)-[:KNOWS]->(rvb),
(ir)-[:KNOWS]->(js),(ir)-[:KNOWS]->(ally),
(rvb)-[:KNOWS]->(ally)
```

$MOVIES$ in the space of $EDGES \in PERSON$

```cypher
CREATE
  (keanu:Person {name: 'Keanu Reever'}),
  (laurence:Person {name: 'Laurence Fishburne'}),
  (carrie:Person {name: 'Carrie-Anne Moss'}),
  (tom:Person {name: 'Tom Hanks'}),
  (theMatrix:Movie {title: 'The Matrix'}),
  (keanu)-[:ACTED_IN]->(theMatrix),
  (laurence)-[:ACTED_IN]->(theMatrix),
  (carrie)-[:ACTED_IN]->(theMatrix)
```

$FRIENDS \cap MOVIES = \emptyset $

$FRIENDS \cup MOVIES = EDGES \in PERSONS$

Relations $KNOWS \in FRIENDS \subseteq PERSON$ and $ACTED\textunderscore IN \in MOVIES \subseteq PERSON$

As opposed to entity tables in SQL

$KNOWS$ has the columns since and rating

```cypher
MATCH (e:Person)-[:KNOWS]-(friends)
WHERE e.name = 'Emil' RETURN e, friends
```

$e \in PERSON$ such that name of e is Emil

$FRIENDS \in KNOWS \subseteq PERSON$

$FRIENDS$ and $MOVIES$ form the basis of Persons.
