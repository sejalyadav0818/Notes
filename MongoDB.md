1. **What is MongoDB?**
   - **Answer:** MongoDB is a NoSQL database that stores data in flexible, JSON-like documents.

2. **Explain the concept of BSON in MongoDB.**
   - **Answer:** BSON (Binary JSON) is a binary-encoded serialization of JSON-like documents used in MongoDB.

3. **What is a document in MongoDB?**
   - **Answer:** A document is a set of key-value pairs in MongoDB, similar to a JSON object.

4. **How is data organized in MongoDB?**
   - **Answer:** Data is organized in MongoDB as collections of documents. Collections are analogous to tables in relational databases.

5. **What is a collection in MongoDB?**
   - **Answer:** A collection is a group of MongoDB documents. It is the equivalent of an RDBMS table.

6. **What is the `_id` field in MongoDB?**
   - **Answer:** The `_id` field is a default field in MongoDB documents that uniquely identifies each document in a collection.

7. **Explain the concept of indexing in MongoDB.**
   - **Answer:** Indexing is the process of creating an index on a field to improve query performance.

8. **What is the purpose of the `find` method in MongoDB?**
   - **Answer:** The `find` method is used to query documents in a collection based on specified criteria.

   ```javascript
   // Example
   db.users.find({ age: { $gte: 18 } });
   ```

9. **How can you insert a document in MongoDB?**
   - **Answer:** The `insertOne` or `insertMany` methods are used to insert documents into a collection.

   ```javascript
   // Example
   db.users.insertOne({ name: "John", age: 25 });
   ```

10. **Explain the purpose of the `update` method in MongoDB.**
    - **Answer:** The `update` method is used to modify existing documents in a collection.

    ```javascript
    // Example
    db.users.update({ name: "John" }, { $set: { age: 26 } });
    ```

11. **What is the aggregation framework in MongoDB?**
    - **Answer:** The aggregation framework is a set of operators to perform data transformations and computations on MongoDB documents.

12. **Explain the concept of sharding in MongoDB.**
    - **Answer:** Sharding is the process of distributing data across multiple machines to improve scalability.

13. **What is the purpose of the `remove` method in MongoDB?**
    - **Answer:** The `remove` method is used to delete documents from a collection.

    ```javascript
    // Example
    db.users.remove({ name: "John" });
    ```

14. **How does MongoDB provide support for transactions?**
    - **Answer:** MongoDB supports multi-document transactions starting from version 4.0.

15. **What is the `$addToSet` operator used for in MongoDB?**
    - **Answer:** The `$addToSet` operator adds elements to an array in a document if they do not already exist.

    ```javascript
    // Example
    db.users.update({ name: "John" }, { $addToSet: { hobbies: "Reading" } });
    ```

16. **Explain the concept of replication in MongoDB.**
    - **Answer:** Replication is the process of synchronizing data across multiple servers to ensure data availability and redundancy.

17. **How can you create an index in MongoDB?**
    - **Answer:** The `createIndex` method is used to create an index on a field.

    ```javascript
    // Example
    db.users.createIndex({ name: 1 });
    ```

18. **What is the purpose of the `findOne` method in MongoDB?**
    - **Answer:** The `findOne` method retrieves a single document from a collection based on specified criteria.

    ```javascript
    // Example
    db.users.findOne({ age: { $gte: 18 } });
    ```

19. **Explain the concept of capped collections in MongoDB.**
    - **Answer:** Capped collections are fixed-size collections that maintain insertion order.

20. **How can you query embedded documents in MongoDB?**
    - **Answer:** You can query embedded documents using dot notation.

    ```javascript
    // Example
    db.users.find({ "address.city": "New York" });
    ```

21. **What is the purpose of the `limit` method in MongoDB?**
    - **Answer:** The `limit` method restricts the number of documents returned by a query.

    ```javascript
    // Example
    db.users.find().limit(10);
    ```

22. **Explain the concept of an aggregation pipeline in MongoDB.**
    - **Answer:** An aggregation pipeline is a sequence of stages where each stage transforms the documents.

    ```javascript
    // Example
    db.sales.aggregate([
      { $match: { date: { $gte: new Date("2022-01-01") } } },
      { $group: { _id: "$product", totalSales: { $sum: "$quantity" } } }
    ]);
    ```

23. **What is the purpose of the `distinct` method in MongoDB?**
    - **Answer:** The `distinct` method returns distinct values for a specified field in a collection.

    ```javascript
    // Example
    db.users.distinct("city");
    ```

24. **Explain the concept of a compound index in MongoDB.**
    - **Answer:** A compound index involves multiple fields to improve query performance.

    ```javascript
    // Example
    db.users.createIndex({ name: 1, age: -1 });
    ```

25. **What is the purpose of the `mapReduce` function in MongoDB?**
    - **Answer:** The `mapReduce` function processes large datasets using parallel processing.

26. **Explain the concept of a TTL (Time-To-Live) index in MongoDB.**
    - **Answer:** A TTL index automatically deletes documents from a collection after a specified period.

    ```javascript
    // Example (expiration after 7 days)
    db.logs.createIndex({ createdAt: 1 }, { expireAfterSeconds: 604800 });
    ```

