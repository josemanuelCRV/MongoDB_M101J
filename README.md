# M101J: MongoDB for Java Developers

[![N|Solid](https://endijs.com/wp-content/uploads/2014/04/MongoDB_University_Logo.png)](https://university.mongodb.com/)

### About this course
Learn everything you need to know to get started building a MongoDB-based app. This course will go over basic installation, JSON, schema design, querying, insertion of data, indexing and working with the Java driver. In the course, you will build a blogging platform, backed by MongoDB. 

---------
### Units 

- **Week 1 - Introduction:**  Overview, Design Goals, the Mongo Shell, JSON Intro, Installing Tools, Overview of Blog Project. Maven, Spark and Freemarker Intro.
    - *[Quizzes][qw1]* 
    - *[Homeworks][hw1]*   

- **Week 2 - CRUD:** Mongo Shell, Query Operators, Update Operators and a Few Commands.
    - *[Quizzes][qw2]* 
    - *[Homeworks][hw2]* 
    
- **Week 3 - Schema Design:** Patterns, Case Studies & Tradeoffs
    - *[Quizzes][qw3]* 
    - *[Homeworks][hw3]*

- **Week 4 - Performance:** Using Indexes, Monitoring And Understanding Performance. Performance In Sharded Environments.
    - *[Quizzes][qw4]* 
    - *[Homeworks][hw4]*
    
- **Week 5 - Aggregation Framework:** Goals, The Use Of The Pipeline, Comparison With SQL Facilities.
    - *[Quizzes][qw5]* 
    - *[Homeworks][hw5]*

- **Week 6 - Application Engineering:** Drivers, Impact Of Replication And Sharding On Design And Development..
    - *[Quizzes][qw6]* 
    - *[Homeworks][hw6]*

- **Week 7 - Case Studies:** Interview with Charity Majors, Parse and interview with Ryan Bubinski, Codecademy.
    - *[Quizzes][qw7]* 
    - *[Homeworks][hw7]*


- Final Exam: Final Exam
Final Project In this project we put together everything we've covered through the course to build a complete application backed by MongoDB. 

----
    
### Quizzes

#### Week 1 - Introduction:  

Quiz: *`welcome to M101J:`*  
    *What counts toward your final grade in the class?* 
-   [ ] Quizzes
-   [x] Homeworks
-   [x] Final Exam
-   [ ] Class Participation

Quiz: *`JSON:`*  
*Which of the following value types are defined by the JSON spec?*

-   [x] object
-   [x] array
-   [ ] date
-   [x] string
-   [ ] integer
-   [x] number

Quiz: *`BSON:`*  
*True or false? BSON plays the role of a canonical (i.e., "unique") representation of documents shared across all drivers and tools.*

-   [x] True
-   [ ] False

Quiz: *`Blog in Relational Tables:`*  
*let's assume that our blog can be modeled with the following relational tables:*

    authors:
        author_id,
        name,
        email,
        password
    
    posts:
        post_id,
        author_id
        title,
        body,
        publication_date
    
    comments:
        comment_id,
        name,
        email,
        comment_text
    
    post_comments:
        post_id,
        comment_id 
        
    tags
        tag_id
        name
    
    post_tags
        post_id
        tag_id  
        
In order to display a blog post with its comments and tags, how many tables will need to be accessed?

-   [ ] 2
-   [ ] 3
-   [ ] 5
-   [x] 6

Quiz: *`Blog in Documents:`*  
*Given the document schema that we proposed for the blog, how many collections would we need to access to display the blog home page?*
-   [ ] 0
-   [x] 1
-   [ ] 2
-   [ ] 4


Quiz: *`Introduction to Schema Design:`*  
*In which scenario is it impossible to embed data within a document (you must put the data in a separate collection)?*
-   [ ] The data would be duplicated across multiple objects within a collection.
-   [ ] You need an index on the data element.
-   [x] The embedded data could exceed the 16MB document limit within MongoDB.
-   [ ] The data is not isomorphic.




----

#### Week 2 - CRUD:  

Quiz: *`Java Driver: Representing Documents:`*  
    *How would you create a document using the Java driver with this JSON structure:* 

````
{
   "_id" : "user1",
   "interests" : [ "basketball", "drumming"]
}
````
-   [ ] new HashMap().put("_id", "user1").put(Arrays.asList("basketball", "drumming"));
-   [ ] new Document("_id", "user1").append("interests", "basketball", "drumming");
-   [ ] new DBObject("_id", "user1").append("interests", Arrays.asList("basketball", "drumming"));
-   [x] new Document("_id", "user1").append("interests", Arrays.asList("basketball", "drumming"));


Quiz: *`Java Driver: Insert`*  
    *Do you expect the second insert below to succeed?* 
    
````
MongoClient client = new MongoClient();
MongoDatabase database = client.getDatabase("school");
MongoCollection<Document> people = database.getCollection("people");

Document doc = new Document("name", "Andrew Erlichson").append("company", "10gen");

people.insertOne(doc);      // first insert
doc.remove("_id");             // remove the _id key
people.insertOne(doc);      // second insert 
````

-   [ ] No, because the _id will be a duplicate in the collection.
-   [ ] No because the remove call will remove the entire document.
-   [x] Yes, because the remove call will remove the _id field added by the driver in the first insert.
-   [ ] Yes, because the driver always adds a unique _id field on insert.


Quiz: *`Java Driver: Find, FindOne, and Count`*  
    *In the following code snippet:* 

````    
MongoClient client = new MongoClient();
MongoDatabase database = client.getDatabase("school");
MongoCollection<Document> people = database.getCollection("people");
Document doc;
// xxxx
System.out.println(doc);
````

*Please enter the simplest one line of Java code that would be needed in place of // xxxx to make it print one document from the people collection.*     
````
doc=people.find().first();  
````

Quiz: *`Java Driver: Querying with a filter`*  
    *Given a collection named "scores" of documents with two fields -- type and score -- what is the correct line of code to find all documents where type is "quiz" and score is greater than 20 and less than 90. Select all that apply.* 

-   [ ] scores.find(new Document("score", new Document("$gt", 20).append("$lt", 90))
-   [x] scores.find(new Document("type", "quiz").append("score", new Document("$gt", 20).append("$lt", 90)))
-   [ ] scores.find(new Document("type", "quiz").append("$gt", new Document("score", 20)).append("$lt", new Document("score", 90)))
-   [x] scores.find(Filters.and(Filters.eq("type", "quiz"), Filters.gt("score", 20), Filters.lt("score", 90)))


Quiz: *`Java Driver: Querying with a Projection`*  
    *Given a variable named "students" of type MongoCollection<Document>, which of the following lines of code could be used to find all documents in the collection, retrieving only the "phoneNumber" field.* 

-   [ ] students.find(new Document("phoneNumber", 1).append("_id", 0))
-   [x] students.find().projection(Projections.fields(Projections.include("phoneNumber"), Projections.excludeId())
-   [ ] students.find(new Document("phoneNumber", 1))
-   [x] students.find().projection(new Document("phoneNumber", 1).append("_id", 0))


Quiz: *`Java Driver: Querying with Sort, Skip and Limit`*  
    *Supposed you had the following documents in a collection named things.* 
````
{ "_id" : 0, "value" : 10 }
{ "_id" : 1, "value" : 5 }
{ "_id" : 2, "value" : 7 }
{ "_id" : 3, "value" : 20 }
````
    *If you performed the following query in the Java driver:*

````
collection.find().sort(new Document("value", -1)).skip(2).limit(1)
````
    *which document would be returned?* 

-   [ ] The document with _id=0
-   [x] The document with _id=1
-   [ ] The document with _id=2
-   [x] The document with _id=3



Quiz: *`Java Driver: Update and Replace`*  
    *In the following code fragment, what is the Java expression in place of xxxx that will set the field "examiner" to the value "Jones" for the document with _id of 1. Please use the $set operator.
    
````
# update using $set
scores.updateOne(new Document("_id", 1), xxxx);
````

````
new Document("$set", new Document("examiner", "Jones"))
````

Quiz: *`Java Driver: Delete`*  
    *Given a collection with the following documents, how many will be affected by the following deletion statement?*
    
````
{ _id: 0, x: 1 }
{ _id: 1, x: 1 }
{ _id: 2, x: 1 }
{ _id: 3, x: 2 }
{ _id: 4, x: 2 }
````

````
collection.deleteOne(Filters.eq("x", 1))
````

-   [ ] 0
-   [x] 1
-   [ ] 2
-   [ ] 3






[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)
   
   [qw1]: <https://github.com/josemanuelCRV/MongoDB_M101J/blob/master/README.md#week-1---introduction>
   [hw1]: <https://university.mongodb.com/>
   
   [qw2]: <https://github.com/josemanuelCRV/MongoDB_M101J/blob/master/README.md#week-2---crud>
   [hw2]: <https://university.mongodb.com/>
   
   [qw3]: <https://university.mongodb.com/>
   [hw3]: <https://university.mongodb.com/>
   
   [qw4]: <https://university.mongodb.com/>
   [hw4]: <https://university.mongodb.com/>
   
   [qw5]: <https://university.mongodb.com/>
   [hw5]: <https://university.mongodb.com/>
   
   [qw6]: <https://university.mongodb.com/>
   [hw6]: <https://university.mongodb.com/>
   
   [qw7]: <https://university.mongodb.com/>
   [hw7]: <https://university.mongodb.com/>

   [1]: https://university.mongodb.com

