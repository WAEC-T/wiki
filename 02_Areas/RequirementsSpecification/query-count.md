# API Query Count Comparison

## API Endpoints

| API                 | /register | /latest | /msgs | /msgs/<username> (POST) | /msgs/<username> (GET) | /follow/<username> (GET) | /follow/<username> |
|---------------------|-----------|---------|-------|--------------------------|-------------------------|---------------------------|---------------------|
| go-gin                | 2 → 3     | 1       | 2     | 3                        | 3                     | 3                         | 4                   |
| python-flask          | 4 → 3     | 2 → 1   | 3 → 2 | 4 → 3                     | 4 → 3                | 5 → 3                     | 5 → 4               |
| rust-actix            | 3         | 1       | 2     | 3                        | 3                     | 3                         | 1                   |
| go-gorilla            | 2 → 3     | 1       | 2     | 3                        | 3                     | 3                         | 4                   |
| c-sharp-razor         | 3         | 1       | 3     | 3                        | 3                     | 3                         | 4                   |
| **Final Query Count** | 3         | 1       | 2     | 3                        | 3                     | 3                         | 4                   |

---

## Page Endpoints 

| App                   | /public | /users/<username>/unfollow | /users/<username>/follow  | /register | /logout | /login | /add_message | /       | /username |
|-----------------------|---------|----------------------------|---------------------------|-----------|---------|--------|--------------|---------|-----------|
| go-gorilla            | 2       | 4                          | 2                         | 2         | 0       | 3 → 1  | 2            | 3 → 2   | 4         |
| python-flask          | 2       | 4                          | 3 → 2                     | 3 → 2     | 1 → 0   | 2 → 1  | 2            | 2       | 4         |
| rust-actix            | 2       | 4                          | 2                         | 2         | 0       | 2 → 1  | 2            | 2       | 4         |  
| go-gin                | 2       | 4                          | 2                         | 2         | 0       | 3 → 1  | 2            | 3 → 2   | 4         |
| **Final Query Count** | 2       | 4                          | 2                         | 2         | 0       | 1      | 2            | 2       | 4         | 