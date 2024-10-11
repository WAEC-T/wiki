### 1. **Get Latest Command**

```bash
bash
Code kopieren
curl -X GET "http://localhost:5000/api/latest" \
     -H "Authorization: Basic c2ltdWxhdG9yOnN1cGVyX3NhZmUh"

```

### 2. **Register User**

```bash
curl -X POST "http://localhost:5000/api/register?latest=1" \
     -H "Authorization: Basic c2ltdWxhdG9yOnN1cGVyX3NhZmUh" \
     -H "Content-Type: application/json" \
     -d '{
           "username": "newuser",
           "email": "newuser@example.com",
           "pwd": "password123"
         }'

```

### 3. **Get Messages from Public Timeline**

```bash
curl -X GET "http://localhost:5000/api/msgs?latest=1&no=100" \
     -H "Authorization: Basic c2ltdWxhdG9yOnN1cGVyX3NhZmUh"

```

### 4. **Get User Messages**

```bash
curl -X GET "http://localhost:5000/api/msgs/newuser?latest=1&no=100" \
     -H "Authorization: Basic c2ltdWxhdG9yOnN1cGVyX3NhZmUh"

```

### 5. **Post Message**

```bash
curl -X POST "http://localhost:5000/api/msgs/newuser?latest=1" \
     -H "Authorization: Basic c2ltdWxhdG9yOnN1cGVyX3NhZmUh" \
     -H "Content-Type: application/json" \
     -d '{
           "content": "Hello, this is my message!"
         }'

```

### 6. **Get User Followers**

```bash
curl -X GET "http://localhost:5002/api/fllws/newuser?latest=1&no=20" \
     -H "Authorization: Basic c2ltdWxhdG9yOnN1cGVyX3NhZmUh"

curl -X GET "http://127.0.0.1:5000/api/fllws/aa?latest=1&no=20" \
     -H "Authorization: Basic c2ltdWxhdG9yOnN1cGVyX3NhZmUh"
     
     
   http://127.0.0.1:5000/

```

### 7. **Follow User**

```bash
curl -X POST "http://localhost:5000/api/fllws/newuser?latest=1" \
     -H "Authorization: Basic c2ltdWxhdG9yOnN1cGVyX3NhZmUh" \
     -H "Content-Type: application/json" \
     -d '{
           "follow": "test"
         }'

```

### 8. **Unfollow User**

```bash
curl -X POST "http://localhost:5000/api/fllws/newuser?latest=1" \
     -H "Authorization: Basic c2ltdWxhdG9yOnN1cGVyX3NhZmUh" \
     -H "Content-Type: application/json" \
     -d '{
           "unfollow": "anotheruser"
         }'

```