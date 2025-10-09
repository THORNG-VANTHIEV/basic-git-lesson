# Trigger in Database (ជាភាសាខ្មែរ និង English Keywords)

## 1. What is a Trigger in Database? (Trigger គឺជាអ្វី?)
**Trigger** គឺជា stored procedure ពិសេសមួយនៅក្នុង database ដែលវា **execute ដោយស្វ័យប្រវត្តិ** នៅពេលមាន **event** មួយកើតឡើងលើ table ឬ view។  
- អ្នកមិនអាច **call** trigger ដោយផ្ទាល់បានទេ។  
- Database system នឹង **fire** វា នៅពេលមាន **INSERT, UPDATE, DELETE**។  

---

## 2. Usage of Trigger (ការប្រើប្រាស់ Trigger)
Trigger ប្រើសម្រាប់៖  
- ✅ **Data validation** – ពិនិត្យ និងទប់ស្កាត់ data មិនត្រឹមត្រូវ។  
- ✅ **Enforcing business rules** – ឧទាហរណ៍ បងារ់មិនអោយប្រាក់ខែតិចជាងកំណត់។  
- ✅ **Auditing / Logging** – កត់ត្រា ការផ្លាស់ប្តូរ (អ្នកណា កែប្រែ អ្វី នៅពេលណា)។  
- ✅ **Cascading actions** – update ឬ delete related records ដោយស្វ័យប្រវត្តិ។  
- ✅ **Prevent unauthorized operations** – ឧទាហរណ៍ Block **DELETE** សម្រាប់ Manager។  

---

## 3. Types of Trigger (ប្រភេទនៃ Trigger)  

### Based on Action:
- **INSERT Trigger** – fire ពេលមានការបញ្ចូល row ថ្មី។  
- **UPDATE Trigger** – fire ពេលមានការកែប្រែ row។  
- **DELETE Trigger** – fire ពេលមានការលុប row។  

### Based on Execution Time:
- **BEFORE Trigger** – execute មុនពេលមាន action (INSERT/UPDATE/DELETE)។  
  - ឧទាហរណ៍៖ ពិនិត្យ data មុនពេល insert។  
- **AFTER Trigger** – execute បន្ទាប់ពីមាន action។  
  - ឧទាហរណ៍៖ log data បន្ទាប់ពី update។  

### Special (អាស្រ័យលើ DBMS):
- **INSTEAD OF Trigger** – ជំនួសការប្រតិបត្តិ (ប្រើសម្រាប់ view នៅ SQL Server/Oracle)។  
- **Row-level Trigger** – fire សម្រាប់ row នីមួយៗ។  
- **Statement-level Trigger** – fire ម្តងសម្រាប់ statement មួយ (មិនមែន row)។  

---

## Example in MySQL

```sql
CREATE TRIGGER before_insert_employee
BEFORE INSERT ON employees
FOR EACH ROW
BEGIN
  -- Prevent salary less than 500
  IF NEW.salary < 500 THEN
    SIGNAL SQLSTATE '45000'
      SET MESSAGE_TEXT = 'Salary cannot be less than 500';
  END IF;
END;
```

Trigger នេះ ពិនិត្យ **salary** មុនពេល insert ទៅក្នុង `employees`។  