27. **How can you perform case-insensitive queries in MongoDB?**
    - **Answer:** Use the `$regex` operator with the case-insensitive flag.

    ```javascript
    // Example
    db.users.find({ name: { $regex: /^john$/, $options: "i" } });
    ```

28. **Explain the concept of text indexes in MongoDB.**
    - **Answer:** Text indexes support text search on string content.

    ```javascript
    // Example
    db.articles.createIndex({ content: "text" });
    db.articles.find({ $text: { $search: "MongoDB" } });
    ```

29. **What is the purpose of the `explain` method in MongoDB?**
    - **Answer:** The `explain` method provides information on query execution and performance.

    ```javascript
    // Example
    db.users.find({ age: { $gte: 18 } }).explain("executionStats");


    ```

30. **Explain the concept of a covered query in MongoDB.**
    - **Answer:** A covered query is a query where all the fields in the result are covered by an index, minimizing the data scanned.

    ```javascript
    // Example
    db.users.find({ age: { $gte: 18 } }, { name: 1, _id: 0 }).explain("executionStats");
    ```
31. **How does MongoDB handle transactions?**
   - **Answer:** MongoDB supports multi-document transactions starting from version 4.0. Transactions allow you to perform multiple operations on one or more documents atomically.

   ```javascript
   const session = db.getMongo().startSession();
   session.startTransaction();

   try {
     db.users.updateOne({ name: "Alice" }, { $inc: { balance: -50 } }, { session });
     db.transactions.insertOne({ user: "Alice", amount: 50 }, { session });

     session.commitTransaction();
   } catch (error) {
     print(`Transaction aborted: ${error}`);
     session.abortTransaction();
   }
   ```

32. **Explain the concept of the `aggregate` method in MongoDB.**
   - **Answer:** The `aggregate` method is used to perform aggregation operations on a collection. It allows you to transform and process data using a pipeline of stages.

   ```javascript
   // Example: Calculate the average age of users in each city
   db.users.aggregate([
     { $group: { _id: "$city", averageAge: { $avg: "$age" } } }
   ]);
   ```

33. **What is the purpose of the `count` method in MongoDB?**
   - **Answer:** The `count` method is used to count the number of documents in a collection that match a specified query.

   ```javascript
   // Example: Count the number of users with age greater than 25
   db.users.count({ age: { $gt: 25 } });
   ```

34. **Explain the concept of Geospatial Indexing in MongoDB.**
   - **Answer:** Geospatial indexing in MongoDB allows for the efficient querying of spatial data. It supports 2D and 3D indexes for points, lines, and polygons.

   ```javascript
   // Example: Find locations near a specific point
   db.places.createIndex({ location: "2dsphere" });
   db.places.find({
     location: {
       $near: {
         $geometry: { type: "Point", coordinates: [-73.9667, 40.78] },
         $maxDistance: 2000
       }
     }
   });
   ```

35. **What is the purpose of the `explain` method in MongoDB?**
   - **Answer:** The `explain` method provides information about the query execution plan, helping optimize queries and indexes.

   ```javascript
   // Example: Explain the query execution plan
   db.users.find({ age: { $gte: 18 } }).explain("executionStats");
   ```

36. **How can you perform a case-insensitive search in MongoDB?**
   - **Answer:** Use the `$regex` operator with the case-insensitive option.

   ```javascript
   // Example: Case-insensitive search for user names starting with "j"
   db.users.find({ name: { $regex: /^j/i } });
   ```

37. **Explain the concept of a covered query in MongoDB.**
   - **Answer:** A covered query is one where all the fields returned in the result are covered by an index, reducing the amount of data that needs to be scanned.

   ```javascript
   // Example: Covered query using an index on the "age" field
   db.users.find({ age: { $gte: 25 } }, { name: 1, age: 1, _id: 0 }).explain("executionStats");
   ```

38. **What is the purpose of the `findOneAndUpdate` method in MongoDB?**
   - **Answer:** The `findOneAndUpdate` method atomically updates and returns a single document based on a query.

   ```javascript
   // Example: Update the age of a user and return the original document
   db.users.findOneAndUpdate({ name: "Bob" }, { $set: { age: 30 } }, { returnDocument: "before" });
   ```

39. **Explain the concept of a capped collection in MongoDB.**
   - **Answer:** A capped collection is a fixed-size collection with a maximum number of documents. Once the limit is reached, older documents are replaced with new ones.

   ```javascript
   // Example: Create a capped collection with a size limit of 100KB
   db.createCollection("logs", { capped: true, size: 100000 });
   ```

40. **How can you handle relationships between documents in MongoDB?**
    - **Answer:** MongoDB supports embedding documents, referencing documents, and using a hybrid approach. The choice depends on factors like data size, access patterns, and consistency requirements.

    ```javascript
    // Example: Referencing documents (normalized model)
    const user = {
      _id: ObjectId(),
      name: "Alice",
      address_id: ObjectId("address_id")
    };

    const address = {
      _id: ObjectId("address_id"),
      city: "New York"
    };
    ```
