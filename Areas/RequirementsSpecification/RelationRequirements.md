
---
### Table `public.followers`

| Column  | Type    | Collation | Nullable | Default |
|---------|---------|-----------|----------|---------|
| who_id  | integer |           | not null |         |
| whom_id | integer |           | not null |         |

#### Indexes:
- "followers_pkey" PRIMARY KEY, btree (who_id, whom_id)

#### Foreign-key constraints:
- "followers_who_id_fkey" FOREIGN KEY (who_id) REFERENCES users(user_id)
- "followers_whom_id_fkey" FOREIGN KEY (whom_id) REFERENCES users(user_id)

#### Query Result: `SELECT * FROM followers LIMIT 10;`

| who_id | whom_id |
|--------|---------|
|   2    |    1    |

---
### Table: `public.messages`

| Column     | Type                         | Collation | Nullable | Default                                        |
|------------|------------------------------|-----------|----------|------------------------------------------------|
| message_id | integer                      |           | not null | `nextval('messages_message_id_seq'::regclass)` |
| author_id  | integer                      |           | not null |                                                |
| text       | text                         |           | not null |                                                |
| pub_date   | timestamp without time zone  |           |          |                                                |
| flagged    | integer                      |           |          |                                                |

#### Indexes:
- **messages_pkey**: PRIMARY KEY, btree (message_id)
- **author_id_index**: btree (author_id)
- **pub_date_index**: btree (pub_date)


### Query Result: `SELECT * FROM messages LIMIT 10`

| message_id | author_id | text    | pub_date                    | flagged |
|------------|-----------|---------|-----------------------------|---------|
| 1          | 1         | hello 1 | 2024-09-27 14:18:30.633699  | 0       |
| 2          | 1         | hello 2 | 2024-09-27 14:18:35.743643  | 0       |
| 3          | 1         | hello 3 | 2024-09-27 14:18:38.971770  | 0       |
| 4          | 2         | hola 1  | 2024-09-27 14:19:37.757499  | 0       |
| 5          | 2         | hola 2  | 2024-09-27 14:19:41.457376  | 0       |

**(5 rows)**

---
### Table: `public.users`

| Column   | Type    | Collation | Nullable | Default                                  |
|----------|---------|-----------|----------|------------------------------------------|
| user_id  | integer |           | not null | `nextval('users_user_id_seq'::regclass)` |
| username | text    |           | not null |                                          |
| email    | text    |           | not null |                                          |
| pw_hash  | text    |           | not null |                                          |

### Indexes:
- `users_pkey` PRIMARY KEY, btree (user_id)
- `username_index` btree (username)

### Referenced by:
- TABLE `followers` CONSTRAINT `followers_who_id_fkey` FOREIGN KEY (who_id) REFERENCES `users(user_id)`
- TABLE `followers` CONSTRAINT `followers_whom_id_fkey` FOREIGN KEY (whom_id) REFERENCES `users(user_id)`


### Query Result: `SELECT * FROM users LIMIT 10;`

| user_id | username |    email     | pw_hash                                                                                                                                                          |
|---------|----------|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1       | user1    | user1@web.de | scrypt:32768:8:1$NjVoLMvwSW4x2sLK$69ac0d64f68a8d63b615359d6fa610ed217de7a81e558c654924c4d3d4bbccc2315a0d0cf1ce020a5a206a8356b4eb706ae25ae220b01826d95b00dc097d827c |
| 2       | user2    | user2@web.de | scrypt:32768:8:1$u5kldzFkqRheH9J6$94cbd7eecad93f524d2be3cb8ded625eed55030238eeac19bfcb9ef20dde94c806e6a63b727e799d6166bf01e704d65c68199463c8aec7709b3adec8326180a4 |

(2 rows)


---
### Table `public.latest`

after curl:

```
curl -X POST "http://localhost:5000/api/register?latest=1337" \
     -H "Content-Type: application/json" \
     -H "Authorization: Basic c2ltdWxhdG9yOnN1cGVyX3NhZmUh" \
     -d '{
           "username": "test",
           "email": "test@test",
           "pwd": "foo"
         }'
```

| id  | value    |
|----------|---------|
| 1  | 1337 |