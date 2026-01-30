Before APIs (Application Programming Interfaces) became widespread, systems used several different methods to share data and functionality:

## 1. **Direct Database Access**
Applications would connect directly to each other's databases. This was messy because:
- Apps needed to know the exact database structure
- Changes to one database could break other apps
- Security was harder to manage

**Example:** An e-commerce site might directly query the inventory database of a warehouse system to check stock levels, using SQL queries like:
```sql
SELECT quantity FROM warehouse_db.inventory WHERE product_id = 12345;
```

## 2. **File Transfers**
Systems would exchange data by writing and reading files, often on scheduled intervals.

**Example:** A payroll system might generate a CSV file every night:
```csv
employee_id,hours_worked,date
101,8.5,2024-01-29
102,7.0,2024-01-29
```
Then the accounting system would read this file the next morning to process payments.

## 3. **Screen Scraping**
Programs would parse the HTML or text output meant for human users to extract data.

**Example:** A price comparison site might load a retailer's webpage and parse the HTML to find prices:
```html
<span class="price">$29.99</span>
```

## 4. **Remote Procedure Calls (RPC)**
Earlier protocols like CORBA, RMI, or COM/DCOM allowed programs to call functions on remote systems, but they were complex and platform-specific.

**Example:** A Java application calling a method on a remote server using RMI to get customer data.

APIs standardized and simplified all of this by creating clean, documented interfaces for systems to communicate reliably and securely.
