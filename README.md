# airbnb-clone-project

## Team Roles

| Role | Responsibility |
|------|----------------|
| **Backend Developer** | Implements the core logic of the application, develops API endpoints, integrates the database, and ensures business rules are followed. |
| **Database Administrator (DBA)** | Designs the database schema, manages data integrity, optimizes queries, handles backups and performance tuning. |
| **DevOps Engineer** | Manages deployment, configures CI/CD pipelines, handles infrastructure, monitors performance, and ensures uptime. |
| **QA Engineer** | Writes and runs test cases, performs integration and regression testing, ensures all features meet quality standards and requirements. |
| **Project Manager (Optional)** | Oversees project timelines, coordinates between team members, manages resources and ensures delivery milestones are met. |
| **UI/UX Designer (Optional)** | Designs intuitive and user-friendly interfaces that enhance the user experience across all platforms. |

---

## Technology Stack

| Technology | Purpose in the Project |
|------------|------------------------|
| **Django** | A high-level Python web framework used to build secure, scalable backend services and APIs. |
| **Django REST Framework** | A toolkit for building robust and customizable REST APIs with Django. |
| **PostgreSQL** | A powerful open-source relational database used to store application data. |
| **GraphQL** | A query language for APIs that enables clients to request exactly the data they need, improving efficiency. |
| **Celery** | A task queue used for handling asynchronous and scheduled background tasks (e.g., sending emails, processing payments). |
| **Redis** | An in-memory key-value store used for caching, message brokering, and session management. |
| **Docker** | A containerization platform that packages the application and its dependencies to ensure consistent deployment across environments. |
| **CI/CD Pipelines** | Automates testing, integration, and deployment of code to improve development efficiency and reliability. |

---

## Database Design

### Entities and Key Fields

- **User**
  - `id`: Unique identifier
  - `name`: Full name
  - `email`: Email address
  - `password`: Hashed password
  - `is_host`: Boolean to distinguish hosts from regular users

- **Property**
  - `id`: Unique identifier
  - `title`: Name of the property
  - `description`: Detailed information about the listing
  - `location`: Geographic location
  - `price_per_night`: Cost per night

- **Booking**
  - `id`: Unique identifier
  - `user_id`: Foreign key to User
  - `property_id`: Foreign key to Property
  - `check_in_date`: Date
  - `check_out_date`: Date

- **Review**
  - `id`: Unique identifier
  - `user_id`: Foreign key to User
  - `property_id`: Foreign key to Property
  - `rating`: Numeric score
  - `comment`: Text feedback

- **Payment**
  - `id`: Unique identifier
  - `booking_id`: Foreign key to Booking
  - `amount`: Payment amount
  - `status`: Payment status
  - `timestamp`: Time of transaction

### Relationships

- A **User** can own multiple **Properties**.
- A **User** can create multiple **Bookings**.
- Each **Booking** is associated with one **User** and one **Property**.
- **Reviews** are written by Users about Properties.
- Each **Payment** is linked to a Booking.

---

## Feature Breakdown

- **User Management**
  - Allows users to sign up, log in, manage profiles, and toggle host status. Critical for authentication and user-specific operations.

- **Property Management**
  - Enables hosts to create, update, and delete listings. Provides search and filter functionality for renters.

- **Booking System**
  - Lets users book available properties with date validation and availability checks. Handles reservation logic.

- **Reviews and Ratings**
  - Users can leave feedback on stays. These ratings help maintain quality and transparency on the platform.

- **Payment Processing**
  - Handles secure transactions for bookings using background processing with Celery. Ensures financial data is handled safely.

- **Admin Panel**
  - Provides an interface for admins to manage users, properties, and bookings efficiently using Django Admin.

---

## API Security

- **Authentication**
  - Use of JWT or session-based authentication to verify user identity.

- **Authorization**
  - Ensures that only permitted users can access or modify certain resources (e.g., only property owners can edit their properties).

- **Rate Limiting**
  - Prevents abuse by limiting the number of API requests from a single user or IP in a given time frame.

- **Input Validation & Data Sanitization**
  - Prevents common attacks like SQL injection and XSS by cleaning all inputs.

- **Importance**
  - Protecting user accounts, sensitive data, and payments is critical for user trust and platform integrity.

---