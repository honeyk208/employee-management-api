# employee-mgmt
API for managing employees
Employee Management API
This is a Spring Boot application for managing employees, implementing various functionalities like authentication, role-based access control, logging, caching, and more. The application includes API documentation through Swagger UI and OpenAPI and leverages multiple design patterns to make the application modular and maintainable.

Table of Contents
Project Description
Features
Setup Instructions
Design Choices
Technologies Used
API Documentation
License
Project Description
This project is an Employee Management System where users can:

Register new employees
View employee details
Search employees by name, department, and skills
Manage employees with role-based access (Admin/User)


#Setup Instructions
1. Clone the Repository

git clone https://github.com/your-username/employee-management-api.git
cd employee-management-api

2. Install Dependencies
   mvn clean install
   
3. Configure Redis (Optional)
   spring.redis.host=localhost
  spring.redis.port=6379
4. Run the Application
   mvn spring-boot:run
5. Access Swagger UI
http://localhost:8080/swagger-ui.html


Design Choices
1. JWT Authentication:
The application uses JWT (JSON Web Token) for authentication. This ensures that:

API access is secure and only authenticated users can perform actions.
The token-based system is stateless, meaning the server doesn't need to store session data.
2. Role-based Access Control:
The system uses Spring Security to implement role-based access:

Admins: Can create, update, and delete employee data.
Users: Can only view employee data.
3. Caching with Redis:
Caching was implemented using Redis to optimize the performance of the GET /employees endpoint. This reduces unnecessary database queries and improves response time for frequently accessed data.
4. Design Patterns:
Builder Pattern: Used for constructing Employee objects in a flexible way, especially when dealing with multiple optional attributes.
5. AOP for Logging and Audit Trail:
Aspect-Oriented Programming (AOP) was used to intercept method calls and log execution details.


You can interact with the API using Swagger UI:

Base URL: http://localhost:8080
Endpoints:
POST /auth/login: Login and get a JWT token.
GET /employees: Retrieve all employees (admin and user access).
GET /employees/{id}: Retrieve a specific employee by ID (admin and user access).
POST /employees: Create a new employee (admin only).
PUT /employees/{id}: Update an employee (admin only).
DELETE /employees/{id}: Delete an employee (admin only).
GET /employees/search: Search employees by name, department, and skills.


