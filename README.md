## Project - Books Management

This project is an application skeleton for a typical [Node.js](https://nodejs.org/) web app.


## Getting Started

To get you started you can simply clone the repository:

```
git clone https://github.com/AkshayG999/Book_management_asst.git
```

and install the dependencies

```
npm install
```

### Prerequisites

You need git to clone the repository. You can get git from
[http://git-scm.com/](http://git-scm.com/).

A number of node.js tools is necessary to initialize and test the project. You must have node.js and its package manager (npm) installed. You can get them from [http://nodejs.org/](http://nodejs.org/). The tools/modules used in this project are listed in package.json and include express, mongodb and mongoose.


### Run the Application

The project is preconfigured with a simple development web server. The simplest way to start this server is:

    npm start

### Models

- Author Model

```yaml
{
  title: {string, mandatory, enum[Mr, Mrs, Miss]},
  name: {string, mandatory},
  phone: {string, mandatory, unique},
  email: {string, mandatory, valid email, unique},
  password: {string, mandatory, minLen 8, maxLen 15},
  address: {
    street: {string},
    city: {string},
    pincode: {string}
  },
  createdAt: {timestamp},
  updatedAt: {timestamp}
}
```

- Books Model

````yaml
{
  title: { string, mandatory, unique },
  excerpt: { string, mandatory },
  summary: { string, mandatory },
  authorId: { ObjectId, mandatory, refs to author model },
  ISBN: { string, mandatory, unique },
  category: { string, mandatory },
  subcategory: [string, mandatory],
  reviews:
    { number, default: 0, comment: Holds number of reviews of this book },
  deletedAt: { Date, when the document is deleted },
  isDeleted: { boolean, default: false },
  releasedAt: { Date, mandatory, format("YYYY-MM-DD") },
  createdAt: { timestamp },
  updatedAt: { timestamp },
}



## Response

### Successful Response structure

```yaml
{ status: true, message: "Success", data: {} }
````

### Error Response structure

```yaml
{ status: false, message: "" }
```

## Collections

## users

```yaml
{
  _id: ObjectId("88abc190ef0288abc190ef02"),
  title: "Mr",
  name: "John Doe",
  phone: 9897969594,
  email: "johndoe@mailinator.com",
  password: "abcd1234567",
  address:
    { street: "110, Ridhi Sidhi Tower", city: "Jaipur", pincode: "400001" },
  "createdAt": "2021-09-17T04:25:07.803Z",
  "updatedAt": "2021-09-17T04:25:07.803Z",
}
```

### books

```yaml
{
  "_id": ObjectId("88abc190ef0288abc190ef55"),
  "title": "How to win friends and influence people",
  "summary":"Book Summary-0",
  "excerpt": "book body",
  "authorId": ObjectId("88abc190ef0288abc190ef02"),
  "ISBN": "978-0008391331",
  "category": "Book",
  "subcategory": "Non fiction",
  "isDeleted": false,
  "reviews": 0,
  "releasedAt": "2021-09-17"
  "createdAt": "2021-09-17T04:25:07.803Z",
  "updatedAt": "2021-09-17T04:25:07.803Z",
}
```

## Response examples

### Get books response

```yaml
{
  status: true,
  message: 'Books list',
  data: [
    {
      "_id": ObjectId("88abc190ef0288abc190ef55"),
      "title": "How to win friends and influence people",
      "summary":"Book Summary-0",
      "excerpt": "book body",
      "authorId": ObjectId("88abc190ef0288abc190ef02")
      "category": "Book",
      "reviews": 0,
      "releasedAt": "2021-09-17T04:25:07.803Z"
    },
    {
      "_id": ObjectId("88abc190ef0288abc190ef56"),
      "title": "How to win friends and influence people",
      "summary":"Book Summary-1",
      "excerpt": "book body",
      "authorId": ObjectId("88abc190ef0288abc190ef02")
      "category": "Book",
      "reviews": 0,
      "releasedAt": "2021-09-17T04:25:07.803Z"
    }
  ]
}
```

### Book details response

```yaml
{
  status: true,
  message: 'Books list',
  data: {
    "_id": ObjectId("88abc190ef0288abc190ef55"),
    "title": "How to win friends and influence people",
    "summary":"Book Summary",
    "excerpt": "book body",
    "authorId": ObjectId("88abc190ef0288abc190ef02")
    "category": "Book",
    "subcategory": ["Non fiction", "Self Help"],
    "isDeleted": false,
    "reviews": 4,
    "releasedAt": "2021-09-17T04:25:07.803Z"
    "createdAt": "2021-09-17T04:25:07.803Z",
    "updatedAt": "2021-09-17T04:25:07.803Z",
  }
}
```

### Book details response no reviews

```yaml
{
  status: true,
  message: 'Books list',
  data: {
    "_id": ObjectId("88abc190ef0288abc190ef55"),
    "title": "How to win friends and influence people",
    "summary":"Book Summary",
    "excerpt": "book body",
    "authorId": ObjectId("88abc190ef0288abc190ef02")
    "category": "Book",
    "subcategory": "Non fiction", "Self Help",
    "isDeleted": false,
    "reviews": 0,
    "releasedAt": "2021-09-17"
    "createdAt": "2021-09-17T04:25:07.803Z",
    "updatedAt": "2021-09-17T04:25:07.803Z",
  }
}
```

