
## Step 1: Install mongodb Stateful Set
`kubectl apply -f mongo-ss.yaml` 
## Step 2: Install mongodb Headless svc
`kubectl apply -f mongo-svc.yaml` 
## Step 3: Connect to mongodb and verify connections
`kubectl exec -it mongodb-standalone-0 sh`

`mongo mongodb://mongodb-standalone-0.database:27017`

`use admin` 

`db.auth('admin','password')` /* authenticate */

`db.createCollection('todo')`  /* create collection */

` db.getCollectionNames()` /*  list collections */

`show dbs` /*  list dbs */



## insert a todo's
`db.todo.insertOne( { name: 'Learn Containers', completed:false })` 

`db.todo.insertMany([ 
    { name: 'Learn Deployments', completed:false }, 
    { name: 'Learn Pods', completed:false }, 
    { name: 'Learn SS', completed:false },
    { name: 'Learn Jobs', completed:false }, 
    { name: 'Learn Cron', completed:false }
    ])`

##Find todos

`db.todo.find({})`

## Update 

` db.todo.updateOne(
      { "name" : "Learn Containers" },
      { $set: { "completed" : true } }
   );`

` db.todo.updateOne(
      { "name" : "Learn Pods" },
      { $set: { "completed" : true } }
   );`
## Query completed task
` db.todo.find(
       { "completed" : true } 
   );`

## Delete completed task
 `  db.todo.deleteOne( { "completed" : true } 
    );`


### Commands
use admin;
db.auth('admin','password');
db.createCollection('todo');
db.getCollectionNames();
show dbs;
db.todo.insertOne( { name: 'Learn Containers', completed:false });
db.todo.insertMany([ 
    { name: 'Learn Deployments', completed:false }, 
    { name: 'Learn Pods', completed:false }, 
    { name: 'Learn SS', completed:false },
    { name: 'Learn Jobs', completed:false }, 
    { name: 'Learn Cron', completed:false }
    ]);
db.todo.findOne({});
db.todo.updateOne(
      { "name" : "Learn Containers" },
      { $set: { "completed" : true } }
   );
db.todo.updateOne(
      { "name" : "Learn Pods" },
      { $set: { "completed" : true } }
   );
db.todo.find(
       { "completed" : true } 
   );
 db.todo.deleteOne( { "completed" : true } 
    );