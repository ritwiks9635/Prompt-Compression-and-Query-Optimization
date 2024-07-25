# **💬Prompt-Compression-and-Query-Optimization💬**

![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQVMQKfGmrOkpHslnOh6B-3ML4s0uKONhxmkA&usqp=CAU)

## **What Is Prompt Compression?**
Prompt compression is a technique used in natural language processing (NLP) to optimize the inputs given to LLMs by reducing their length without significantly altering the quality and relevance of the output. This optimization is crucial due to the impact the number of tokens in queries has on LLM performance.

Tokens are the basic units of text LLMs use, representing words or subwords depending on the language model's tokenizer. Reducing the number of tokens in a prompt is beneficial and sometimes necessary for several reasons:

- **Token limit constraints:** LLMs have a maximum token limit for inputs. Exceeding this limit can truncate important information, reducing the output's clarity and the model's effectiveness.
  
- **Processing efficiency and cost reduction:** Fewer tokens mean faster processing times and lower costs.
  
- **Improved response relevance:** A human-readable prompt does not always mean a good prompt. Sometimes the prompts we think are good and informative carry unimportant information for the LLMs, such as stop words ("a," "the," "is," etc.).
  
Prompt compression reduces the token number by employing strategies such as removing redundant information, summarizing key points, or utilizing specialized algorithms to distill the essence of a prompt while minimizing its token count.

## **When Should We Use Prompt Compression?**

Let’s explore the scenarios where we could use prompt compression.

**Advanced prompt engineering techniques**

Techniques like chain-of-thought prompting, while highly effective, often result in lengthy prompts that can reach thousands of tokens. This increases processing times and costs and may exceed the token limits of certain models.

Prompt compression mitigates these issues by reducing the token count while preserving the prompt's effectiveness.

**Retrieval-augmented generation (RAG) pipelines**

RAG pipelines combine information retrieval with text generation and are often used in specialized chatbots and other applications where contextual understanding is critical. These pipelines frequently need extensive conversation histories or retrieved documents as prompts, leading to high token counts and increased expenses.

Prompt compression is essential in such cases to maintain essential context while minimizing costs.

**Applicability and limitations of prompt compression**

It's important to note that prompt compression is not a universal solution and should be used judiciously. For instance, assistant models like ChatGPT, designed for conversational contexts, may not benefit from aggressive prompt compression.

These models often do not charge per token and have integrated chat summarization and memory features to manage conversation history effectively, making compression redundant.

It’s also important to note that even when working with models that charge per token, excessive compression could lead to a loss of nuance or important details. Striking the right balance between reducing size and maintaining the integrity of the prompt’s meaning is key.

## **How Does Prompt Compression Work?**
Prompt compression techniques can be categorized into three main methods: knowledge distillation, encoding, and filtering. Each technique leverages different strengths to optimize the length and efficiency of prompts for LLMs.

While we’ll be talking about each of these techniques, you can find a more comprehensive approach in this paper: Efficient Prompting Methods for Large Language Models: A Survey. Throughout this article, I’ll be referring to this paper as the “survey paper.”

**Knowledge distillation**

Knowledge distillation is a technique in the field of machine learning, first introduced by Hinton et al. (2015), where a smaller, simpler model (the student) is trained to replicate the behavior of a larger, more complex model (the teacher).

This technique was initially developed to address the computational challenges of training an ensemble of models. In the context of prompt engineering, knowledge distillation can be used to compress the prompt instead of the model.

This is achieved by learning how to compress the hard prompts within LLMs through soft prompt tuning. For detailed insights, refer to sections 3.1 and appendix A.1.1 of the survey paper.

**Encoding**

Encoding methods transform input texts into vectors, reducing prompt length without losing critical information. These vectors capture the prompts' essential meaning, allowing LLMs to process shorter inputs efficiently.

Interestingly, LLMs are proficient in other languages like Base64, which can be utilized in encoding to reduce the token size of the prompt. For example, the prompt “Translate the following text to French: Hello, how are you?” encoded in Base64 is “VHJhbnNsYXRlIHRoZSBmb2xsb3dpbmcgdGV4dCB0byBGcmVuY2g6ICdIZWxsbywgaG93IGFyZSB5b3UnPw==”. You can try prompting your favorite LLM to test it out!

