# springboot-postgresql-jpa-hibernate-crud-example
Spring Boot + Spring Data JPA + PostgreSQL Example

Use spring initializr to create a new Spring boot project with the name: springboot-postgresql-jpa-hibernate-crud-example
Add postgres, JPA, web, Thymeleaf as dependency
Check Maven Dependencies - pom.xml file
Configure PostgreSQL Database in application.properties file 
Create JPA Entity - Employee.java
Create Spring Data Repository - EmployeeRepository.java
Create Spring Rest Controller - EmployeeController.java
Create Exception(Error) Handling for RESTful Services - ResourceNotFoundException
Customizing Error Response Structure - ErrorDetails
Create GlobalExceptionHandler Class
Running Application
 
1. Get all Employees REST API
The GET method is used to retrieve data from the server
HTTP Method: GET 
Request URL: http://localhost:8080/api/v1/employees
Output:
[
    {
        "id": 1,
        "firstName": "ram",
        "lastName": "kumar",
        "emailId": "ramkumar@gmail.com"
    },
    {
        "id": 2,
        "firstName": "siva",
        "lastName": "kumar",
        "emailId": "sivakumar@gmail.com"
    },
    {
        "id": 3,
        "firstName": "ramesh",
        "lastName": "kumar",
        "emailId": "rameshkumar@gmail.com"
    }
]

2. Get Employee by ID REST API
HTTP Method: GET 
Request URL: http://localhost:8080/api/v1/employees/1
Output:
{
    "id": 1,
    "firstName": "ram",
    "lastName": "kumar",
    "emailId": "ramkumar@gmail.com"
}

1. Create Employee REST API
The POST method sends data to the server and creates a new resource. 
Important:
Use @GeneratedValue(strategy = GenerationType.SEQUENCE)
In Emplyee POJO class for Primary key id
Instead of 
@GeneratedValue(strategy = GenerationType.IDENTITY) 
HTTP Method: POST 
Request URL: http://localhost:8080/api/v1/employees 
Input: Body -> raw
{
"firstName": "kumarx",
"lastName": "satheesx",
"emailId": " kumarxsatheesx@gmail.com"
}

Ouptut:
{
    "id": 53,
    "firstName": "kumarx",
    "lastName": "satheesx",
    "emailId": " kumarxsatheesx@gmail.com"
}
4. Update Employee REST API
HTTP Method: GET 
Request URL: http://localhost:8080/api/v1/emploees/1
{
    "id": 1,
    "firstName": "ram",
    "lastName": "kumar",
    "emailId": "ramkumar@gmail.com"
}


The PUT method is most often used to update an existing resource.
HTTP Method: PUT 
Request URL: http://localhost:8080/api/v1/emploees/1

{
    "firstName": "ramx",
    "lastName": "kumarx",
    "emailId": "ramxkumarx@gmail.com"
}
The DELETE method is used to delete a resource specified by its URI.
5. Delete Employee REST API
HTTP Method: DELETE 
Request URL: http://localhost:8080/api/v1/employees/1
{
    "deleted": true
}


-- Table: public.employees

-- DROP TABLE IF EXISTS public.employees;

CREATE TABLE IF NOT EXISTS public.employees
(
    id bigint NOT NULL,
    first_name text COLLATE pg_catalog."default" NOT NULL,
    last_name text COLLATE pg_catalog."default" NOT NULL,
    email_address text COLLATE pg_catalog."default" NOT NULL,
    CONSTRAINT employees_pkey PRIMARY KEY (id)
)

TABLESPACE pg_default;

ALTER TABLE IF EXISTS public.employees
    OWNER to postgres;

select * from employees;
