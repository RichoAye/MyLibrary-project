# Rahel Mekonen ID=1501427
#  MyLibrary - Desktop Application with Database Integration

##  Project Overview

**MyLibrary** is a Windows Forms (WinForms) application developed in **C#** that allows a small library to manage its **book inventory** and **member borrowing records**. This project demonstrates event-driven programming, GUI design using WinForms, and database operations using **ADO.NET**.



##  Login Functionality

- Simple login screen with **Username** and **Password** input.
- Credentials are verified against a `Users` table in the database.
- On **successful login**, the main application window loads.
- On **failure**, a red error message is shown without crashing the app.

---

##  Main Features

###  Books Management

- View books in a `DataGridView` with columns:
  - `BookID`, `Title`, `Author`, `Year`, `AvailableCopies`
- Features:
  -  **Add Book**: Opens a form to input new book data.
  -  **Edit Book**: Opens with selected row data for editing.
  -  **Delete Book**: Confirms before deleting the record.
- Validations:
  - No empty fields.
  - Year must be numeric and within a reasonable range.
  - AvailableCopies must be a non-negative integer.

---

###  Borrowers Management

- Displays borrowers in a `DataGridView` with:
  - `BorrowerID`, `Name`, `Email`, `Phone`
- Features:
  -  Add Borrower
  -  Edit Borrower
  -  Delete Borrower
  -  **Issue Book**:
    - Select borrower and book
    - Insert into `IssuedBooks` table with `IssueDate`, `DueDate`
    - Decrease `AvailableCopies`
  -  **Return Book**:
    - Select an issued record
    - Remove/flag record as returned
    - Increase `AvailableCopies`

---

### Reports and Filtering (Bonus)

- Filter books by **author name** or **year range**
- Generate **Overdue Report**:
  - Shows books where `DueDate < Today`

---

## Technologies Used

| Component     | Technology                     |
|---------------|--------------------------------|
| UI Framework  | Windows Forms (.NET)           |
| Language      | C#                             |
| Database      | SQL Server / MySQL / SQLite    |
| Data Access   | ADO.NET                         |
| Design Pattern| Event-Driven Programming        |

---

##  Database Schema (Sample)

### Users
| Username | Password |

|--------|----------|----------|

### Books
| BookID | Title | Author | Year | AvailableCopies |
|--------|-------|--------|------|------------------|

### Borrowers
| BorrowerID | Name | Phone |

|------------|------|-------|-------|

### IssuedBooks
| IssueID | BookID | BorrowerID | IssueDate | DueDate |


##  How to Run the Application

### Prerequisites

- Visual Studio 2019/2022
- .NET Framework 4.7.2 or later
- SQL Server / MySQL / SQLite
- SSMS (for SQL Server) or relevant DB tool

### Steps

1. Clone this repository:
    ```bash
    git clone https://github.com/yourusername/MyLibrary.git
    ```

2. Open the solution `.sln` file in Visual Studio.

3. Update connection string in `App.config` or main code:
    ```xml
    <connectionStrings>
      <add name="MyLibraryDB"
           connectionString="Data Source=localhost;Initial Catalog=MyLibraryDB;Integrated Security=True"
           providerName="System.Data.SqlClient" />
    </connectionStrings>
    ```

4. Create the database using the provided SQL scripts (or manually):
    - Create tables: `Users`, `Books`, `Borrowers`, `IssuedBooks`
    - Insert sample data

5. Build and Run (`F5`)

6. Login with:
    - Username: `Richo`
    - Password: `1234` (or what’s stored in your `Users` table)

---

##  Best Practices Implemented

- **Parameterized Queries** to prevent SQL injection
- **try-catch blocks** around all database operations
- **Input validation** for all text and numeric fields
- **Event handlers** for all UI interactions
- **Password masking** in the login form
- **Form navigation** after login success

---



