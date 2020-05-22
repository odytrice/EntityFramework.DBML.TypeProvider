# EntityFramework.TypeProvider
F# Entity Framework Core Type Provider

This type provider uses DBML to generate Entity Framework Types. [DBML](https://www.dbml.org/home/#intro) is a simple Database markup Language that looks something like what we have below

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

You can easily write it by hand or use a tool like https://dbdiagram.io/ to generate it

The goal of this project is essentially to use this schema to generate [Entity Framework Core](https://github.com/dotnet/efcore) Types 
From which an application can talk to any Database backend SQL Server, Postgres, Mysql e.t.c.
