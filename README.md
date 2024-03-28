**Running the GraphQL Server:
**

1. Navigate to the GraphQL directory using cd GraphQL && npm ci.

2. Execute npm run start.

🚀 Server is now ready at: http://localhost:4001/

GraphQL playground can be accessed at: http://localhost:4001/

Below are some sample queries you can try on the playground:

query Authors {
  authors {
    id
    name
    books {
      id
      title
      publishedYear
    }
  }
}

query Books {
  books {
    id
    title
    publishedYear
    author {
      id
      name
    }
  }
}

query Author {
  author(id: "2") {
    id
    name
    books {
      id
      title
      publishedYear
    }
  }
}

query Book {
  book(id: "103") {
    author {
      name
    }
    publishedYear
    title
  }
}

mutation AddBook($title: String!, $publishedYear: Int!, $authorId: ID!) {
  addBook(title: $title, publishedYear: $publishedYear, authorId: $authorId) {
    id
    title
    publishedYear
    author {
      id
      name
    }
  }
}


Variables:

{
  "title": "New Book 4",
  "publishedYear": 2022,
  "authorId": "1"
}

**Running the gRPC Server:**

1. Navigate to the gRPC/ directory and install dependencies using npm ci.

2. Start the server with npm run server.

3. Run the client using npm run client.

🚀 gRPC server is now listening on port 30043.
🚀 gRPC client is running at port 3000.

You can try the following curl commands in the terminal to see the gRPC communication:

curl http://localhost:3000/

curl -X POST -H "Content-Type: application/json" -d '{"name":"John Doe","age":30,"address":"123 Main St"}' http://localhost:3000/create

curl -X POST -H "Content-Type: application/json" -d '{"id":"customer_id_here","name":"Updated Name","age":35,"address":"456 Elm St"}' http://localhost:3000/update

curl -X POST -H "Content-Type: application/json" -d '{"customer_id":"customer_id_to_remove"}' http://localhost:3000/remove
