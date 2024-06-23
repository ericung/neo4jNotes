# neo4jNotes

$FRIENDS$ in the space of $PERSON$

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

$MOVIES$ in the space of $PERSON$

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

$FRIENDS \cup MOVIES = PERSONS$

Relations $KNOWS \subseteq FRIENDS \subseteq PERSON$ and $ACTED\textunderscore IN \subseteq MOVIES \subseteq PERSON$

As opposed to entity tables in SQL

$KNOWS$ has the columns since and rating

```cypher
MATCH (e:Person)-[:KNOWS]-(friends)
WHERE e.name = 'Emil' RETURN e, friends
```

$e \in PERSON$ such that name of e is Emil

$friends \in KNOWS \subseteq PERSON$
