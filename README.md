# Smart Employee Management & HR System

> **A Complete, Professional Java Swing Desktop Application built with SQLite & JDBC.**
> 
> **Important Note:** This project uses **SQLite** (`employee_management.db`) and **does NOT require MySQL** or any external database server setup.

---

## 🌟 Overview & Key Features

The **Smart Employee Management & HR System** is a production-grade desktop application designed for managing company workforce, attendance, leaves, payroll, reports, employee documents, and system notifications.

### 🔑 Features Summary:
1. **First-Run Automatic Database Setup**: Automatically creates the local SQLite database (`employee_management.db`) and seeds 6 departments, 10 employees, sample attendance, leave requests, payroll records, and user accounts.
2. **Role-Based Authentication**:
   - **ADMIN**: Full system access (Employee CRUD, Departments, Attendance, Leaves, Payroll, Reports, Settings, User Management).
   - **HR**: Employee CRUD, Attendance, Leaves, Payroll, Reports, Settings.
   - **EMPLOYEE**: View personal profile, view own attendance history, apply for leave, view leave status, view own payroll & salary slip.
3. **Interactive Main Dashboard**:
   - **Dynamic Stat Cards**: Total Employees, Active Employees, On Leave, Total Departments, Monthly Payroll (calculated live from SQLite).
   - **Department Distribution Bars**: Visual employee count breakdown per department.
   - **Upcoming Birthdays & Work Anniversaries**: Calculated automatically within the next 30 days.
   - **Pending Leave Requests Widget**: Instant review link for HR/Admin.
4. **Complete Employee Management (CRUD)**:
   - Form validation (Email, Phone, Date format, Non-negative salary).
   - Search by ID, Name, Email, Phone.
   - Filter by Department, Employment Status, Designation.
   - Sort by Name, Salary, Joining Date.
   - Profile Photo support (JFileChooser) with fallback placeholder.
   - Double-click employee row to open full **Detailed Profile Dialog**.
5. **Department Management**:
   - Add/Update/Delete departments.
   - **Safe Deletion Check**: Prevents deleting a department if active employees are assigned to it.
6. **Attendance Management**:
   - Mark daily attendance (Present, Absent, Half Day, Late, On Leave).
   - Check-in / Check-out time tracking.
   - **Duplicate Attendance Check**: Prevents duplicate entries for the same employee on the same date.
   - Today's Attendance summary statistics badges.
7. **Leave Management & Approval System**:
   - Employee leave application (Casual, Sick, Earned, Emergency).
   - To-date validation (cannot be before From-date).
   - Admin/HR Approve / Reject workflow with confirmation dialogs.
8. **Payroll Management**:
   - Real-time automatic salary calculation:
     - `Gross Salary = Basic Salary + HRA + Transport Allowance + Other Allowance`
     - `Total Deduction = PF + Professional Tax + Other Deduction`
     - `Net Salary = Gross Salary - Total Deduction`
   - Validation against negative values.
9. **Printable Salary Slip Generator**:
   - Itemized earnings & deductions payslip renderer.
   - **Print** directly via standard Swing graphics / printer API.
   - **Export** salary slip to HTML format.
10. **System Reports Module**:
    - Generates Employee, Attendance, Leave, Payroll, and Department Reports.
    - Date range filtering (From Date, To Date).
    - **CSV Export**: Integrated `CSVExporter.java` using `JFileChooser`.
11. **System Notifications Vault**:
    - Live alerts for pending leaves, upcoming birthdays, work anniversaries, and payroll due dates.
12. **Employee Document Vault**:
    - Store Aadhaar, PAN, Resume, Joining Letter, Experience Certificates.
    - Open files natively via Java `Desktop.getDesktop().open()`.
    - Handles missing files gracefully.
13. **Modern UI & Theme System (Light / Dark Mode)**:
    - Custom modern color tokens, rounded cards, high-contrast sidebar, styled JTables.
    - Toggle live between **Light Mode** and **Dark Mode** via header button or Settings.

---

## 🛠️ Technology Stack & Requirements

- **Programming Language**: Java (JDK 8 or higher, tested on JDK 26)
- **GUI Framework**: Java Swing (JFrame, JPanel, CardLayout, JSplitPane, JTable)
- **Database Engine**: SQLite 3 (Embedded File Database: `employee_management.db`)
- **Database Connectivity**: JDBC (`org.sqlite.JDBC`)
- **Security**: PreparedStatement (SQL Injection prevention) & SHA-256 password hashing.

---

## 📁 Project Structure

