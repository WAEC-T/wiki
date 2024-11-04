1. POST /register

Expected Input
Headers:
Content-Type: application/json
Authorization: Basic <base64_encoded_credentials>
Data (JSON body):
json
Code kopieren
{
  "username": "<username>",
  "email": "<email>",
  "pwd": "<password>"
}
Query Parameters:
latest: Integer value to set the latest state.
Expected Behavior
Register a new user with the provided username, email, and password.
Update the latest value in the database to match the provided latest parameter.
Expected Response
Status Code: 200 OK (if registration is successful).
Validation: After registration, the latest value should reflect the newly provided value.