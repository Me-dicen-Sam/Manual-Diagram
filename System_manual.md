---
title: "U-Library System Manual"
author: "Samuel Baquero"
date: "2025-11-20"
output:
  md_document:
    variant: preserve_yaml
    markdown: true
---

# SYSTEM DOCUMENTATION - U-LIBRARY

## 1. Project Information

**Project Name:** U-Library - University Library Management System  
**Student Name:** Samuel Baquero  
**Course:** Software Engineering  
**Semester:** Sixth Semester  
**Date:** November 2024  
**Instructor:** Jaider Quintero

**Short Project Description:**  
U-Library is a comprehensive web-based library management system designed for universities. It facilitates efficient management of books, authors, students, loans, reservations, and provides real-time reporting capabilities.

## 2. System Architecture Overview

### 2.1 Architecture Description

U-Library follows a **three-tier client-server architecture** with clear separation of concerns:

- **Presentation Layer:** Angular 20 frontend with PrimeNG components
- **Application Layer:** Django REST Framework backend API
- **Data Layer:** Multi-database support (PostgreSQL, MySQL, SQL Server)

### 2.2 Technologies Used

**Frontend:**
- Angular 20.0.0
- PrimeNG 20.3.0 UI Components
- Tailwind CSS 4.1.17
- TypeScript 5.8.2
- RxJS 7.8.0

**Backend:**
- Django 5.2.7
- Django REST Framework 3.15.2
- Python 3.11
- Django CORS Headers 4.6.0

**Database Engine:**
- PostgreSQL 15 (Primary)
- MySQL 8.0 (Secondary)
- SQL Server 2019 (Optional)
- SQLite (Development)

**Additional Libraries / Tools:**
- Docker & Docker Compose
- Git for version control
- Postman for API testing
- JWT for authentication

### 2.3 Visual explanation of the system's operation

```
┌─────────────────────────────────────────────────────────────┐
│                    CLIENT BROWSER                          │
│  ┌───────────────────────────────────────────────────────┐  │
│  │               Angular Frontend (4200)                │  │
│  │  ┌─────────────┐  ┌──────────────┐  ┌─────────────┐   │  │
│  │  │ Components  │  │   Services   │  │   Models    │   │  │
│  │  │ • BookList  │  │ • BookService│  │ • Book      │   │  │
│  │  │ • LoanForm  │  │ • LoanService│  │ • Student   │   │  │
│  │  │ • Student   │  │ • Student    │  │ • Loan      │   │  │
│  │  └─────────────┘  └──────┬───────┘  └─────────────┘   │  │
│  │         ▲                 │                           │  │
│  │         │                 ▼                           │  │
│  │    ┌────┴─────────────────────────────┐               │  │
│  │    │  PrimeNG + Tailwind CSS UI       │               │  │
│  │    │ • DataTables • Forms • Charts    │               │  │
│  │    └──────────────────────────────────┘               │  │
│  └───────────────────────┬───────────────────────────────┘  │
└──────────────────────────┼──────────────────────────────────┘
                           │
                    HTTP REST API (JSON)
                           │
┌──────────────────────────▼──────────────────────────────────┐
│               Django Backend (8000)                        │
│  ┌───────────────────────────────────────────────────────┐  │
│  │                   REST API Layer                      │  │
│  │  ┌──────────────┐  ┌──────────────┐  ┌────────────┐   │  │
│  │  │   ViewSets   │  │ Serializers  │  │   URLs     │   │  │
│  │  │ • BookViewSet│  │ • Book       │  │ /api/books/│   │  │
│  │  │ • LoanViewSet│  │ • Loan       │  │ /api/loans/│   │  │
│  │  │ • Student    │  │ • Student    │  │ /students/ │   │  │
│  │  └──────┬───────┘  └──────────────┘  └────────────┘   │  │
│  └─────────┼─────────────────────────────────────────────┘  │
│            │                                                │
│  ┌─────────▼─────────────────────────────────────────────┐  │
│  │                 Business Logic Layer                  │  │
│  │  ┌──────────┐  ┌──────────┐  ┌──────────────────────┐ │  │
│  │  │  Models  │  │  Admin   │  │   Middleware         │ │  │
│  │  │ • Book   │  │ • Book   │  │ • CORS               │ │  │
│  │  │ • Author │  │ • Loan   │  │ • Authentication     │ │  │
│  │  │ • Loan   │  │ • Student│  │ • Validation         │ │  │
│  │  └────┬─────┘  └──────────┘  └──────────────────────┘ │  │
│  └───────┼───────────────────────────────────────────────┘  │
│          │                                                  │
│  ┌───────▼───────────────────────────────────────────────┐  │
│  │              Django ORM (Database Abstraction)        │  │
│  └───────┬───────────────────────────────────────────────┘  │
└──────────┼──────────────────────────────────────────────────┘
           │
┌──────────▼───────────────────────────────────────────────────┐
│                    DATABASE LAYER                            │
│  ┌────────────┐  ┌───────────┐  ┌────────────┐  ┌──────────┐ │
│  │ PostgreSQL │  │   MySQL   │  │ SQL Server │  │  SQLite  │ │
│  │   15       │  │   8.0     │  │   2019     │  │ (Dev)    │ │
│  └────────────┘  └───────────┘  └────────────┘  └──────────┘ │
└──────────────────────────────────────────────────────────────┘

DATA FLOW:
1. User interaction → Angular Component
2. Component calls Service method
3. Service makes HTTP request to Django API
4. Django ViewSet processes request
5. Serializer validates/transforms data
6. Model interacts with database via ORM
7. Response flows back through layers
8. Angular updates UI with received data
```

