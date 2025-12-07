# Task Management Dashboard

A simple Task Management Dashboard built with **ASP.NET Core MVC** and **Entity Framework Core**.  
It allows **admins** to manage users and tasks, and **users** to view and update tasks assigned to them.


---

## 📚 Features

- **Authentication & Authorization**
  - Login and logout using ASP.NET Core Identity.
  - Role-based access: **Admin** and **User**.

- **Task Management**
  - Create, read, update, delete (CRUD) tasks.
  - Fields like: Title, Description, Status, Priority, Due Date, Assigned User, Created Date.
  - Filter & search tasks by status, priority, assignee, and date.

- **User Management (Admin)**
  - View list of users.
  - Assign roles (Admin/User).
  - Assign tasks to users.

- **Dashboard View**
  - Summary cards (e.g. total tasks, open tasks, completed tasks).
  - Task list table with sorting and filtering.

- **Database**
  - Built using **Entity Framework Core** with **Code-First Migrations**.
  - SQL Server as the database provider.

---

## 🛠 Tech Stack

- **Backend**
  - ASP.NET Core MVC (.NET 7)
  - Entity Framework Core
  - ASP.NET Core Identity

- **Frontend**
  - Razor Views
  - Bootstrap / CSS (update based on your UI)

- **Database**
  - Microsoft SQL Server
  - EF Core Migrations

---

## 🏗 Architecture

This project follows the **MVC (Model–View–Controller)** pattern:

- **Models**
  - `ApplicationUser` (extends IdentityUser)
  - `TaskItem` (or `TaskModel` – update to your class name)
  - Any ViewModels used for combining data for the UI.

- **Views**
  - Razor Views for:
    - Task listing, create/edit, detail
    - Dashboard
    - Authentication (Login/Register if enabled)
    - Admin pages (Users, Roles, etc.)

- **Controllers**
  - `TaskController` – handles all task-related operations.
  - `AccountController` – handles login / logout / register.
  - `AdminController` (if present) – handles user & role management.
  - `HomeController` – dashboard / landing page.

- **Data Access**
  - `ApplicationDbContext` inherits from `IdentityDbContext<ApplicationUser>`.
  - Uses EF Core DbSets like:
    - `DbSet<TaskItem> Tasks`
    - Plus Identity tables for users/roles.

---

## 🗄 Database Schema (High Level)

**Tables (simplified):**

- `AspNetUsers` – stores user details (from Identity)
- `AspNetRoles` – stores roles (`Admin`, `User`)
- `AspNetUserRoles` – mapping between users & roles
- `Tasks` (or your table name) – main task table:
  - `Id` (PK)
  - `Title`
  - `Description`
  - `Status` (e.g. ToDo, InProgress, Completed)
  - `Priority` (e.g. Low, Medium, High)
  - `DueDate`
  - `AssignedUserId` (FK to `AspNetUsers`)
  - `CreatedAt`, `UpdatedAt`