Surprisingly, some encoding techniques are also used for model jailbreaking, which involves manipulating LLM to bypass its safety mechanisms. For more details on encoding methods, see sections 3.2 and appendix A.1.2 of the survey paper.

**Filtering**

While the previous two methods try to compress the whole prompt, filtering techniques focus on eliminating unnecessary parts to enhance the efficiency of LLMs.

Filtering techniques evaluate the information content of different parts of a prompt and remove redundant information since not all information in the prompt is beneficial for LLMs. This can be done at various levels, such as sentences, phrases, or tokens.

The goal is to retain only the most relevant parts of the prompt. In the paper Selective Context by Li et al. (2023), researchers use self-information metrics to filter redundant information. In the paper LLMLingua: Compressing Prompts for Accelerated Inference of Large Language Models, researchers from Microsoft refine prompts into key components and dynamically adjust compression ratios for each part. For further reading, refer to sections 3.3 and appendix A.1.3 of the survey paper.lter redundant information. In the paper LLMLingua: Compressing Prompts for Accelerated Inference of Large Language Models, researchers from Microsoft refine prompts into key components and dynamically adjust compression ratios for each part. For further reading, refer to sections 3.3 and appendix A.1.3 of the survey paper.


##**Query optimization**

**Query optimization** is a technique used in database management systems (DBMS) to determine the most efficient way to execute a query. The goal is to reduce the time it takes to process a query and minimize the resources required to do so. 

Here are some techniques used in query optimization:

- Join optimization: Arranges joins in different orders and estimates the cost of each order before selecting the cheapest option that produces the same result as the original order
  
- Index selection: Using the right indexes can speed up queries and improve application performance
  
- Denormalization: Adding duplicate data to tables to avoid costly joins in relational databases
  
- Avoiding queries inside a loop: Running queries inside a loop can slow down execution time
  
- Optimizing database design: Ensuring tables are normalized and indexes are used effectively
  
- Limiting the number of rows retrieved: Using the LIMIT and OFFSET clauses to paginate query results can help if you only need a small subset of the data
  
Some query optimization tools include:

- EverSQL: Improves database server performance by making queries run faster
  
- SolarWinds Database Performance Analyzer: Combines performance analysis and query optimization for MySQL


## **What is MongoDB?**

