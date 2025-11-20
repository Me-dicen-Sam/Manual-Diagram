---
title: "U-Library User Manual"
author: "Samuel Baquero"
date: "2025-11-20"
output:
  md_document:
    variant: preserve_yaml
    markdown: true
---
# U-Library — User Manual

## 1. Introduction
U-Library is a web system for university library management. It allows the administration of books, authors, students, loans, reservations, and reports. This guide explains how to use the application from the end-user perspective.

## 2. Getting Started
### 2.1 Access and Login
- Open your browser and navigate to the U-Library URL provided by your institution.
- Enter your email and password.
- Click “Login”.

![Login](images/login.png)

### 2.2 Layout Overview
- Sidebar: navigation between modules (Dashboard, Books, Students, Loans, Reservations, Reports).
- Top bar: user menu and notifications.
- Content area: lists, forms, and details.

![Dashboard](images/dashboard.png)
![Layout with sidebar](images/layout.png)

## 3. Books
### 3.1 List and Search
- Go to Books.
- Use search by title or author.
- Apply filters by category, status, and publication year.
- Sort by columns.

![Book list](images/book-list.png)

### 3.2 Create a Book
- Click “New Book”.
- Fill: ISBN, Title, Publication year, Publisher, Category, Authors.
- Click “Save”.
- You will see a success confirmation.

![Create book](images/book-create.png)

### 3.3 Edit a Book
- Open the book’s row menu, click “Edit”.
- Update fields and click “Save”.
- You will see a success confirmation.

![Edit book](images/book-edit.png)

### 3.4 Delete a Book
- Open the book’s row menu, click “Delete”.
- Confirm in the dialog.
- You will see a success confirmation.

![Delete book confirmation](images/book-delete-confirm.png)

## 4. Students
### 4.1 List and Search
- Go to Students.
- Search by name, code, or email.
- Apply filters as needed.

![Student list](images/student-list.png)

### 4.2 Create a Student
- Click “New Student”.
- Fill: student code, first name, last name, email, phone, career.
- Click “Save”.

![Create student](images/student-create.png)

## 5. Loans
### 5.1 Create a Loan
- Go to Loans.
- Click “New Loan”.
- Select student and book copy.
- Set due date.
- Click “Create Loan”.

![Create loan](images/loan-create.png)

### 5.2 Active Loans
- View active loans in the list.
- Filter by student, status, or date.

![Active loans](images/loan-active-list.png)

### 5.3 Return a Book
- Open the loan’s row menu, select “Return”.
- Confirm return; the status becomes “returned”.

![Return process](images/loan-return.png)

## 6. Reservations
### 6.1 List Reservations
- Go to Reservations.
- View pending, confirmed, or expired reservations.

![Reservation list](images/reservation-list.png)

### 6.2 Create a Reservation
- Click “New Reservation”.
- Select student and book.
- Confirm reservation.

![Create reservation](images/reservation-create.png)

## 7. Notifications and Errors
- Successful actions display a green toast message.
- Validation errors or server errors display a red toast message.
- If a book copy is already loaned, the system will prevent new loans.

## 8. Tips
- Use pagination controls at the bottom of lists.
- Combine search with filters for faster results.
- Keep student email unique to avoid duplicates.

## 9. Appendix — Screenshot Guidelines
- Size: 1280x720 px
- Format: PNG or JPG
- Use realistic sample data
- Include confirmation or error messages when relevant