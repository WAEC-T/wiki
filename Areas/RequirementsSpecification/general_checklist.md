
### 1. Schema and Tables
- [ ] All applications must have the table names within the schema.
- [ ] The types of the schema should follow the most idiomatic standard (e.g. message_id -> Integer).
- [ ] Password hashing in line with the framework
- [ ] latest for the api call is `id=1 and value=integer`
- [ ] pub_date uses the supplied TIMESTAMP format without the timezone format.

### 2. Endpoint Requirements 
- [ ]  The given application must adhere to following endpoints:
   * `/register [POST]`
   * `/msg [GET]`
   * `/msg/<username> [GET]&[POST]`
   * `/fllws/<username> [GET]&[POST]`
   * `/latest [GET]`
- [ ] msg renders limit 100 messages

### 3. Ports 
- [ ] Use port 5000:5000 for _both_ the web application and the API service.
- [ ] The given application provides an `\api` endpoint
- [ ] "/" must point to the web application

### 4. Redirects
- [ ] successful register redirects to...
- [ ] successful login redirects to...
- [ ] successful logout redirects to...
- [ ] successful follow redirects to...
- [ ] successful unfoloow redirects to...
