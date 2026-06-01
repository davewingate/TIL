# Neo4j

## [Neo4j Fundamentals](https://graphacademy.neo4j.com/courses/neo4j-fundamentals/)

### Key Concepts
Neo4j databases are labeled property graphs.  
Key concepts: Nodes, Relationships, Labels & Properties.

Labels describe the "type" of a Node.  It's possible for nodes to have multiple labels.

All relationships have a type and a direction.

Properties are named key/value pairs associated with either nodes or relationships.  All property values have a data type.

Graph databases are most helpful when the relationships amond data elements are as important as the data elements themselves.

### Use Cases
Graph databases facilitate efficient querying or complex relationships.  The query time is in purportion to the number of queried relationships, regardless of the over all data size.  They shine over traditional relational databases when, for example, working with relationships of unknown depth.

### Cypher

#### Finding Nodes
Find the person named 'Tom Hanks'.

```cypher
MATCH (n:Person)
WHERE n.name = 'Tom Hanks'
RETURN n
```

... or ...

```cypher
MATCH (n:Person {name: 'Tom Hanks'}) RETURN n
```

#### Finding Nodes with Relationships
Find people who acted in 'Toy Story'.

```cypher
MATCH (m:Movie)<-[r:ACTED_IN]-(p:Person)
WHERE m.title = 'Toy Story'
RETURN m, r, p
```

... or ...

```cypher
MATCH (m:Movie {title: 'Toy Story'}) <-[r:ACTED_IN]- (p:Person) RETURN m, r, p
```

#### Returning Tabular Data
Fetch a table of title and roles for movies that 'Emma Stone' has acted in.

```cypher
MATCH (p:Person {name: 'Emma Stone'}) -[a:ACTED_IN]-> (m:Movie) 
RETURN m.title, a.role
```

#### Repeated Node Types
Which directors have directed 'Tom Hanks'.

```cypher
MATCH (p:Person) -[rd:DIRECTED]-> (m:Movie) <-[ra:ACTED_IN]- (p2:Person {name: 'Tom Hanks'}) 
RETURN p.name as director, m.title
```

#### Creating Node and Relationships
Upsert two nodes and their relationship.

```cypher
MERGE (m:Movie {title: "Arthur the King"})
MERGE (u:User {name: "Adam"})
MERGE (u)-[r:RATED {rating: 5}]->(m)
RETURN u, r, m
```

## [Cypher Fundamentals](https://graphacademy.neo4j.com/courses/cypher-fundamentals)
 - In Cypher, labels, property keys, and variables are case-sensitive. Cypher keywords are not case-sensitive.
 - Using `WHERE` to filter your queries is very powerful because you can add more logic to your `WHERE` clause -- e.g. `MATCH (p:Person) WHERE p.name = 'Tom Hanks' OR p.name = 'Rita Wilson' RETURN p`.
 


## Tutorials
 - [Intro to Graph Databases Series](https://www.youtube.com/playlist?list=PL9Hl4pk2FsvWM9GWaguRhlCQ-pa-ERd4U)
 - [Neo4j Fundamentals](https://graphacademy.neo4j.com/courses/neo4j-fundamentals/)
 - [Cypher Fundamentals](https://graphacademy.neo4j.com/courses/cypher-fundamentals)
 - [Getting Started with Aura Free Tier](https://www.youtube.com/watch?v=1Ee242FDFcc)