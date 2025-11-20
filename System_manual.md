---
title: "U-Library System Manual"
author: "Samuel Baquero"
date: "2025-11-20"
output:
  md_document:
    variant: preserve_yaml
    markdown: true
---

# SYSTEM DOCUMENTATION — U‑Library

## 1. Project Information
Project Name: U‑Library — University Library Management System  
Student Name: [Your Name]  
Course: Software Development  
Semester: Sixth Semester  
Date: December 2024  
Instructor: [Instructor Name]

Short Project Description:  
A full web system for university library management to handle books, authors, students, loans, reservations, and reporting.

## 2. System Architecture Overview

### 2.1 Architecture Description
3‑tier client–server architecture:
- Frontend: Angular application (port 4200)
- Backend: Django REST API (port 8000)
- Relational database (PostgreSQL 15 or MySQL 8.0)

### 2.2 Technologies Used
- Frontend:
  - Angular 20.0.0
  - PrimeNG 20.3.0
  - Tailwind CSS 4.1.17
  - TypeScript 5.8.2
- Backend:
  - Django 5.2.7
  - Django REST Framework 3.15.2
  - Python 3.x
- Database Engine:
  - PostgreSQL 15 / MySQL 8.0
  - ORM: Django ORM
- Tools:
  - Git, Postman, Docker (optional), JWT auth

### 2.3 ASCII Architecture Diagram (No Images)
```

+----------------------- CLIENT BROWSER -----------------------+

| Angular Application (Port 4200) |
| --- |
| +------------------+   +----------------+   +------------+ |
|  |
| +------------------+   +----------------+   +------------+ |
| PrimeNG + Tailwind CSS UI |

+---------------------------|----------------------------------+

v  HTTP REST API (JSON)

+----------------------- DJANGO BACKEND -----------------------+

| REST API Layer |
| --- |
| +-----------+   +---------------+    +-------------------+ |
|  |
| +-----------+   +---------------+    +-------------------+ |
| Business Logic Layer |
| +--------+     +-------------+       +------------------+ |
|  |
|  |
| +--------+     +-------------+       +------------------+ |
| Django ORM (Abstraction) |

+---------------------------|----------------------------------+

v

+--------------------------- DATABASE LAYER -------------------+

| PostgreSQL | MySQL | MSSQL | Oracle | SQLite |
| --- | --- | --- | --- | --- |

+-------------------------------------------------------------+

```

## 3. Database Documentation (ENGLISH)

### 3.1 Database Description
Relational schema for cataloging, user management, and circulation.
Core entities: Book, Author, Student, Loan, BookCopy.  
Constraints and business rules enforced via API validation and DB constraints.

### 3.2 ERD — ASCII (No Images)
```

Book (id PK, isbn UNIQUE, title, publication_year, publisher_id FK, category_id FK)

| 1:N |
| --- |

v

BookCopy (id PK, copy_code, status, book_id FK)

Author (id PK, first_name, last_name, nationality, birth_date)

^ N:M via BookAuthor

|  |
| --- |

BookAuthor (book_id FK -> Book, author_id FK -> Author)  -- join table

Student (id PK, student_code UNIQUE, first_name, last_name, email UNIQUE, phone, career)

| 1:N |
| --- |

v

Loan (id PK, loan_date, due_date, return_date, status, student_id FK)

```

### 3.3 Logical Model
- Book(id, isbn, title, publication_year, publisher_id, category_id)
- Author(id, first_name, last_name, nationality, birth_date)
- Student(id, student_code, first_name, last_name, email, phone, career)
- Loan(id, loan_date, due_date, return_date, status, student_id)
- BookCopy(id, copy_code, status, book_id)
- BookAuthor(book_id, author_id)

### 3.4 Physical Model (Tables)
| Table     | Column            | Type            | PK/FK | Description                          |
|-----------|-------------------|-----------------|-------|--------------------------------------|
| books     | id                | SERIAL/INT      | PK    | Book identifier                      |
|           | isbn              | VARCHAR(13)     |       | Unique ISBN                          |
|           | title             | VARCHAR(200)    |       | Title                                |
|           | publication_year  | INTEGER         |       | Year                                 |
|           | publisher_id      | INT             | FK    | publishers(id)                       |
|           | category_id       | INT             | FK    | categories(id)                       |
| book_copy | id                | SERIAL/INT      | PK    | Copy identifier                      |
|           | copy_code         | VARCHAR         |       | Inventory code                       |
|           | status            | VARCHAR         |       | available, loaned, maintenance, lost |
|           | book_id           | INT             | FK    | books(id)                            |
| student   | id                | SERIAL/INT      | PK    | Student identifier                   |
|           | student_code      | VARCHAR         |       | Unique code                          |
|           | first_name        | VARCHAR         |       | First name                           |
|           | last_name         | VARCHAR         |       | Last name                            |
|           | email             | VARCHAR         |       | Unique email                         |
|           | phone             | VARCHAR         |       | Phone number                         |
|           | career            | VARCHAR         |       | Academic program                     |
| loan      | id                | SERIAL/INT      | PK    | Loan identifier                      |
|           | loan_date         | DATE/TIMESTAMP  |       | Start date                           |
|           | due_date          | DATE/TIMESTAMP  |       | Due date                             |
|           | return_date       | DATE/TIMESTAMP  |       | Date returned                        |
|           | status            | VARCHAR         |       | pending, active, returned, overdue   |
|           | student_id        | INT             | FK    | student(id)                          |