## 3. Database Documentation

### 3.1 Database Description

The U-Library system uses a **normalized relational database** designed for academic library operations. The database supports multiple engines through Django ORM abstraction while maintaining data integrity through foreign key constraints and business logic validation.

**Key Design Principles:**
- Third Normal Form (3NF) compliance
- Referential integrity with cascade operations
- Unique constraints on business keys
- Indexed fields for performance optimization

### 3.2 ERD – Entity Relationship Diagram

```
[IMAGE: erd-diagram.png]
Description: Entity Relationship Diagram showing all tables and their relationships
Manual Usuario: Mostrará captura completa del diagrama ERD generado
```

```
ENTITY RELATIONSHIP DIAGRAM (ASCII Representation):

BOOKS ─────┐             STUDENTS ─────┐
  id PK    │               id PK       │
  isbn     │               student_code│
  title    │               first_name  │
  year     │               last_name   │
  publisher│               email       │
           │               career      │
           │                           │
           └──────────┐                │
AUTHORS ──────────────┤                │
  id PK               │                │
  first_name          │                │
  last_name           │                │
  nationality         │                │
                      │                │
BOOK_AUTHORS ─────────┘                │
  book_id PK,FK ───────────────────────┘
  author_id PK,FK                       │
                                        │
BOOK_COPIES ────────────────────────────┤LOANS
  id PK                                 │  id PK
  book_id FK ───────────────────────────┘  student_id FK
  copy_code                               │  book_copy_id FK
  status                                  │  loan_date
  location                                │  due_date
                                          │  return_date
CATEGORIES ─────┐                         │  status
  id PK         │                         │
  name          │                         │
  description   │                         │
                │                         │
BOOK_CATEGORIES ┘                    RESERVATIONS
  book_id PK,FK ──────────────────────┐  id PK
  category_id PK,FK                   │  student_id FK
                                      │  book_id FK
PUBLISHERS ─────┐                     │  reservation_date
  id PK         │                     │  expiry_date
  name          │                     │  status
  address       │                     │
  contact       │                     └───────────┘
                │
BOOK.publisher_id FK ──────────────────┘
```

### 3.3 Logical Model

**Core Entities Definition:**

1. **Book**
   - Represents bibliographic information
   - Attributes: ISBN (unique), title, publication year, publisher reference
   - Business Rules: ISBN validation, title uniqueness per publisher

