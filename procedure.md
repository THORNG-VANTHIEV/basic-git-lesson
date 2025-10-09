# Procedure in Database (ជាភាសាខ្មែរ + English Keywords)

## 1. What is a Procedure? (Procedure គឺជាអ្វី?)
**Procedure** ឬ **Stored Procedure** គឺជា **set of SQL statements** ដែលរក្សាទុក (store) នៅក្នុង database ហើយអាច **execute (call)** ពេលណាក៏បាន។  

វាស្រដៀងទៅនឹង **function** នៅក្នុង programming languages តែប្រើសម្រាប់ database។  

---

## 2. Key Points (ចំណុចសំខាន់)  
- **Procedure** ត្រូវបាន **stored** នៅក្នុង database។  
- អ្នកអាច **call** វា ដោយប្រើឈ្មោះ និងផ្តល់ **parameters**។  
- អាចមាន **SQL statements** (INSERT, UPDATE, DELETE, SELECT) និង **control logic** (IF, LOOP)។  
- ខុសពី **Trigger** ដែល run ដោយស្វ័យប្រវត្តិ, **Procedure** ត្រូវ **execute manually** (ដោយអ្នកប្រើ ឬ application)។  

---

## 3. Usage of Procedures (ការប្រើប្រាស់ Procedure)  
- ✅ **Reusability** – សរសេរ SQL ម្តង ប៉ុន្តែអាចប្រើបានច្រើនដង។  
- ✅ **Encapsulation** – រួមបញ្ចូល SQL statements ច្រើនជាមួយគ្នា។  
- ✅ **Security** – អាចបិទការចូលទៅ table ដោយផ្ទាល់ ហើយអោយ user call procedure ជំនួស។  
- ✅ **Performance** – DBMS នឹង precompile និង optimize procedure ម្តងហើយប្រើឡើងវិញ។  
- ✅ **Maintainability** – កែប្រែ business logic មួយកន្លែង គ្រប់ program អាចប្រើបាន។  

---

## 4. Example in MySQL  

```sql
DELIMITER $$

CREATE PROCEDURE GetEmployeeByID(IN emp_id INT)
BEGIN
    SELECT * FROM employees
    WHERE employee_id = emp_id;
END $$

DELIMITER ;
```

👉 **Call Procedure**:
```sql
CALL GetEmployeeByID(101);
```

នេះនឹង return employee ដែលមាន `employee_id = 101`។  

---

## 5. Difference between Procedure and Trigger (ភាពខុសគ្នា)  

| Feature        | **Procedure** | **Trigger** |
|----------------|--------------|-------------|
| Execution      | Must be **called manually** (CALL …) | Runs **automatically** when event (INSERT/UPDATE/DELETE) occurs |
| Usage          | Business logic, reports, batch jobs | Enforce rules, validation, auditing |
| Control        | Full control by developer | Controlled by database events |