![](https://miro.medium.com/v2/resize:fit:512/1*doAg1_fMQKWFoub-6gwUiQ.png)

MongoDB is an open source NoSQL database management program. NoSQL (Not only SQL) is used as an alternative to traditional relational databases. NoSQL databases are quite useful for working with large sets of distributed data. MongoDB is a tool that can manage document-oriented information, store or retrieve information.

MongoDB is used for high-volume data storage, helping organizations store large amounts of data while still performing rapidly. Organizations also use MongoDB for its ad-hoc queries, indexing, load balancing, aggregation, server-side JavaScript execution and other features.

Structured Query Language (SQL) is a standardized programming language that is used to manage relational databases. SQL normalizes data as schemas and tables, and every table has a fixed structure.

Instead of using tables and rows as in relational databases, as a NoSQL database, the MongoDB architecture is made up of collections and documents. Documents are made up of Key-value pairs -- MongoDB's basic unit of data. Collections, the equivalent of SQL tables, contain document sets. MongoDB offers support for many programming languages, such as C, C++, C#, Go, Java, Python, Ruby and Swift.

**How does MongoDB work?**


MongoDB environments provide users with a server to create databases with MongoDB. MongoDB stores data as records that are made up of collections and documents.

Documents contain the data the user wants to store in the MongoDB database. Documents are composed of field and value pairs. They are the basic unit of data in MongoDB. The documents are similar to JavaScript Object Notation (JSON) but use a variant called Binary JSON (BSON). The benefit of using BSON is that it accommodates more data types. The fields in these documents are like the columns in a relational database. Values contained can be a variety of data types, including other documents, arrays and arrays of documents, according to the MongoDB user manual. Documents will also incorporate a primary key as a unique identifier. A document's structure is changed by adding or deleting new or existing fields.

Sets of documents are called collections, which function as the equivalent of relational database tables. Collections can contain any type of data, but the restriction is the data in a collection cannot be spread across different databases. Users of MongoDB can create multiple databases with multiple collections.

The mongo shell is a standard component of the open-source distributions of MongoDB. Once MongoDB is installed, users connect the mongo shell to their running MongoDB instances. The mongo shell acts as an interactive JavaScript interface to MongoDB, which allows users to query or update data and conduct administrative operations.

A binary representation of JSON-like documents is provided by the BSON document storage and data interchange format. Automatic sharding is another key feature that enables data in a MongoDB collection to be distributed across multiple systems for horizontal scalability, as data volumes and throughput requirements increase.

The NoSQL DBMS uses a single master architecture for data consistency, with secondary databases that maintain copies of the primary database. Operations are automatically replicated to those secondary databases for automatic failover.

MongoDB supporting technologies.MongoDB supporting technologies include MongoDB Stich, Atlas Global Clusters, and Mobile, along with newer MongoDB updates.

**Why is MongoDB used?**


An organization might want to use MongoDB for the following:

Storage. MongoDB can store large structured and unstructured data volumes and is scalable vertically and horizontally. Indexes are used to improve search performance. Searches are also done by field, range and expression queries.
Data integration. This integrates data for applications, including for hybrid and multi-cloud applications.
Complex data structures descriptions. Document databases enable the embedding of documents to describe nested structures (a structure within a structure) and can tolerate variations in data.
Load balancing. MongoDB can be used to run over multiple servers.

**Features of MongoDB**


Features of MongoDB include the following:

Replication. A replica set is two or more MongoDB instances used to provide high availability. Replica sets are made of primary and secondary servers. The primary MongoDB server performs all the read and write operations, while the secondary replica keeps a copy of the data. If a primary replica fails, the secondary replica is then used.
Scalability. MongoDB supports vertical and horizontal scaling. Vertical scaling works by adding more power to an existing machine, while horizontal scaling works by adding more machines to a user's resources.
Load balancing. MongoDB handles load balancing without the need for a separate, dedicated load balancer, through either vertical or horizontal scaling.
Schema-less. MongoDB is a schema-less database, which means the database can manage data without the need for a blueprint.
Document. Data in MongoDB is stored in documents with key-value pairs instead of rows and columns, which makes the data more flexible when compared to SQL databases.


**Advantages of MongoDB**


MongoDB offers several potential benefits:

Schema-less. Like other NoSQL databases, MongoDB doesn't require predefined schemas. It stores any type of data. This gives users the flexibility to create any number of fields in a document, making it easier to scale MongoDB databases compared to relational databases.
Document-oriented. One of the advantages of using documents is that these objects map to native data types in several programming languages., Having embedded documents also reduces the need for database joins, which can lower costs.
Scalability. A core function of MongoDB is its horizontal scalability, which makes it a useful database for companies running big data applications. In addition, sharding lets the database distribute data across a cluster of machines. MongoDB also supports the creation of zones of data based on a shard key.
Third-party support. MongoDB supports several storage engines and provides pluggable storage engine APIs that let third parties develop their own storage engines for MongoDB.
Aggregation. The DBMS also has built-in aggregation capabilities, which lets users run MapReduce code directly on the database rather than running MapReduce on Hadoop. MongoDB also includes its own file system called GridFS, akin to the Hadoop Distributed File System. The use of the file system is primarily for storing files larger than BSON's size limit of 16 MB per document. These similarities let MongoDB be used instead of Hadoop, though the database software does integrate with Hadoop, Spark and other data processing frameworks.


**Disadvantages of MongoDB**


Though there are some valuable benefits to MongoDB, there are some downsides to it as well.

Continuity. With its automatic failover strategy, a user sets up just one master node in a MongoDB cluster. If the master fails, another node will automatically convert to the new master. This switch promises continuity, but it isn't instantaneous -- it can take up to a minute. By comparison, the Cassandra NoSQL database supports multiple master nodes. If one master goes down, another is standing by, creating a highly available database infrastructure.
Write limits. MongoDB's single master node also limits how fast data can be written to the database. Data writes must be recorded on the master, and writing new information to the database is limited by the capacity of that master node.
Data consistency. MongoDB doesn't provide full referential integrity through the use of foreign-key constraints, which could affect data consistency.
Security. In addition, user authentication isn't enabled by default in MongoDB databases. However, malicious hackers have targeted large numbers of unsecured MongoDB systems in attacks, which led to the addition of a default setting that blocks networked connections to databases if they haven't been configured by a database administrator.