2. **Author**
   - Represents book authors
   - Attributes: Name, nationality, birth date
   - Business Rules: Unique name+birthdate combination

3. **Student**
   - Represents library users
   - Attributes: Student code (unique), personal information, academic program
   - Business Rules: Email uniqueness, active status validation

4. **BookCopy**
   - Represents physical book instances
   - Attributes: Copy code, status, location
   - Business Rules: Status transitions, availability checks

5. **Loan**
   - Represents book lending transactions
   - Attributes: Dates, status, relationships
   - Business Rules: Loan limits, overdue calculations

### 3.4 Physical Model (Tables)

#### Books Table
| Table | Column | Type | PK/FK | Description |
|-------|--------|------|-------|-------------|
| books | id | BigAutoField | PK | Primary key |
| books | isbn | CharField(13) | UK | Unique ISBN identifier |
| books | title | CharField(200) | - | Book title |
| books | publication_year | IntegerField | - | Publication year |
| books | publisher_id | BigInteger | FK | Publisher reference |

#### Authors Table
| Table | Column | Type | PK/FK | Description |
|-------|--------|------|-------|-------------|
| authors | id | BigAutoField | PK | Primary key |
| authors | first_name | CharField(100) | - | Author first name |
| authors | last_name | CharField(100) | - | Author last name |
| authors | nationality | CharField(50) | - | Author nationality |

#### Students Table
| Table | Column | Type | PK/FK | Description |
|-------|--------|------|-------|-------------|
| students | id | BigAutoField | PK | Primary key |
| students | student_code | CharField(20) | UK | Unique student identifier |
| students | email | EmailField | UK | Student email address |
| students | career | CharField(50) | - | Academic program |

## 4. Use Cases – CRUD

### 4.1 Use Case: Create Book

**Actor:** Librarian  
**Description:** Add a new book to the library catalog  
**Preconditions:** User authenticated with librarian privileges, publisher exists  
**Postconditions:** Book record created, available for inventory management  
**Main Flow:**
1. Navigate to Books → New Book
2. Enter ISBN (validated for format)
3. Enter title and publication year
4. Select publisher from dropdown
5. Assign authors and categories
6. Submit form
7. System validates data and creates record
8. Success confirmation displayed

### 4.2 Use Case: Read Books

**Actor:** Student/Librarian  
**Description:** Browse and search library catalog  
**Preconditions:** System operational, catalog populated  
**Postconditions:** Book information displayed, no data modification  
**Main Flow:**
1. Access books listing page
2. View paginated results with book details
3. Use search functionality by title/author/ISBN
4. Apply filters by category/availability
5. Sort results by various criteria
6. View individual book details with copy availability

### 4.3 Use Case: Update Book Information

**Actor:** Librarian  
**Description:** Modify existing book records  
**Preconditions:** Book exists in system, user has edit permissions  
**Postconditions:** Book information updated, changes persisted  
**Main Flow:**
1. Locate book in listing
2. Access edit interface
3. Modify desired fields (title, authors, categories)
4. Validate changes
5. Save updates
6. System applies changes and confirms

### 4.4 Use Case: Delete Book

**Actor:** Librarian  
**Description:** Remove book from catalog  
**Preconditions:** Book exists, no active loans for any copies  
**Postconditions:** Book removed from active catalog, historical data preserved  
**Main Flow:**
1. Access book management interface
2. Select delete action for target book
3. System checks for active loans
4. Confirm deletion in dialog
5. Execute soft/hard delete based on configuration
6. Update inventory counts

## 5. Backend Documentation

### 5.1 Backend Architecture

The backend follows **Django MTV (Model-Template-View)** pattern adapted for API:

- **Models:** Data layer with Django ORM
- **ViewSets:** Request handling and business logic
- **Serializers:** Data transformation and validation
- **URLs:** RESTful endpoint routing

**Key Design Patterns:**
- Repository pattern (Django ORM)
- Serializer pattern for data transformation
- ViewSet pattern for CRUD operations
- Router pattern for automatic URL mapping