Example DDL (PostgreSQL):
```

CREATE TABLE books_book (

id SERIAL PRIMARY KEY,

isbn VARCHAR(13) UNIQUE NOT NULL,

title VARCHAR(200) NOT NULL,

publication_year INTEGER NOT NULL,

publisher_id INTEGER REFERENCES publishers_publisher(id),

category_id INTEGER REFERENCES categories_category(id)

);

```

## 4. Use Cases — CRUD

### 4.1 Use Case: Create Book
Actor: Librarian  
Preconditions: Valid ISBN and title.  
Postconditions: Book created and available for copy registration.  
Main Flow:
1. Click “New Book”.
2. Enter fields.
3. System checks uniqueness of ISBN.
4. System saves and returns confirmation.

### 4.2 Use Case: Read Book
- List supports pagination, filters, text search, and sorting.
- Detail view shows full metadata.

### 4.3 Use Case: Update Book
- Edit fields, validate, save.

### 4.4 Use Case: Delete Book
- Allowed when no blocking dependencies exist.

## 5. Backend Documentation

### 5.1 Backend Architecture
Django + DRF with ViewSets, Serializers, URL routing, and JWT authentication.

### 5.2 Folder Structure
```

backend/

├── apps/

│   ├── books/

│   │   ├── [models.py](http://models.py)

│   │   ├── [views.py](http://views.py)

│   │   ├── [serializers.py](http://serializers.py)

│   │   └── [urls.py](http://urls.py)

│   ├── students/

│   └── loans/

├── config/

│   ├── [settings.py](http://settings.py)

│   └── [urls.py](http://urls.py)

└── [manage.py](http://manage.py)

```

### 5.3 API Documentation (REST)
Books
- `GET /api/books/` — List books
- `POST /api/books/` — Create book
- `GET /api/books/{id}/` — Retrieve book
- `PUT /api/books/{id}/` — Update book
- `DELETE /api/books/{id}/` — Delete book

Loans
- `POST /api/loans/` — Create loan
- `PUT /api/loans/{id}/return/` — Return book copy

Students
- `GET /api/students/` — List students

Request example:
```

{

"isbn": "978-0123456789",

"title": "One Hundred Years of Solitude",

"publication_year": 1967,

"publisher_id": 1,

"category_id": 2

}

```

Status codes:
- 200 OK, 201 Created, 204 No Content
- 400 Bad Request, 404 Not Found, 500 Server Error

Authentication:
- JWT Bearer tokens in Authorization header.

### 5.4 REST Client
- Postman collections grouped by entity.
- Environments for local and production.
- Auth folder for login and token refresh.

### 5.5 Environment Variables
```

DATABASE_URL=postgresql://user:[pass@localhost](mailto:pass@localhost)/ulibrary

SECRET_KEY=your-secret-key

DEBUG=True

```

### 5.6 Scripts
```

python [manage.py](http://manage.py) runserver

python [manage.py](http://manage.py) makemigrations

python [manage.py](http://manage.py) migrate

```

## 6. Frontend Documentation

### 6.1 Tech and Structure
Framework: Angular 20.0.0

```

src/app/

├── components/

│   ├── book/

│   │   ├── book-list/

│   │   ├── book-create/

│   │   └── book-edit/

│   ├── loan/

│   └── student/

├── services/

│   ├── book.service.ts

│   ├── loan.service.ts

│   └── student.service.ts

├── models/

│   ├── book.model.ts

│   └── loan.model.ts

└── app.routes.ts

```

API Consumption (example):
```

// book.service.ts

getBooks(): Observable<Book[]> {

return this.http.get<Book[]>('/api/books/');

}

```

### 6.2 Frontend Operation (ASCII)
```

[Component] -> [Service: HttpClient] -> /api/... -> [Response]

| render table/forms with PrimeNG |
| --- |
| Tailwind for styling |

```

