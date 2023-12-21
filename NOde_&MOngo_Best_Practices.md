
# Node.js Documentation and Best Practices

## Introduction

This documentation provides insights into common Node.js practices, Mongoose queries, and HTTP request handling using Axios and Fetch.

## Mongoose Queries

### 1. Fetching Data

#### Example: Get all users excluding the "__v" field

```javascript
router.get("/user", async (req, res) => {
  const usersData = await user.find().select("-__v");
  res.status(200).json({ data: userData });
});
```

Explanation: Using `.select("-__v")` excludes the "__v" field from the query result. "__v" typically represents the version key added by Mongoose.

#### Example: Get users with a specific age

```javascript
const ageToFind = 25;
const usersWithSpecificAge = await users.find({ age: ageToFind });
```

Explanation: Use `.find({})` to select documents based on a specific condition, such as finding users with a particular age.

### 2. Updating Data

#### Example: Using `findByIdAndUpdate` and `findOneAndUpdate`

```javascript
const updatedDocument = await Model.findByIdAndUpdate(id, update, { new: true });
const updatedDocument = await Model.findOneAndUpdate({ name: "John" }, update, { new: true });
```

Explanation: Use `findByIdAndUpdate` with a unique identifier and `findOneAndUpdate` with any field to modify documents. `{ new: true }` returns the updated document.

#### Example: Using `updateOne` and `updateMany`

```javascript
const filter = { name: "John" };
const update = { $set: { age: 30 } };
const result = await UserModel.updateOne(filter, update);

const filter = { status: "active" };
const update = { $set: { status: "inactive" } };
const result = await UserModel.updateMany(filter, update);
```

Explanation: Use `updateOne` to modify a single document and `updateMany` to modify multiple documents based on specified conditions.

### 3. Finding and Saving Data

#### Example: Using `findOne` and `save`

```javascript
const filter = { name: "Alice" };
const updateData = { age: 25 };

const userToUpdate = await UserModel.findOne(filter);

if (userToUpdate) {
  userToUpdate.age = updateData.age;
  const updatedUser = await userToUpdate.save();
} else {
  // Handle the case where the document is not found
}
```

Explanation: Use `findOne` to find a document, update its data, and then save the changes.

#### Example: Using `findOne` and `find({})`

```javascript
const result = await Model.findOne({ name: "John" });
const results = await Model.find({ status: "active" });
```

Explanation: Use `findOne` for a single result and `find({})` for multiple results based on specific conditions.

### 4. Deleting Data

#### Example: Using `findByIdAndDelete`, `deleteOne`, and `deleteMany`

```javascript
const deletedUserData = await users.findByIdAndDelete({ _id: id });

// Deletes a single document that matches the specified conditions
const result = await Model.deleteOne({ name: "John" });

// Deletes all documents that match the specified conditions
const result = await Model.deleteMany({ status: "inactive" });

// Combination of findOne and remove
const userToDelete = await Model.findOne({ name: "Alice" });
if (userToDelete) {
  const result = await userToDelete.remove();
} else {
  // Handle the case where the document is not found
}
```

Explanation: Choose the deletion method based on your specific use case.

## HTTP Requests: Axios vs. Fetch

### Axios

```javascript
import axios from "axios";

axios.get("https://api.example.com/data")
  .then(response => console.log(response.data))
  .catch(error => console.error(error));
```

### Fetch

```javascript
fetch("https://api.example.com/data")
  .then(response => {
    if (!response.ok) {
      throw new Error("Network response was not ok");
    }
    return response.json();
  })
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

Explanation: Both Axios and Fetch are used for making HTTP requests in JavaScript applications. Axios simplifies error handling, while Fetch requires manual checking of the `ok` property.

# Follow this repository for reference: [sejalyadav0818/NOde-MOnGo](https://github.com/sejalyadav0818/NOde-MOnGo)