### 5.2 Folder Structure

```
backend/
├── config/                          # Project configuration
│   ├── settings.py                  # Global settings
│   ├── urls.py                      # Main URL routing
│   └── wsgi.py                      # WSGI entry point
├── apps/                            # Django applications
│   ├── books/                       # Book management
│   │   ├── models.py                # Book, BookCopy models
│   │   ├── views.py                 # BookViewSet, BookCopyViewSet
│   │   ├── serializers.py           # Book serializers
│   │   └── urls.py                  # Book API routes
│   ├── students/                    # Student management
│   │   ├── models.py                # Student model
│   │   ├── views.py                 # StudentViewSet
│   │   └── serializers.py           # Student serializers
│   ├── loans/                       # Loan management
│   │   ├── models.py                # Loan model
│   │   ├── views.py                 # LoanViewSet
│   │   └── services.py              # Loan business logic
│   └── reservations/                # Reservation management
├── utils/                           # Utility functions
│   ├── validators.py                # Custom validators
│   └── helpers.py                   # Helper functions
└── manage.py                        # Django management script
```

### 5.3 API Documentation (REST)

**Method Path:** `GET /api/books/`

**Purpose:** Retrieve paginated list of books with filtering and search capabilities  
**Request Body Example:** None (query parameters only)

**Query Parameters:**
- `page` - Page number (default: 1)
- `search` - Search term for title/author/ISBN
- `category` - Filter by category ID
- `available` - Filter by availability

**Responses:**
- **200 OK**
```json
{
  "count": 150,
  "next": "http://api.ulibrary.com/books/?page=2",
  "previous": null,
  "results": [
    {
      "id": 1,
      "isbn": "9780123456789",
      "title": "Sample Book Title",
      "publication_year": 2023,
      "publisher": {"id": 1, "name": "Sample Publisher"},
      "authors": [
        {"id": 1, "first_name": "John", "last_name": "Doe"}
      ],
      "available_copies": 3
    }
  ]
}
```

- **400 Bad Request**
```json
{
  "error": "Invalid search parameters",
  "details": {"page": ["Ensure this value is greater than or equal to 1."]}
}
```

**Method Path:** `POST /api/books/`

**Purpose:** Create a new book record  
**Request Body Example:**
```json
{
  "isbn": "9780123456789",
  "title": "New Book Title",
  "publication_year": 2024,
  "publisher": 1,
  "authors": [1, 2],
  "categories": [3, 5]
}
```

**Responses:**
- **201 Created** - Book successfully created
- **400 Bad Request** - Validation errors
- **409 Conflict** - ISBN already exists

### 5.4 REST Client Examples

**Using curl:**
```bash
# Get all books
curl -X GET "http://localhost:8000/api/books/?search=django&page=1"

# Create new book
curl -X POST "http://localhost:8000/api/books/" \
  -H "Content-Type: application/json" \
  -d '{
    "isbn": "9780123456789",
    "title": "Django for Professionals",
    "publication_year": 2024,
    "publisher": 1
  }'

# Update book
curl -X PUT "http://localhost:8000/api/books/1/" \
  -H "Content-Type: application/json" \
  -d '{"title": "Updated Book Title"}'
```

## 6. Frontend Documentation

### 6.1 Technical Frontend Documentation

**Framework Used:** Angular 20.0.0 with TypeScript

**Architecture Pattern:** Component-based architecture with service layer

**Key Concepts:**
- Components for UI presentation
- Services for business logic and API communication
- Models/Interfaces for type safety
- RxJS Observables for reactive programming
- Router for navigation and lazy loading

### 6.2 Folder Structure

