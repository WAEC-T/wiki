# REQUIREMENTS SPECIFICATION

## GENERAL SCHEMA REQUIREMENTS
1. All applications need to adhere to the table names within the schema
2. 

## SPECIFIC TABLE REQUIREMENTS
### Messages
1. Every message should adhere to the following types within the db-schema and not be null.
- message_id: Integer (PRIMARY KEY)
- author_id: Integer
- text: String
- pub_date: String || DateTime 
- flagged: Integer

2. The types of the schema should adhere to most idiomatic standard (fx. message_id -> Integer).

### Users
1. When creating users the password must be hashe
### Followers
...
### Latest
1. The database must have a _latest_ relation/table with the following type:
- id: Integer (always 1)
- val: Integer
  
## ENDPOINT REQUIREMENTS
1. The given application must adhere to following endpoints
- /register POST
- /msgs GET
- /msgs/{username} GET | POST
- /fllws/{username} GET | POST
- /latest GET

## PORT REQUIREMENTS
All applications must:
1. Use port 5000:5000 for _both_ the web-application and API service.
2. Provide an /api endpoint
3. No "/" must direct to the web-application (GET)

### /latest endpoint
...
### /register endpoint
...
### /msgs endpoint
...
### /msgs/{username} endpoint
1. The body must contain a JSON-objecy with a key called "content" containing a message of type string.
### /fllws/{username} endpoint
...
### 
...
 

## NICE TO HAVE BUT NOT NEEDED
1. All ids should maybe uuids since that is the most idiomatic
2. All web-applications should display the same datetime format
3. 