```
JAVA_PROJECT/
 ├── bin/                         # Compiled class files
 ├── database/
 │    └── employee_management.sql # Optional backup SQL script
 ├── lib/
 │    ├── sqlite-jdbc-3.45.1.0.jar
 │    ├── slf4j-api-1.7.36.jar
 │    └── slf4j-simple-1.7.36.jar
 ├── src/
 │    ├── main/
 │    │    └── Main.java
 │    ├── model/
 │    │    ├── User.java
 │    │    ├── Employee.java
 │    │    ├── Department.java
 │    │    ├── Attendance.java
 │    │    ├── Leave.java
 │    │    ├── Payroll.java
 │    │    └── DocumentModel.java
 │    ├── dao/
 │    │    ├── UserDAO.java
 │    │    ├── EmployeeDAO.java
 │    │    ├── DepartmentDAO.java
 │    │    ├── AttendanceDAO.java
 │    │    ├── LeaveDAO.java
 │    │    ├── PayrollDAO.java
 │    │    └── DocumentDAO.java
 │    ├── ui/
 │    │    ├── LoginFrame.java
 │    │    ├── DashboardFrame.java
 │    │    ├── DashboardHomePanel.java
 │    │    ├── EmployeePanel.java
 │    │    ├── EmployeeDetailsDialog.java
 │    │    ├── DepartmentPanel.java
 │    │    ├── AttendancePanel.java
 │    │    ├── LeavePanel.java
 │    │    ├── PayrollPanel.java
 │    │    ├── SalarySlipPanel.java
 │    │    ├── ReportsPanel.java
 │    │    ├── NotificationPanel.java
 │    │    ├── DocumentPanel.java
 │    │    └── SettingsPanel.java
 │    └── util/
 │         ├── DatabaseConnection.java
 │         ├── DatabaseInitializer.java
 │         ├── PasswordUtil.java
 │         ├── ValidationUtil.java
 │         ├── CSVExporter.java
 │         └── ThemeUtil.java
 ├── employee_management.db       # Auto-created SQLite database file
 ├── build.bat                    # One-click build batch script
 ├── run.bat                      # One-click run batch script
 └── README.md
```

---

## 🚀 Default Credentials

The system comes pre-seeded with sample user accounts for testing:

| Role | Username | Password | Access Level |
| :--- | :--- | :--- | :--- |
| **ADMIN** | `admin` | `admin123` | Full access (Users, Employees, Depts, Attendance, Leaves, Payroll, Reports, Settings) |
| **HR** | `hr` | `hr123` | Employee CRUD, Attendance, Leaves, Payroll, Reports, Settings |
| **EMPLOYEE** | `employee` | `employee123` | Personal profile, personal attendance, apply/view leaves, salary slip |

---

## 💻 How to Build & Run

### Method 1: Using Batch Scripts (Windows)
1. Double-click `build.bat` to compile all source code.
2. Double-click `run.bat` to launch the application.

### Method 2: From Terminal / Command Prompt
**Compilation:**
```bash
javac -cp "lib/*" -d bin src/util/*.java src/model/*.java src/dao/*.java src/ui/*.java src/main/*.java
```

**Execution:**
```bash
java -cp "bin;lib/*" main.Main
```

### Method 3: In an IDE (Eclipse / IntelliJ IDEA / NetBeans / VS Code)
1. Open the `JAVA_PROJECT` folder in your IDE.
2. Add all JAR files inside `lib/` to your project's Build Path / Classpath.
3. Run `src/main/Main.java`.

---

## 🗄️ Database Architecture

The SQLite database uses foreign keys (`PRAGMA foreign_keys = ON;`) to enforce relational integrity:

- `departments (department_id PK)` ➔ `employees (department_id FK)`
- `employees (employee_id PK)` ➔ `attendance (employee_id FK)`
- `employees (employee_id PK)` ➔ `leaves (employee_id FK)`
- `employees (employee_id PK)` ➔ `payroll (employee_id FK)`
- `employees (employee_id PK)` ➔ `documents (employee_id FK)`
- `employees (employee_id PK)` ➔ `users (employee_id FK)`

---

## 🎓 Viva & College Project Presentation Points

- **Object-Oriented Programming (OOP)**:
  - **Encapsulation**: Model classes (`Employee`, `Department`, `Payroll`) encapsulate private fields with getters/setters.
  - **Abstraction & DAO Pattern**: GUI panels communicate only with Data Access Objects (`EmployeeDAO`, `LeaveDAO`), keeping database logic completely separated from presentation logic.
  - **Polymorphism**: Used in event listeners (`ActionListener`, `MouseAdapter`) and custom Swing component cell renderers.
- **SQLite vs MySQL**:
  - SQLite is lightweight, file-based (`employee_management.db`), serverless, and requires zero installation or database passwords.
- **Security**:
  - `PreparedStatement` is used for every query to eliminate SQL Injection vulnerabilities.
  - Passwords are stored securely as SHA-256 hashes.
- **Exception Handling**:
  - Try-with-resources blocks auto-close SQL connections, statements, and result sets to prevent resource leaks.
  - Clear user alerts (`JOptionPane`) replace raw error tracebacks.
"# Employee_Management_system" 
