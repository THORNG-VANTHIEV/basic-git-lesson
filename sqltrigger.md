# SQL Script Explanation (Trigger Example)

## 1. Create Database
```sql
CREATE DATABASE trigger_db;
```
- Creates a new database named **`trigger_db`**.

---

## 2. Use the Database
```sql
USE trigger_db
GO
```
- Switches the context to the `trigger_db` database.
- `GO` is a batch separator.

---

## 3. Create Staff Table
```sql
CREATE TABLE Staff (
    StaffID INT IDENTITY(1,1) PRIMARY KEY,
    StaffName NVARCHAR(100) NOT NULL,
    StaffPosition NVARCHAR(50) NOT NULL,
    Salary DECIMAL(10,2),
    HireDate DATE DEFAULT GETDATE()
);
```
- **`Staff`** table stores employees.
- `StaffID`: auto-increment primary key.
- `StaffName`, `StaffPosition`: required fields.
- `Salary`: decimal value for salary.
- `HireDate`: defaults to today’s date.

---

## 4. Insert Sample Data
```sql
INSERT INTO Staff (StaffName, StaffPosition, Salary)
VALUES 
('Vuthy Chan', 'Manager', 1500.00),
('Sokha Phan', 'Staff', 900.00),
('Dara Kim', 'Staff', 850.00);
```
- Adds 3 employees:  
  - **Vuthy Chan** (Manager, 1500)  
  - **Sokha Phan** (Staff, 900)  
  - **Dara Kim** (Staff, 850)

---

## 5. Create StaffLog Table
```sql
CREATE TABLE StaffLog (
    LogID INT IDENTITY(1,1) PRIMARY KEY,
    StaffID INT,
    StaffName NVARCHAR(100),
    ActionDate DATETIME,
    ActionType NVARCHAR(50)
);
```
- **`StaffLog`** table is for logging staff actions.
- Fields: LogID, StaffID, StaffName, ActionDate, ActionType.

---

## 6. Create Trigger
```sql
CREATE TRIGGER trg_Staff_Delete
ON Staff
INSTEAD OF DELETE
AS
BEGIN
    -- Prevent delete for Manager
    IF EXISTS (SELECT * 
               FROM deleted 
               WHERE StaffPosition = 'Manager')
    BEGIN
        PRINT 'Managers cannot be deleted!';
        RETURN;
    END

    -- Otherwise, log deleted staff
    INSERT INTO StaffLog (StaffID, StaffName, ActionDate, ActionType)
    SELECT StaffID, StaffName, GETDATE(), 'DELETE'
    FROM deleted;

    -- Perform actual delete for normal staff
    DELETE FROM Staff
    WHERE StaffID IN (SELECT StaffID FROM deleted);
END;
GO
```

### Explanation
1. **Prevent deletion of Managers**  
   - If the deleted row is a Manager → block deletion.  

2. **Log deletions**  
   - For non-managers, inserts details into `StaffLog`.  

3. **Delete staff**  
   - Deletes staff row only if not a Manager.

---

## ✅ Summary
- Database: `trigger_db`
- Tables: `Staff`, `StaffLog`
- Rule: Managers cannot be deleted.
- All other staff deletions are logged into `StaffLog` before deletion.
