Microsoft Windows [Version 10.0.26100.4061]
(c) Microsoft Corporation. All rights reserved.

C:\Users\Minfy>mongosh
Current Mongosh Log ID: 6836cb1e64827826e46c4bcf
Connecting to:          mongodb://127.0.0.1:27017/?directConnection=true&serverSelectionTimeoutMS=2000&appName=mongosh+2.5.1
Using MongoDB:          8.0.9
Using Mongosh:          2.5.1

For mongosh info see: https://www.mongodb.com/docs/mongodb-shell/


To help improve our products, anonymous usage data is collected and sent to MongoDB periodically (https://www.mongodb.com/legal/privacy-policy).
You can opt-out by running the disableTelemetry() command.

------
   The server generated these startup warnings when booting
   2025-05-28T12:18:12.575+05:30: Access control is not enabled for the database. Read and write access to data and configuration is unrestricted
------

test> mongo dbs
Uncaught:
SyntaxError: Missing semicolon. (1:5)

> 1 | mongo dbs
    |      ^
  2 |

test> show dbs
admin   40.00 KiB
config  12.00 KiB
local   40.00 KiB
test> use fatherfamily
switched to db fatherfamily
fatherfamily> db.moneyRecord.insertOne({})
{
  acknowledged: true,
  insertedId: ObjectId('6836cc2564827826e46c4bd0')
}
fatherfamily> show collections
moneyRecord
fatherfamily> switch to todo
Uncaught:
SyntaxError: Unexpected token, expected "(" (1:7)

> 1 | switch to todo
    |        ^
  2 |

fatherfamily> use todo
switched to db todo
todo> show collections

todo> db.todotask.insertOne({
... task:"To complete Assignment"
... deadline: new Date("2025-05-30
todo> db.createCollection("tasks")
{ ok: 1 }
todo> db.tasks.insertOne({
... task:"Complete the assignment",
... deadline : ISODate("2025-05-30T23:59:59Z"),
... status:"pending"
... })
{
  acknowledged: true,
  insertedId: ObjectId('6836e16464827826e46c4bd1')
}
todo> db.tasks.find()
[
  {
    _id: ObjectId('6836e16464827826e46c4bd1'),
    task: 'Complete the assignment',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: 'pending'
  }
]
todo> db.tasks.find({status: "pending"})
[
  {
    _id: ObjectId('6836e16464827826e46c4bd1'),
    task: 'Complete the assignment',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: 'pending'
  }
]
todo> db.tasks.updateOne({task:"Complete the assignment"},{$set:{status: "completed"}})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
todo> db.tasks.find()
[
  {
    _id: ObjectId('6836e16464827826e46c4bd1'),
    task: 'Complete the assignment',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: 'completed'
  }
]
todo> db.tasks.insertOne({ task: "remind venkat to buy the google", deadline: ISODate("2025-05-30T23:59:59Z"), status: "pending" })
{
  acknowledged: true,
  insertedId: ObjectId('6836e25464827826e46c4bd2')
}
todo> db.tasks.find()
[
  {
    _id: ObjectId('6836e16464827826e46c4bd1'),
    task: 'Complete the assignment',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: 'completed'
  },
  {
    _id: ObjectId('6836e25464827826e46c4bd2'),
    task: 'remind venkat to buy the google',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: 'pending'
  }
]
todo> db.tasks.updateOne({task:"remind venkat to buy the google"},{$set:{status: "completed"}})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
todo> db.tasks.find()
[
  {
    _id: ObjectId('6836e16464827826e46c4bd1'),
    task: 'Complete the assignment',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: 'completed'
  },
  {
    _id: ObjectId('6836e25464827826e46c4bd2'),
    task: 'remind venkat to buy the google',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: 'completed'
  }
]
todo> db.showcollections
todo.showcollections
todo> show collections
tasks
todo> db.tasks.insertOne({
... task: ISODate("2025-05-30T23:59:59Z"),
... priority:"high",
... status:false
... })
{
  acknowledged: true,
  insertedId: ObjectId('6836e51364827826e46c4bd3')
}
todo> db.task.find()

todo> db.tasks.find()
[
  {
    _id: ObjectId('6836e16464827826e46c4bd1'),
    task: 'Complete the assignment',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: 'completed'
  },
  {
    _id: ObjectId('6836e25464827826e46c4bd2'),
    task: 'remind venkat to buy the google',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: 'completed'
  },
  {
    _id: ObjectId('6836e51364827826e46c4bd3'),
    task: ISODate('2025-05-30T23:59:59.000Z'),
    priority: 'high',
    status: false
  }
]
todo> db.tasks.updateMany(
...     { status: "completed" },
...     { $set: { status: true } }
... )
...
... db.tasks.updateMany(
...     { status: "pending" },
...     { $set: { status: false } }
... )
...
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 0,
  modifiedCount: 0,
  upsertedCount: 0
}
todo> db.tasks.find()
[
  {
    _id: ObjectId('6836e16464827826e46c4bd1'),
    task: 'Complete the assignment',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: true
  },
  {
    _id: ObjectId('6836e25464827826e46c4bd2'),
    task: 'remind venkat to buy the google',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: true
  },
  {
    _id: ObjectId('6836e51364827826e46c4bd3'),
    task: ISODate('2025-05-30T23:59:59.000Z'),
    priority: 'high',
    status: false
  }
]
todo> db.tasks.updateOne(
...     { task: "New Task Without Status" },
...     { $set: { status: false } },
...     { upsert: true }
... )
...
{
  acknowledged: true,
  insertedId: ObjectId('6836e834fc57c3c234b50577'),
  matchedCount: 0,
  modifiedCount: 0,
  upsertedCount: 1
}
todo> db.tasks.insertOne({
...     task: "Start a new project",
...     deadline: ISODate("2025-06-01T00:00:00Z"),
...     priority: "medium",
...     category: "work"
... })
...
todo> db.tasks.insertOne({
... task: "new todo task",
... deadline:ISODate("2025-05-30T00:00:00Z"),
... })
{
  acknowledged: true,
  insertedId: ObjectId('6836e8b164827826e46c4bd4')
}
todo> db.tasks.find()
[
  {
    _id: ObjectId('6836e16464827826e46c4bd1'),
    task: 'Complete the assignment',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: true
  },
  {
    _id: ObjectId('6836e25464827826e46c4bd2'),
    task: 'remind venkat to buy the google',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: true
  },
  {
    _id: ObjectId('6836e51364827826e46c4bd3'),
    task: ISODate('2025-05-30T23:59:59.000Z'),
    priority: 'high',
    status: false
  },
  {
    _id: ObjectId('6836e834fc57c3c234b50577'),
    task: 'New Task Without Status',
    status: false
  },
  {
    _id: ObjectId('6836e8b164827826e46c4bd4'),
    task: 'new todo task',
    deadline: ISODate('2025-05-30T00:00:00.000Z')
  }
]
todo> db.tasks.updateMany(
...     { status: { $exists: false } }, // Finds tasks where `status` is missing
...     { $set: { status: false } }
... )
...
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
todo> db.tasks.find()
[
  {
    _id: ObjectId('6836e16464827826e46c4bd1'),
    task: 'Complete the assignment',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: true
  },
  {
    _id: ObjectId('6836e25464827826e46c4bd2'),
    task: 'remind venkat to buy the google',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: true
  },
  {
    _id: ObjectId('6836e51364827826e46c4bd3'),
    task: ISODate('2025-05-30T23:59:59.000Z'),
    priority: 'high',
    status: false
  },
  {
    _id: ObjectId('6836e834fc57c3c234b50577'),
    task: 'New Task Without Status',
    status: false
  },
  {
    _id: ObjectId('6836e8b164827826e46c4bd4'),
    task: 'new todo task',
    deadline: ISODate('2025-05-30T00:00:00.000Z'),
    status: false
  }
]
todo> db.tasks.insertOne({
...     task: "Start a new project",
...     deadline: ISODate("2025-06-01T00:00:00Z"),
...     priority: "medium",
...     category: "work",
...     status: false,
...     createdAt: new Date(),  // Stores the creation time
...     updatedAt: new Date()   // Initially same as createdAt
... })
...
{
  acknowledged: true,
  insertedId: ObjectId('6836ea3464827826e46c4bd5')
}
todo> db.tasks.updateOne(
...     { task: "Start a new project" },
...     { $set: { status: true, updatedAt: new Date() } }
... )
...
todo> db.tasks.updateOne(
...     { task: "Start a new project" },
...     { $set: { status: true, updatedAt: new Date() } }
... )
...
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
todo> db.tasks.find()
[
  {
    _id: ObjectId('6836e16464827826e46c4bd1'),
    task: 'Complete the assignment',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: true
  },
  {
    _id: ObjectId('6836e25464827826e46c4bd2'),
    task: 'remind venkat to buy the google',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: true
  },
  {
    _id: ObjectId('6836e51364827826e46c4bd3'),
    task: ISODate('2025-05-30T23:59:59.000Z'),
    priority: 'high',
    status: false
  },
  {
    _id: ObjectId('6836e834fc57c3c234b50577'),
    task: 'New Task Without Status',
    status: false
  },
  {
    _id: ObjectId('6836e8b164827826e46c4bd4'),
    task: 'new todo task',
    deadline: ISODate('2025-05-30T00:00:00.000Z'),
    status: false
  },
  {
    _id: ObjectId('6836ea3464827826e46c4bd5'),
    task: 'Start a new project',
    deadline: ISODate('2025-06-01T00:00:00.000Z'),
    priority: 'medium',
    category: 'work',
    status: true,
    createdAt: ISODate('2025-05-28T10:49:24.477Z'),
    updatedAt: ISODate('2025-05-28T10:50:00.784Z')
  }
]
todo> db.createCollection("tasks", {
...    validator: {
...       $jsonSchema: {
...          bsonType: "object",
...          required: ["task", "deadline", "status"],
...          properties: {
...             status: {
...                bsonType: "bool",  // Only allows Boolean values
...                description: "Status must be true or false"
...             }
...          }
...       }
...    }
... })
...
MongoServerError[NamespaceExists]: namespace todo.tasks already exists, but with different options: { uuid: UUID("4b4511cf-1dd5-45c3-9298-4dfb08e282bf") }
todo> db.tasks.updateMany(
...     {},  // Selects all documents
...     { $set: { updated: new Date() } }  // Adds `updated` field with the current timestamp
... )
...
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 6,
  modifiedCount: 6,
  upsertedCount: 0
}
todo> db.tasks.find()
[
  {
    _id: ObjectId('6836e16464827826e46c4bd1'),
    task: 'Complete the assignment',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: true,
    updated: ISODate('2025-05-28T11:07:48.662Z')
  },
  {
    _id: ObjectId('6836e25464827826e46c4bd2'),
    task: 'remind venkat to buy the google',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: true,
    updated: ISODate('2025-05-28T11:07:48.662Z')
  },
  {
    _id: ObjectId('6836e51364827826e46c4bd3'),
    task: ISODate('2025-05-30T23:59:59.000Z'),
    priority: 'high',
    status: false,
    updated: ISODate('2025-05-28T11:07:48.662Z')
  },
  {
    _id: ObjectId('6836e834fc57c3c234b50577'),
    task: 'New Task Without Status',
    status: false,
    updated: ISODate('2025-05-28T11:07:48.662Z')
  },
  {
    _id: ObjectId('6836e8b164827826e46c4bd4'),
    task: 'new todo task',
    deadline: ISODate('2025-05-30T00:00:00.000Z'),
    status: false,
    updated: ISODate('2025-05-28T11:07:48.662Z')
  },
  {
    _id: ObjectId('6836ea3464827826e46c4bd5'),
    task: 'Start a new project',
    deadline: ISODate('2025-06-01T00:00:00.000Z'),
    priority: 'medium',
    category: 'work',
    status: true,
    createdAt: ISODate('2025-05-28T10:49:24.477Z'),
    updatedAt: ISODate('2025-05-28T10:50:00.784Z'),
    updated: ISODate('2025-05-28T11:07:48.662Z')
  }
]
todo> db.tasks.updateOne(
...     { task: "Start a new project" },
...     { $set: { status: true, updated: new Date() } }
... )
...
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
todo> db.tasks.find()
[
  {
    _id: ObjectId('6836e16464827826e46c4bd1'),
    task: 'Complete the assignment',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: true,
    updated: ISODate('2025-05-28T11:07:48.662Z')
  },
  {
    _id: ObjectId('6836e25464827826e46c4bd2'),
    task: 'remind venkat to buy the google',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: true,
    updated: ISODate('2025-05-28T11:07:48.662Z')
  },
  {
    _id: ObjectId('6836e51364827826e46c4bd3'),
    task: ISODate('2025-05-30T23:59:59.000Z'),
    priority: 'high',
    status: false,
    updated: ISODate('2025-05-28T11:07:48.662Z')
  },
  {
    _id: ObjectId('6836e834fc57c3c234b50577'),
    task: 'New Task Without Status',
    status: false,
    updated: ISODate('2025-05-28T11:07:48.662Z')
  },
  {
    _id: ObjectId('6836e8b164827826e46c4bd4'),
    task: 'new todo task',
    deadline: ISODate('2025-05-30T00:00:00.000Z'),
    status: false,
    updated: ISODate('2025-05-28T11:07:48.662Z')
  },
  {
    _id: ObjectId('6836ea3464827826e46c4bd5'),
    task: 'Start a new project',
    deadline: ISODate('2025-06-01T00:00:00.000Z'),
    priority: 'medium',
    category: 'work',
    status: true,
    createdAt: ISODate('2025-05-28T10:49:24.477Z'),
    updatedAt: ISODate('2025-05-28T10:50:00.784Z'),
    updated: ISODate('2025-05-28T11:11:26.467Z')
  }
]
todo> db.tasks.updateMany(
...     { priority: { $exists: false } }, // If priority is missing
...     { $set: { priority: "basic" } }
... )
...
... db.tasks.updateMany(
...     { category: { $exists: false } }, // If category is missing
...     { $set: { category: "work" } }
... )
...
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 5,
  modifiedCount: 5,
  upsertedCount: 0
}
todo> db.tasks.find()
[
  {
    _id: ObjectId('6836e16464827826e46c4bd1'),
    task: 'Complete the assignment',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: true,
    updated: ISODate('2025-05-28T11:07:48.662Z'),
    priority: 'basic',
    category: 'work'
  },
  {
    _id: ObjectId('6836e25464827826e46c4bd2'),
    task: 'remind venkat to buy the google',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: true,
    updated: ISODate('2025-05-28T11:07:48.662Z'),
    priority: 'basic',
    category: 'work'
  },
  {
    _id: ObjectId('6836e51364827826e46c4bd3'),
    task: ISODate('2025-05-30T23:59:59.000Z'),
    priority: 'high',
    status: false,
    updated: ISODate('2025-05-28T11:07:48.662Z'),
    category: 'work'
  },
  {
    _id: ObjectId('6836e834fc57c3c234b50577'),
    task: 'New Task Without Status',
    status: false,
    updated: ISODate('2025-05-28T11:07:48.662Z'),
    priority: 'basic',
    category: 'work'
  },
  {
    _id: ObjectId('6836e8b164827826e46c4bd4'),
    task: 'new todo task',
    deadline: ISODate('2025-05-30T00:00:00.000Z'),
    status: false,
    updated: ISODate('2025-05-28T11:07:48.662Z'),
    priority: 'basic',
    category: 'work'
  },
  {
    _id: ObjectId('6836ea3464827826e46c4bd5'),
    task: 'Start a new project',
    deadline: ISODate('2025-06-01T00:00:00.000Z'),
    priority: 'medium',
    category: 'work',
    status: true,
    createdAt: ISODate('2025-05-28T10:49:24.477Z'),
    updatedAt: ISODate('2025-05-28T10:50:00.784Z'),
    updated: ISODate('2025-05-28T11:11:26.467Z')
  }
]
todo> db.tasks.find().pretty()
[
  {
    _id: ObjectId('6836e16464827826e46c4bd1'),
    task: 'Complete the assignment',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: true,
    updated: ISODate('2025-05-28T11:07:48.662Z'),
    priority: 'basic',
    category: 'work'
  },
  {
    _id: ObjectId('6836e25464827826e46c4bd2'),
    task: 'remind venkat to buy the google',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: true,
    updated: ISODate('2025-05-28T11:07:48.662Z'),
    priority: 'basic',
    category: 'work'
  },
  {
    _id: ObjectId('6836e51364827826e46c4bd3'),
    task: ISODate('2025-05-30T23:59:59.000Z'),
    priority: 'high',
    status: false,
    updated: ISODate('2025-05-28T11:07:48.662Z'),
    category: 'work'
  },
  {
    _id: ObjectId('6836e834fc57c3c234b50577'),
    task: 'New Task Without Status',
    status: false,
    updated: ISODate('2025-05-28T11:07:48.662Z'),
    priority: 'basic',
    category: 'work'
  },
  {
    _id: ObjectId('6836e8b164827826e46c4bd4'),
    task: 'new todo task',
    deadline: ISODate('2025-05-30T00:00:00.000Z'),
    status: false,
    updated: ISODate('2025-05-28T11:07:48.662Z'),
    priority: 'basic',
    category: 'work'
  },
  {
    _id: ObjectId('6836ea3464827826e46c4bd5'),
    task: 'Start a new project',
    deadline: ISODate('2025-06-01T00:00:00.000Z'),
    priority: 'medium',
    category: 'work',
    status: true,
    createdAt: ISODate('2025-05-28T10:49:24.477Z'),
    updatedAt: ISODate('2025-05-28T10:50:00.784Z'),
    updated: ISODate('2025-05-28T11:11:26.467Z')
  }
]
todo> db.tasks.countDocumnets({})
TypeError: db.tasks.countDocumnets is not a function
todo> db.tasks.countDocuments({})
6
todo> db.tasks.countDocuments({status:true})
3
todo> db.tasks.find().sort({ $natural: 1 })
[
  {
    _id: ObjectId('6836e16464827826e46c4bd1'),
    task: 'Complete the assignment',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: true,
    updated: ISODate('2025-05-28T11:07:48.662Z'),
    priority: 'basic',
    category: 'work'
  },
  {
    _id: ObjectId('6836e25464827826e46c4bd2'),
    task: 'remind venkat to buy the google',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: true,
    updated: ISODate('2025-05-28T11:07:48.662Z'),
    priority: 'basic',
    category: 'work'
  },
  {
    _id: ObjectId('6836e51364827826e46c4bd3'),
    task: ISODate('2025-05-30T23:59:59.000Z'),
    priority: 'high',
    status: false,
    updated: ISODate('2025-05-28T11:07:48.662Z'),
    category: 'work'
  },
  {
    _id: ObjectId('6836e834fc57c3c234b50577'),
    task: 'New Task Without Status',
    status: false,
    updated: ISODate('2025-05-28T11:07:48.662Z'),
    priority: 'basic',
    category: 'work'
  },
  {
    _id: ObjectId('6836e8b164827826e46c4bd4'),
    task: 'new todo task',
    deadline: ISODate('2025-05-30T00:00:00.000Z'),
    status: false,
    updated: ISODate('2025-05-28T11:07:48.662Z'),
    priority: 'basic',
    category: 'work'
  },
  {
    _id: ObjectId('6836ea3464827826e46c4bd5'),
    task: 'Start a new project',
    deadline: ISODate('2025-06-01T00:00:00.000Z'),
    priority: 'medium',
    category: 'work',
    status: true,
    createdAt: ISODate('2025-05-28T10:49:24.477Z'),
    updatedAt: ISODate('2025-05-28T10:50:00.784Z'),
    updated: ISODate('2025-05-28T11:11:26.467Z')
  }
]
todo>     { $set: { dueDate: new Date() } }  // Adds `up
ISODate('2025-05-28T11:20:25.524Z')
todo> db.tasks.find().pretty()
[
  {
    _id: ObjectId('6836e16464827826e46c4bd1'),
    task: 'Complete the assignment',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: true,
    updated: ISODate('2025-05-28T11:07:48.662Z'),
    priority: 'basic',
    category: 'work'
  },
  {
    _id: ObjectId('6836e25464827826e46c4bd2'),
    task: 'remind venkat to buy the google',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: true,
    updated: ISODate('2025-05-28T11:07:48.662Z'),
    priority: 'basic',
    category: 'work'
  },
  {
    _id: ObjectId('6836e51364827826e46c4bd3'),
    task: ISODate('2025-05-30T23:59:59.000Z'),
    priority: 'high',
    status: false,
    updated: ISODate('2025-05-28T11:07:48.662Z'),
    category: 'work'
  },
  {
    _id: ObjectId('6836e834fc57c3c234b50577'),
    task: 'New Task Without Status',
    status: false,
    updated: ISODate('2025-05-28T11:07:48.662Z'),
    priority: 'basic',
    category: 'work'
  },
  {
    _id: ObjectId('6836e8b164827826e46c4bd4'),
    task: 'new todo task',
    deadline: ISODate('2025-05-30T00:00:00.000Z'),
    status: false,
    updated: ISODate('2025-05-28T11:07:48.662Z'),
    priority: 'basic',
    category: 'work'
  },
  {
    _id: ObjectId('6836ea3464827826e46c4bd5'),
    task: 'Start a new project',
    deadline: ISODate('2025-06-01T00:00:00.000Z'),
    priority: 'medium',
    category: 'work',
    status: true,
    createdAt: ISODate('2025-05-28T10:49:24.477Z'),
    updatedAt: ISODate('2025-05-28T10:50:00.784Z'),
    updated: ISODate('2025-05-28T11:11:26.467Z')
  }
]
todo> db.tasks.updateMany(
...     { dueDate: { $exists: false } },  // Find tasks missing `dueDate`
...     { $set: { dueDate: ISODate("2025-06-05T00:00:00Z") } }  // Default due date
... )
...
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 6,
  modifiedCount: 6,
  upsertedCount: 0
}
todo> db.tasks.find().pretty()
[
  {
    _id: ObjectId('6836e16464827826e46c4bd1'),
    task: 'Complete the assignment',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: true,
    updated: ISODate('2025-05-28T11:07:48.662Z'),
    priority: 'basic',
    category: 'work',
    dueDate: ISODate('2025-06-05T00:00:00.000Z')
  },
  {
    _id: ObjectId('6836e25464827826e46c4bd2'),
    task: 'remind venkat to buy the google',
    deadline: ISODate('2025-05-30T23:59:59.000Z'),
    status: true,
    updated: ISODate('2025-05-28T11:07:48.662Z'),
    priority: 'basic',
    category: 'work',
    dueDate: ISODate('2025-06-05T00:00:00.000Z')
  },
  {
    _id: ObjectId('6836e51364827826e46c4bd3'),
    task: ISODate('2025-05-30T23:59:59.000Z'),
    priority: 'high',
    status: false,
    updated: ISODate('2025-05-28T11:07:48.662Z'),
    category: 'work',
    dueDate: ISODate('2025-06-05T00:00:00.000Z')
  },
  {
    _id: ObjectId('6836e834fc57c3c234b50577'),
    task: 'New Task Without Status',
    status: false,
    updated: ISODate('2025-05-28T11:07:48.662Z'),
    priority: 'basic',
    category: 'work',
    dueDate: ISODate('2025-06-05T00:00:00.000Z')
  },
  {
    _id: ObjectId('6836e8b164827826e46c4bd4'),
    task: 'new todo task',
    deadline: ISODate('2025-05-30T00:00:00.000Z'),
    status: false,
    updated: ISODate('2025-05-28T11:07:48.662Z'),
    priority: 'basic',
    category: 'work',
    dueDate: ISODate('2025-06-05T00:00:00.000Z')
  },
  {
    _id: ObjectId('6836ea3464827826e46c4bd5'),
    task: 'Start a new project',
    deadline: ISODate('2025-06-01T00:00:00.000Z'),
    priority: 'medium',
    category: 'work',
    status: true,
    createdAt: ISODate('2025-05-28T10:49:24.477Z'),
    updatedAt: ISODate('2025-05-28T10:50:00.784Z'),
    updated: ISODate('2025-05-28T11:11:26.467Z'),
    dueDate: ISODate('2025-06-05T00:00:00.000Z')
  }
]
todo> db.tasks.find({
...     dueDate: {
...         $gte: ISODate(new Date().toISOString().split("T")[0] + "T00:00:00.000Z"),
...         $lt: ISODate(new Date().toISOString().split("T")[0] + "T23:59:59.999Z")
...     }
... })
...

todo> db.tasks.find({
...     createdAt: {
...         $gte: new Date(Date.now() - 5 * 60 * 1000)  // 5 minutes ago
...     }
... })
...

todo>         $gte: new Date(Date.now() - 5 * 60 * 1000)
ISODate('2025-05-28T11:18:19.300Z')
todo> db.tasks.find({
...     createdAt: {
...         $gte: new Date(Date.now() - 5 * 60 * 1000)
...     }
... })
...

todo> db.tasks.find({
...     createdAt: {
...         $lte: new Date(Date.now() - 5 * 60 * 1000)
...     }
... })
...
[
  {
    _id: ObjectId('6836ea3464827826e46c4bd5'),
    task: 'Start a new project',
    deadline: ISODate('2025-06-01T00:00:00.000Z'),
    priority: 'medium',
    category: 'work',
    status: true,
    createdAt: ISODate('2025-05-28T10:49:24.477Z'),
    updatedAt: ISODate('2025-05-28T10:50:00.784Z'),
    updated: ISODate('2025-05-28T11:11:26.467Z'),
    dueDate: ISODate('2025-06-05T00:00:00.000Z')
  }
]
todo>
