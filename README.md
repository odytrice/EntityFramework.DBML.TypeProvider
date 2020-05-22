# EntityFramework.DBML.TypeProvider
F# Entity Framework Core Type Provider for DBML

[DBML](https://www.dbml.org/home/#intro) is a simple Database markup Language

```dbml
Table users {
  id integer
  username varchar
  role varchar
  created_at timestamp
}

Table posts {
  id integer [primary key]
  title varchar
  body text [note: 'Content of the post']
  user_id integer
  status post_status
  created_at timestamp
}

Enum post_status {
  draft
  published
  private [note: 'visible via URL only']
}

Ref: posts.user_id > users.id // many-to-one
```

The goal of this project is essentially to use this schema to generate [Entity Framework Core](https://github.com/dotnet/efcore) Types 
