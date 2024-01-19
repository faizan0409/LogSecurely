# LogSecurely |  Spring Boot Project

# Login and Signup Backend API with Security and JWT Tokens


### 1. Clone the Repository

```
git clone https://github.com/faizan0409/LogSecurely.git
```

### 2. Go the Project

```
cd LogSecurely/LogSecurely

```

### 3. Run the Application
- For GitBash
```
./mvnw spring-boot:run

```
**The application will start running on [http://localhost:8081](http://localhost:8081)**

### **API Endpoints**

### User Signup

- Method: POST
- Path: `http://localhost:8081/app/signup`
- Description: Register a new user.
- Request Body: User data in the JSON format (e.g., name, email, password).

```

{
  "fullName": "Faizan Ansari",
  "password": "faizan@123",
  "email": "faizan@gmail.com"
}
```

- Response:

```
{
    "id": 1,
    "fullName": "Faizan Ansari",
    "password": "$2a$10$KVzpEHKFpX2ephA7RXLgqumnZKFy3bT8wdJMW3tYH2yqUJcpZPGSG",
    "email": "faizan@gmail.com",
    "role": "ROLE_USER"
}

```

### User Login

- Method: GET
- Path: `http://localhost:8081/signIn`
- Description: Authenticate a user and retrieve their details.
- Authentication: Basic Authentication (Username and Password)
    - Username: [faizan@gmail.com](mailto:faizan@gmail.com)
    - Password: faizan@123
- Response:

```
{
    "id": 1,
    "fullName": "Faizan Ansari",
    "password": "$2a$10$KVzpEHKFpX2ephA7RXLgqumnZKFy3bT8wdJMW3tYH2yqUJcpZPGSG",
    "email": "faizan@gmail.com",
    "role": "ROLE_USER"
}

```

### Welcome Endpoint (Requires Authentication)

- Method: GET
- Path: `http://localhost:8081/logged-in/user`
- Description: A protected endpoint that requires authentication to access.
- Authentication: Bearer Token
- Request Header:
    - Authorization: Bearer <token>
- Response: A welcome message string.
- Example:
    - Bearer Token: eyJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJTaGltYmh1Iiwic3ViIjoiSldUIFRva2VuIiwidXNlcm5hbWUiOiJza0BnbWFpbC5jb20iLCJyb2xlIjoiUk9MRV9VU0VSIiwiaWF0IjoxNjg1Njc3Mzg3LCJleHAiOjE2ODU3MDczODd9.VwM2IGD1fABjEcnNoMb4uIyBnYe3_BmZGx33dElaD-E
    - Response: Welcome to Faizan's Website: Faizan Ansari

### Technolgy Stacks

- Java
- Spring Boot
- H2 Database
- Spring Security
- JWT Token
- Lombok
- Maven

### Validation Rules

The following validation rules are applied to the user entity:

- Full Name:
    - Minimum length: 3 characters
    - Maximum length: 20 characters
- Password:
    - At least 8 characters
    - Contains at least one digit
    - Contains at least one lowercase letter
    - Contains at least one uppercase letter
    - Contains at least one special character
- Email:
    - Valid email format - Regular Expression


## H2 Database Configuration

The project uses the H2 in-memory database by default.

The application is configured to use the H2 database. The configuration can be found in the `application.properties` file:

```
# Server Port Configuration
server.port=8081

# H2 Database Configuration
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=faizan
spring.datasource.password=
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console

```
