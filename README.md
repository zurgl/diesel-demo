# Some note with instruction

## Dependencies

```text
sudo apt install libpq-dev
cargo install diesel_cli --no-default-features --features postgres
```

## Basic Setup

```text
cargo new --lib diesel_demo
cd diesel_demo
cargo add dotenvy
cargo add diesel --features=postgres
echo DATABASE_URL=postgres://username:password@localhost/diesel_demo >> .env
diesel setup
diesel migration generate create_posts
```

`up.sql`

```sql
CREATE TABLE posts (
  id SERIAL PRIMARY KEY,
  title VARCHAR NOT NULL,
  body TEXT NOT NULL,
  published BOOLEAN NOT NULL DEFAULT FALSE
)
```

`down.sql`

```sql
DROP TABLE posts
```

```text
diesel migration run
diesel migration redo
```
