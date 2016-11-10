# M101J: MongoDB for Java Developers

[![N|Solid](https://endijs.com/wp-content/uploads/2014/04/MongoDB_University_Logo.png)](https://university.mongodb.com/)

### About this course
Learn everything you need to know to get started building a MongoDB-based app. This course will go over basic installation, JSON, schema design, querying, insertion of data, indexing and working with the Java driver. In the course, you will build a blogging platform, backed by MongoDB. 

---------
#### Units 

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
    
#### Quizzes

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





[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)
   
   [qw1]: <https://github.com/josemanuelCRV/MongoDB_M101J/blob/master/README.md#week-1---introduction>
   [hw1]: <https://university.mongodb.com/>
   
   [qw2]: <https://university.mongodb.com/>
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

