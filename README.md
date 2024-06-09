<div align="center"><b><h1>HotDev - A Job Portal Web Application</h1></b></div>

Welcome to the Job Portal Web Application - an innovative and comprehensive solution designed to revolutionize the way job recruitment is managed. In today's fast-paced job market, navigating the complexities of hiring and job searching can be overwhelming. Our Job Portal Web Application bridges the gap between employers and job seekers by providing a seamless interface that enhances communication, efficiency, and transparency.

Our system is meticulously crafted to handle the diverse needs of job recruitment. Whether it's posting job openings, managing applications, or tracking the progress of job applications, our portal automates these processes to save time and reduce errors. By leveraging modern technologies like Spring Boot and MySQL, we ensure a robust and user-friendly experience for both employers and job seekers.
Key features of the Society Management System include:
<li><strong><ins>User-Friendly Interface:</ins></strong> A simple and intuitive design that facilitates easy navigation for all users.</li>
<li><strong><ins>Job Posting and Management:</ins></strong> Allows employers to post new job openings, view and manage job postings, and track applications received.</li>
<li><strong><ins>Profile Management:</ins></strong> Both employers and job seekers can edit their profiles and upload necessary documents like resumes and company profiles.</li>
<li><strong><ins>Automated Notifications:</ins></strong> Keeps users informed about application status changes and new job postings through automated notifications.</li>
<br>
This Job Portal Web Application is a testament to how technology can simplify and streamline the recruitment process, making it easier for both employers and job seekers. Dive into the details of our project to discover how our application can transform your recruitment process, bringing efficiency, reliability, and convenience to your job search and hiring needs.

<h2>Table of Contents</h2>
<ul>
  <li><a href="#purpose">Purpose</a></li>
  <li><a href="#key-features">Key Features</a></li>
  <li><a href="#technologies-used">Technologies used</a></li>
  <li><a href="#getting-started">Getting Started</a></li>
  <li><a href="#usage">Usage</a></li>
  <li><a href="#screenshots">Screenshots</a></li>
  <li><a href="#contributing">Contributing</a></li>
</ul>

<h2 id="purpose">Purpose</h2>
<p>The purpose of this project is to facilitate job recruitment processes by providing a platform where recruiters can post job vacancies and job seekers can find and apply for jobs. It streamlines the job application and hiring process.</p>

<h2 id="key-features">Key Features</h2>

