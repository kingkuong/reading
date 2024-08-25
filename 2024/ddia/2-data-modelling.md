# Data modelling

Application developers need to think about data modelling

The point of data modelling is to hide abstraction between different layers of data. Eg: data between application vs data being transfer via network vs data stored in db

## Relational db vs Document db
    - In relational db, we store using ID, in document db, we store using whole document/object
    - Relational db has strong normalization + joins
    - Document db joins is the responsibility of application developers
    - Document is schema-on-read, relational is schema-on-write, noticable difference is when changing model structure:
        - Document allow the changes to be handled in application code
        - Relational requires a migration, which might have performance costs
    - Locality of data:
        - Document db store all in 1 object, hence data is very local compared to data living in different tables in relational
        - Caveat: shouldn’t do operation that make the object large → performance cost + wasteful
- Many to many relationships
    - Easy in relational/ difficult in document
    - Network model **(*deprecrated*): 1 model has many parents, use of pointers to link different models. Creating an *access* *path* is application developer’s role & it’s complicated, hence changing of model is complicated
    - Relational Model: with use of *foreign key,* now it’s the db role to create access path
    - Document Model: store objects within the parent model, and uses *document reference* (quite similar to relational model in this)

##  Query languages
- Declarative vs imperative:
    - Declarative: describe data pattern (the what)
    - Imperative: specify which step to take in which order (the how)
    - SQL is declarative
- Declarative is:
    - Cleaner to work with
    - Hide implementation details
    - Allow DB to optimize queries, run queries in parallel, switching stuff around when doing query

Eg:
- CSS is declarative
- JS DOM manipulation is imperative

## MapReduce

- MapReduce:
    - Allow to use `map` and `reduce` function
    - Very prominent in MongoDb
- Graph DB: good for many-to-many relationships
    - Eg: Social network, road systems
    - Graph is noSQL
    - Difference between Graph & Network model



# Further learning & references

- How to actually use MongoDb, DynamoDb, Redis, need to understand what’s the difference between those dbs & when to use which
- RabbitMQ + Kafka
- A graph db example