```
src/
├── app/
│   ├── core/                        # Core functionality
│   │   ├── auth/                    # Authentication
│   │   ├── interceptors/            # HTTP interceptors
│   │   └── guards/                  # Route guards
│   ├── shared/                      # Shared resources
│   │   ├── components/              # Reusable components
│   │   ├── models/                  # TypeScript interfaces
│   │   └── services/                # Shared services
│   ├── features/                    # Feature modules
│   │   ├── books/                   # Book management
│   │   │   ├── components/          # Book components
│   │   │   │   ├── book-list/
│   │   │   │   ├── book-create/
│   │   │   │   ├── book-edit/
│   │   │   │   └── book-detail/
│   │   │   ├── services/            # Book services
│   │   │   └── books.routes.ts      # Book routing
│   │   ├── loans/                   # Loan management
│   │   ├── students/                # Student management
│   │   └── dashboard/               # Dashboard
│   ├── layouts/                     # Layout components
│   │   ├── main-layout/             # Main layout
│   │   └── auth-layout/             # Auth layout
│   └── app.routes.ts                # Main routing
├── assets/                          # Static assets
└── environments/                    # Environment configs
```

**Models, Services and Components:**

**Book Model:**
```typescript
export interface Book {
  id: number;
  isbn: string;
  title: string;
  publication_year: number;
  publisher: Publisher;
  authors: Author[];
  categories: Category[];
  available_copies: number;
}

export interface BookCreateDto {
  isbn: string;
  title: string;
  publication_year: number;
  publisher: number;
  authors: number[];
  categories: number[];
}
```

**Book Service:**
```typescript
@Injectable({ providedIn: 'root' })
export class BookService {
  private apiUrl = `${environment.apiUrl}/books`;
  
  constructor(private http: HttpClient) {}
  
  getBooks(params?: any): Observable<Book[]> {
    return this.http.get<Book[]>(this.apiUrl, { params });
  }
  
  createBook(book: BookCreateDto): Observable<Book> {
    return this.http.post<Book>(this.apiUrl, book);
  }
  
  updateBook(id: number, book: BookCreateDto): Observable<Book> {
    return this.http.put<Book>(`${this.apiUrl}/${id}/`, book);
  }
}
```

### 6.3 Visual explanation of the system's operation

```
[IMAGE: frontend-architecture.png]
Description: Angular component hierarchy and data flow
Manual Usuario: Mostrará captura del dashboard principal con todos los módulos
```

```
ANGULAR COMPONENT HIERARCHY:

AppComponent
├── MainLayoutComponent
│   ├── HeaderComponent
│   ├── SidebarComponent
│   └── RouterOutlet
│       ├── DashboardComponent (default)
│       ├── BookListComponent (/books)
│       │   └── BookDetailComponent
│       ├── BookCreateComponent (/books/create)
│       ├── BookEditComponent (/books/edit/:id)
│       ├── StudentListComponent (/students)
│       ├── LoanListComponent (/loans)
│       └── ReservationListComponent (/reservations)
└── AuthLayoutComponent (/login)

DATA FLOW:
User Action → Component → Service → HTTP → API → Database
       ↑                                      ↓
       └── Component ← Observable ← Service ← Response
```

## 7. Frontend–Backend Integration

The integration follows RESTful principles with JSON data exchange:

**Authentication Flow:**
1. Login request with credentials
2. JWT token generation
3. Token inclusion in subsequent requests
4. Automatic token refresh

**Error Handling:**
- HTTP status code mapping
- User-friendly error messages
- Network error recovery

**Data Synchronization:**
- Real-time updates via RxJS observables
- Optimistic UI updates
- Conflict resolution strategies

## 8. Conclusions & Recommendations

### 8.1 Conclusions

The U-Library system successfully implements a modern, scalable architecture that meets university library requirements. The separation between frontend and backend allows for independent development and deployment. The multi-database support provides flexibility for different institutional environments.

### 8.2 Recommendations

**Short-term Improvements:**
- Implement comprehensive unit testing
- Add API rate limiting
- Enhance error logging and monitoring

**Long-term Enhancements:**
- Mobile application development
- Advanced analytics and reporting
- Integration with university identity systems
- RFID book tracking implementation

**Performance Optimizations:**
- Database query optimization
- Frontend bundle optimization
- Caching strategy implementation

---
