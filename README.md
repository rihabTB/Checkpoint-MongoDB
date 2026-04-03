# Checkpoint-MongoDB


```js

// 1. Create database
use contact

// 2. Create collection
db.createCollection("contactlist")

// 3. Insert documents
db.contactlist.insertMany([
  { lastName: "Ben", firstName: "Moris", email: "ben@gmail.com", age: 26 },
  { lastName: "Kefi", firstName: "Seif", email: "kefi@gmail.com", age: 15 },
  { lastName: "Emilie", firstName: "brouge", email: "emilie.b@gmail.com", age: 40 },
  { lastName: "Alex", firstName: "brown", age: 4 },
  { lastName: "Denzel", firstName: "Washington", age: 3 }
])

// 4. Display all contacts
db.contactlist.find()

// 5. Display one contact by ID
db.contactlist.find({ _id: ObjectId("3") })

// 6. Display contacts with age > 18
db.contactlist.find({ age: { $gt: 18 } })

// 7. Contacts with age > 18 AND name containing "ah"
db.contactlist.find({
  age: { $gt: 18 },
  $or: [
    { firstName: { $regex: "ah", $options: "i" } },
    { lastName: { $regex: "ah", $options: "i" } }
  ]
})

// 8. Update "Kefi Seif" → "Kefi Anis"
db.contactlist.updateOne(
  { lastName: "Kefi", firstName: "Seif" },
  { $set: { firstName: "Anis" } }
)

// 9. Delete contacts with age < 5
db.contactlist.deleteMany({ age: { $lt: 5 } })

// 10. Display all contacts again
db.contactlist.find()