## 7. Frontend–Backend Integration
- Auth: Login → JWT token → Authorization header → automatic refresh.
- Errors: HTTP interceptors + toast messages + loading states.

End‑to‑End flow (Create Loan):
```

Frontend (Form) -> LoanService -> POST /api/loans/

-> Backend (LoanViewSet) validates -> creates record

<- Response -> UI shows success/error

```

## 8. Business Rules
- Max 5 active loans per student.
- Cannot loan a copy already loaned.
- Reservations expire after 3 days.
- Late fees: $1 per day.

## 9. Repository Structure (Proposed)
```

U-Library/

├── docs/

│   ├── User_[Manual.md](http://Manual.md)

│   ├── System_[Manual.md](http://Manual.md)

│   └── images/   # optional, kept empty since docs use ASCII diagrams

├── frontend/

├── backend/

├── [README.md](http://README.md)

└── LICENSE

```

## 10. License
MIT License

## 11. Pending Inputs
- Instructor’s name
- GitHub repository URL
- Deadline and any professor‑specific requirements
```

Archivo: docs/User_[Manual.md](http://Manual.md)

```markdown
# U‑Library — User Manual

## 1. Introduction
U‑Library is a web system for university library management. It supports books, authors, students, loans, reservations, and reports. This guide explains how to use the application as an end user.

## 2. Getting Started
### 2.1 Access and Login
1. Open your browser and navigate to the system URL.
2. Enter your email and password.
3. Click “Login”.

### 2.2 Layout Overview
- Sidebar: navigation between modules (Dashboard, Books, Students, Loans, Reservations, Reports).
- Top bar: user menu and notifications.
- Content area: lists, forms, and details.

### 2.3 Roles and Permissions
- Librarian: full access to cataloging, loans, and reservations.
- Assistant: limited access to daily operations.
- Student: self‑service reservations and viewing personal loans (if enabled).

## 3. Books
### 3.1 List and Search
- Go to Books.
- Search by title or author.
- Filter by category, status, publication year.
- Sort by any visible column.
- Use pagination controls at the bottom.

### 3.2 Create a Book
1. Click “New Book”.
2. Fill ISBN, Title, Publication Year, Publisher, Category, Authors.
3. Click “Save”.
4. A success toast confirms creation.

Validation:
- ISBN must be unique.
- Title is required.

### 3.3 Edit a Book
1. Open the row menu and click “Edit”.
2. Update fields and “Save”.

### 3.4 Delete a Book
1. Open the row menu and click “Delete”.
2. Confirm in the dialog to remove the record.

## 4. Students
### 4.1 List, Search, and Filters
- Go to Students.
- Search by name, student code, or email.
- Filter as needed.

### 4.2 Create a Student
1. Click “New Student”.
2. Fill student code, first name, last name, email, phone, career.
3. Click “Save”.

Validation:
- Student code and email must be unique.

## 5. Loans
### 5.1 Create a Loan
1. Go to Loans and click “New Loan”.
2. Select student and book copy.
3. Set due date and “Create Loan”.

Rules enforced:
- Max 5 active loans per student.
- A copy already loaned cannot be loaned again.
- Due date must be after loan date.

### 5.2 Active Loans
- View active loans.
- Filter by student, status, or date.

### 5.3 Return a Book
1. From the loan row, select “Return”.
2. Confirm. Status becomes “returned”.

## 6. Reservations
### 6.1 List Reservations
- View pending, confirmed, or expired reservations.

### 6.2 Create a Reservation
1. Click “New Reservation”.
2. Select student and book.
3. Confirm reservation.

Rules:
- Reservations expire after 3 days if not fulfilled.

## 7. Notifications and Errors
- Success: green toast with confirmation.
- Validation/server error: red toast with details.
- Examples: duplicate ISBN, invalid email, copy already loaned.

## 8. Tips
- Combine search + filters for precise results.
- Use column sorting to quickly find recent or relevant items.
- Keep unique fields accurate to avoid duplicates.

## 9. Appendix — ASCII Diagrams (No Images)

### 9.1 System Overview (User Perspective)
```

[User] -> [UI Navigation]

|  | __ Books (list/search/filter/sort/paginate) |
| --- | --- |
|  | __ Students (list/create) |
|  | __ Loans (create/return) |
|  | __ Reservations (create/list) |
|  |  |

-> Toast feedback (success/error)

```

### 9.2 Loan Creation Flow (End‑to‑End)
```

Form -> Validate fields -> Submit

-> API POST /api/loans/

-> Server validates business rules

-> Creates record, updates statuses

<- Response 201 or error

UI shows success/error toast