### Application Architecture :-
![Screenshot 2024-06-09 123034](https://github.com/Manishn18/Society-Management/assets/87479740/a7dde62d-4628-4a87-9fea-e7eb25f65549)

#### Overall Flow of the Job Portal Project :- 
<ul>
<li><strong><ins>Web Browser :</ins></strong></li>
<ul>
  The user's interaction with the application starts here. Users can perform actions such as searching for jobs, applying for jobs, posting job openings, and managing profiles through the web browser.
</ul>
<br>
<li><strong><ins>Controller Layer :</ins></strong></li>
<ul>
  <li><strong><ins>Role:-</ins></strong> The controller handles web requests from the user. It acts as an intermediary between the web browser and the service layer.</li>
  <li><strong><ins>Function:-</ins></strong> When a user sends a request (e.g., searching for a job), the controller receives the request, processes it, and delegates the business logic to the service layer.</li>
  <li><strong><ins>Example:-</ins></strong> A request to search for jobs would be handled by a controller method that processes the search parameters and forwards them to the appropriate service method.</li>
</ul>
<br>
<li><strong><ins>Service Layer :</ins></strong></li>
<ul>
  <li><strong><ins>Role:-</ins></strong> The service layer contains the business logic of the application. It acts as a bridge between the controller and the repository layer.</li>
  <li><strong><ins>Function:-</ins></strong> The service processes data and applies business rules. It retrieves data from the repository, processes it, and returns the results to the controller.</li>
  <li><strong><ins>Example:-</ins></strong> The service layer might contain methods to filter job listings based on user search criteria or to handle job applications by saving the application details to the database.</li>
</ul>
<br>  
<li><strong><ins>Repository Layer :</ins></strong></li>
<ul>
  <li><strong><ins>Role:-</ins></strong> The repository layer is responsible for data access and storage. It interacts with the database to perform CRUD (Create, Read, Update, Delete) operations.</li>
  <li><strong><ins>Function:-</ins></strong> The repository retrieves data from the database and returns it to the service layer. It also saves or updates data in the database based on requests from the service layer.</li>
  <li><strong><ins>Example:-</ins></strong> The repository might have methods to fetch job listings from the database or to save a new job posting created by an employer.</li>
</ul>
<br>  
<li><strong><ins>Database :</ins></strong></li>
<ul>
  The repository layer communicates with the database to store and retrieve data. This could include job listings, user profiles, applications, and other relevant information.
</ul>
<br>  
<li><strong><ins>Thymeleaf Templates :</ins></strong></li>
<ul>
  <li><strong><ins>Role:-</ins></strong> Thymeleaf templates are used to render the view. They are responsible for displaying the user interface that the user interacts with.</li>
  <li><strong><ins>Function:-</ins></strong> The controller passes the processed data to the Thymeleaf templates, which then generate the HTML pages that are sent back to the web browser.</li>
  <li><strong><ins>Example:-</ins></strong> A search result page showing job listings or a dashboard displaying user-specific information would be rendered using Thymeleaf templates.</li>
</ul>
<br>  
</ul>

### Database Diagram :-
![Screenshot 2024-06-09 122645](https://github.com/Manishn18/Society-Management/assets/87479740/3adfdd6c-9574-46bb-8c43-64678cc5edc2)

#### 1. `users`
- **Columns:**
  - `user_id`: INT, primary key
  - `email`: VARCHAR(255)
  - `is_active`: BIT(1)
  - `password`: VARCHAR(255)
  - `registration_date`: DATETIME(6)
  - `user_type_id`: INT, foreign key
- **Description:** Stores the general information of all users (both recruiters and job seekers).
- **Relationships:** 
  - Many-to-one relationship with `users_type` (indicated by `user_type_id`).

#### 2. `users_type`
- **Columns:**
  - `user_type_id`: INT, primary key
  - `user_type_name`: VARCHAR(255)
- **Description:** Defines the types of users (e.g., recruiter, job seeker).

#### 3. `recruiter_profile`
- **Columns:**
  - `user_account_id`: INT, primary key, foreign key referencing `users(user_id)`
  - `city`: VARCHAR(255)
  - `company`: VARCHAR(255)
  - `country`: VARCHAR(255)
  - `first_name`: VARCHAR(255)
  - `last_name`: VARCHAR(255)
  - `profile_photo`: VARCHAR(64)
  - `state`: VARCHAR(255)
- **Description:** Stores detailed information specific to recruiters.
- **Relationships:** 
  - One-to-one relationship with `users` (indicated by `user_account_id`).

#### 4. `job_post_activity`
- **Columns:**
  - `job_post_id`: INT, primary key
  - `description_of_job`: VARCHAR(1000)
  - `job_title`: VARCHAR(255)
  - `job_type`: VARCHAR(255)
  - `posted_date`: DATETIME(6)
  - `remote`: VARCHAR(255)
  - `salary`: VARCHAR(255)
  - `job_company_id`: INT, foreign key
  - `job_location_id`: INT, foreign key
  - `posted_by_id`: INT, foreign key referencing `users(user_id)`
- **Description:** Contains information about job postings created by recruiters.
- **Relationships:**
  - Many-to-one relationship with `job_company` (indicated by `job_company_id`).
  - Many-to-one relationship with `job_location` (indicated by `job_location_id`).
  - Many-to-one relationship with `users` (indicated by `posted_by_id`).

#### 5. `job_company`
- **Columns:**
  - `id`: INT, primary key
  - `logo`: VARCHAR(255)
  - `name`: VARCHAR(255)
- **Description:** Stores information about companies.

#### 6. `job_location`
- **Columns:**
  - `id`: INT, primary key
  - `city`: VARCHAR(255)
  - `country`: VARCHAR(255)
  - `state`: VARCHAR(255)
- **Description:** Stores information about job locations.

#### 7. `job_seeker_profile`
- **Columns:**
  - `user_account_id`: INT, primary key, foreign key referencing `users(user_id)`
  - `city`: VARCHAR(255)
  - `country`: VARCHAR(255)
  - `employment_type`: VARCHAR(255)
  - `first_name`: VARCHAR(255)
  - `last_name`: VARCHAR(255)
  - `profile_photo`: VARCHAR(255)
  - `resume`: VARCHAR(255)
  - `state`: VARCHAR(255)
  - `work_authorization`: VARCHAR(255)
- **Description:** Stores detailed information specific to job seekers.
- **Relationships:**
  - One-to-one relationship with `users` (indicated by `user_account_id`).

#### 8. `job_seeker_apply`
- **Columns:**
  - `id`: INT, primary key
  - `apply_date`: DATETIME(6)
  - `cover_letter`: VARCHAR(255)
  - `job`: INT, foreign key referencing `job_post_activity(job_post_id)`
  - `user_id`: INT, foreign key referencing `users(user_id)`
- **Description:** Records applications made by job seekers to job postings.
- **Relationships:**
  - Many-to-one relationship with `job_post_activity` (indicated by `job`).
  - Many-to-one relationship with `users` (indicated by `user_id`).

#### 9. `job_seeker_save`
- **Columns:**
  - `id`: INT, primary key
  - `job_id`: INT, foreign key referencing `job_post_activity(job_post_id)`
  - `user_id`: INT, foreign key referencing `users(user_id)`
- **Description:** Records jobs saved by job seekers for later reference.
- **Relationships:**
  - Many-to-one relationship with `job_post_activity` (indicated by `job_id`).
  - Many-to-one relationship with `users` (indicated by `user_id`).

#### 10. `skills`
- **Columns:**
  - `id`: INT, primary key
  - `experience_level`: VARCHAR(255)
  - `name`: VARCHAR(255)
  - `years_of_experience`: VARCHAR(255)
  - `job_seeker_profile_id`: INT, foreign key referencing `job_seeker_profile(user_account_id)`
- **Description:** Stores skills information associated with job seekers.
- **Relationships:**
  - Many-to-one relationship with `job_seeker_profile` (indicated by `job_seeker_profile_id`).

### Relationships Summary
- `users` table is central to both `recruiter_profile` and `job_seeker_profile`.
- `job_post_activity` is linked to `job_company`, `job_location`, and `users`.
- `job_seeker_apply` and `job_seeker_save` track interactions between job seekers and job postings.
- `skills` are associated with `job_seeker_profile`.

This schema provides a clear separation of user roles, job postings, applications, and company details, ensuring a well-structured database for the Job Portal Web Application.

<h2 id="technologies-used">Technologies used</h2>

### Backend Technologies

#### 1. Spring Boot 3
- **Description:** Spring Boot 3 is a powerful framework that simplifies the development of Java applications. It provides a comprehensive infrastructure for developing enterprise applications.
- **Role in Project:** Spring Boot 3 is used to create the backend services, manage dependencies, and facilitate easy configuration and deployment of the application.

#### 2. Spring MVC
- **Description:** Spring MVC (Model-View-Controller) is a framework for building web applications that follow the MVC design pattern.
- **Role in Project:** Spring MVC is used to handle HTTP requests and responses, process form submissions, and manage the overall flow of the application.

#### 3. Spring Security
- **Description:** Spring Security is a powerful and highly customizable authentication and access-control framework for Java applications.
- **Role in Project:** Spring Security is used to secure the application by handling user authentication, authorization, and other security-related aspects.

#### 4. Spring Data JPA
- **Description:** Spring Data JPA is a part of the Spring Data family that makes it easy to implement JPA-based repositories.
- **Role in Project:** Spring Data JPA is used for data persistence and retrieval, simplifying database interactions by reducing boilerplate code.

#### 5. Hibernate/JPA
- **Description:** Hibernate is an ORM (Object-Relational Mapping) framework that implements JPA (Java Persistence API) for data persistence.
- **Role in Project:** Hibernate/JPA is used to map Java objects to database tables and perform CRUD operations, enabling seamless interaction with the database.

#### 6. MySQL Database
- **Description:** MySQL is an open-source relational database management system.
- **Role in Project:** MySQL is used to store all the data related to users, job postings, applications, and other relevant information, ensuring data integrity and supporting complex queries.

### Frontend Technologies

#### 1. Thymeleaf
- **Description:** Thymeleaf is a modern server-side Java template engine for web and standalone environments capable of processing HTML, XML, JavaScript, CSS, and even plain text.
- **Role in Project:** Thymeleaf is used as the view layer in the MVC (Model-View-Controller) architecture. It integrates seamlessly with Spring Boot and allows for the dynamic rendering of HTML pages based on data passed from the controllers.

- <h2 id="getting-started">Getting Started</h2>
To get started with the HotDev, follow these steps to set up the development environment and run the application locally.
### Prerequisites
Ensure you have the following software installed on your system:
- Java Development Kit (JDK) 8 or higher
- Maven 3.x
- MySQL Database Server
- An IDE like IntelliJ IDEA or Eclipse

### Installation
1. Clone the repository:
   
    ```bash
    git clone https://github.com/yourusername/job-portal-web-application.git
    cd job-portal-web-application
    ```
<br>

2. Set up the MySQL database:
   
    ```sql
    CREATE DATABASE jobportal;
    CREATE USER 'jobportal'@'localhost' IDENTIFIED BY 'jobportal';
    GRANT ALL PRIVILEGES ON jobportal.* TO 'jobportal'@'localhost';
    FLUSH PRIVILEGES;
    ```
<br>

3. Configure the Application Properties: Ensure that the src/main/resources/application.properties file has the correct database configuration:
   
   ```bash
   spring.datasource.url=jdbc:mysql://localhost:3306/jobportal
   spring.datasource.username=jobportal
   spring.datasource.password=jobportal
   spring.jpa.hibernate.ddl-auto=update
   ```
<br>   

4. Run the SQL scripts located in `src/main/resources/sql` to set up the database schema:
   
    ```bash
    mysql -u jobportal -p jobportal < src/main/resources/sql/00-create-user.sql
    mysql -u jobportal -p jobportal < src/main/resources/sql/01-jobportal.sql
    ```
<br>

5. Build and run the application:
   
    ```bash
    mvn clean install
    mvn spring-boot:run
    ```
<br>

6. Access the application: Open your web browser and navigate to -
   
   ```
   http://localhost:8080
   ```
<br>

<h2 id = "usage">Usage</h2>

- Access the application at `http://localhost:8080`.<br>
- Register as a new user (recruiter or candidate).<br>
- Log in to access the respective dashboards.<br>
- Recruiters can post job openings and view applications.<br>
- Candidates can search for jobs and apply.

<h2 id = "screenshots">Screenshots</h2>

#### Home Page
![Screenshot 2024-06-09 172940](https://github.com/Manishn18/Society-Management/assets/87479740/6ffcef34-bc0b-4d98-a1b4-68b4bab59b3d)

#### Candidate Registration Page
![Screenshot 2024-06-09 173124](https://github.com/Manishn18/Society-Management/assets/87479740/760c4da5-80b0-4f56-b389-ab476719e49e)

#### Candidate Login Page
![Screenshot 2024-06-09 173245](https://github.com/Manishn18/Society-Management/assets/87479740/78173f40-2c75-4e30-93a6-c28f8d4d5aad)

#### Candidate Set up Profile
![Screenshot 2024-06-09 194954](https://github.com/Manishn18/Society-Management/assets/87479740/6fabd380-407d-430e-9f43-516863e034b0)

#### Candidate Dashboard
![Screenshot 2024-06-09 195508](https://github.com/Manishn18/Society-Management/assets/87479740/432dcc52-4c4d-4df6-bb92-8fc440b03dbb)

#### Candidate Job Details Page
![Screenshot 2024-06-09 195626](https://github.com/Manishn18/Society-Management/assets/87479740/552308ce-0692-4611-971d-1ee9667e4628)

#### Recruiter Registration Page
![Screenshot 2024-06-09 201947](https://github.com/Manishn18/Society-Management/assets/87479740/493ee020-a774-41c3-ac97-7ac2276d9de8)

## Recruiter Login Page
![Screenshot 2024-06-09 202144](https://github.com/Manishn18/Society-Management/assets/87479740/9b211851-a5f9-4e45-913e-15c04f6d3e72)

### Recruiter Set up Profile
![Screenshot 2024-06-09 202320](https://github.com/Manishn18/Society-Management/assets/87479740/c890461a-ff41-464d-8202-462c266ae0dc)

#### Recruiter Dashboard
![Screenshot 2024-06-09 202630](https://github.com/Manishn18/Society-Management/assets/87479740/8aa7dcc5-2825-455c-b5da-b70085d3541c)

#### Recruiter Post New Job
![Screenshot 2024-06-09 202742](https://github.com/Manishn18/Society-Management/assets/87479740/9ce77f55-3b84-4887-8d2b-374daeb63cba)

<h2 id="contributing">Contributing</h2>
Contributions to HotDev - A Job Portal Web Application are welcomed!
