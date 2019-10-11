l1. Create a database named `blog`.
  
    use blog

2. Create a collection called 'articles'.

  db.createCollection("articles")

3. Insert multiple documents(at least 3) into atricles. It should have fields
  - title as string
  - description as String
  - author as nested object
    - author should have
      - name
      - email
      - age
      - example author: {name: 'abc', email: 'abc@gmail', age: 25}
  - tags : Array of strings like ['html', 'css'] 
```js

  db.articles.insert({title:"a",description:"hello",author:{name:"sam",email:"sam@gmail.com",age:34},tags:["js","mongo"]})

// An article should look like
{
  _id: 'some_random_id',
  title: '',
  description: '',
  author: {
    name: '',
    email: '',
    age: ''
  },
  tags: ['js', 'mongo']
}
```

4. Find all the articles using `db.COLLECTION_NAME.find()`

  db.articles.find()  

5. Find a document using _id field.

  db.articles.find({_id:ObjectId("5d9f5a9d4289755979264719")})


6. Find documents using title and author's name field.

  db.articles.find({"title":"a","author.name":"sam"})  

7. Find doucment using a specific tag.

  db.articles.find({tags:"js"})

8. Update title of a document using its _id field.

  db.articles.update({_id:ObjectId("5d9f5a9d4289755979264719")},{$set:{title:"carbon"}})

9. Update a author's name using article's title.

  db.articles.update({title:"a"},{$set:{"author.name":"markos"}})

10. Add additional tag in a specific document.

  db.articles.update({title:"a"},{$push:{tags:"html"}})

11. Increment an auhtor's age by 5.  

  <!-- db.articles.update({title:"a"},{$set:{"author.age":28}}) -->
  db.articles.update({title:"a"},{$inc:{"author.age":5}})

12. Delete a document using _id field with `db.COLLECTION_NAME.remove()`.


