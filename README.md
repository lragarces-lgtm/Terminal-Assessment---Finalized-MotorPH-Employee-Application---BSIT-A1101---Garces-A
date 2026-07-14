MotorPH Payroll System


📌 Project Overview


MotorPH Payroll System is a fully-featured Java desktop application designed to manage employee records, track attendance, and compute payroll with accurate government deductions (SSS, PhilHealth, Pag‑IBIG, and Withholding Tax). It provides a clean, professional GUI with complete CRUD (Create, Read, Update, Delete) operations, month‑based payroll filtering, and detailed reporting.

The system was developed as a Terminal Assessment submission and has been refined based on comprehensive feedback to meet the highest standards of modularity, functional suitability, maintainability, and usability.

🚀 Key Features


Feature	Description
Secure Login	Role‑based access for payroll_staff (username: payroll_staff / password: 12345).
Employee Management	Add, edit, delete, and view employee records with 14 data fields, including government numbers.
Payroll Calculation	Computes hours worked (with grace period and lunch deduction), gross pay, and all government deductions.
Month‑Based Filtering	View payroll data for any specific month (June–December 2024) or all months combined.
Deduction Breakdown	Separate table columns for SSS, PhilHealth, Pag‑IBIG, Tax, Total Deductions, and Net Pay.
Auto‑Generate Government Numbers	New employees receive random SSS, PhilHealth, TIN, and Pag‑IBIG numbers automatically.
CSV Persistence	All employee data is saved to/loaded from employees.csv; attendance data from attendance.csv.
Backup & Restore	One‑click backup of all CSV data with timestamped files.
Import / Export CSV	Easily import or export employee/payroll data.
Payroll Report	Generate a detailed report with deduction breakdown per employee and overall summary.
Professional UI	Dark theme with gradient headers, polished tables, scrollable forms, and intuitive navigation.


🛠️ Technology Stack

Language: Java (JDK 8 or higher)

GUI Framework: Swing (JFrame, JTable, JDialog, etc.)

Date/Time API: java.time (LocalDate, LocalTime, DateTimeFormatter)

File I/O: java.io, java.nio.file

CSV Parsing: Custom regex split with quoted‑field support

📂 Project Structure

<img width="671" height="194" alt="image" src="https://github.com/user-attachments/assets/f15c2fb1-c819-499b-9f67-8f8a9d1d36e2" />


🧩 CSV File Formats


employees.csv – 14 Columns (Required)
Column Index	Header	Description	Example
0	Employee #	Unique employee ID	10001
1	Last Name	Employee's last name	Garcia
2	First Name	Employee's first name	Manuel III
3	Birthday	Date of birth (MM/dd/yyyy)	10/11/1983
4	Status	Employment status	Regular, Probationary
5	Position	Job title	Chief Executive Officer
6	Immediate Supervisor	Name of supervisor	John Santos
7	Basic Salary	Monthly basic salary	90000.00
8	Gross Semi-monthly Rate	Semi‑monthly rate	45000.00
9	Hourly Rate	Hourly rate	535.71
10	SSS Number	SSS identification number	44-4506057-3
11	PhilHealth Number	PhilHealth identification number	820127000000
12	TIN	Tax Identification Number	442-605-657-000
13	Pag-IBIG Number	Pag‑IBIG identification number	691295000000


Sample Row:

10001,Garcia,Manuel III,10/11/1983,Regular,Chief Executive Officer,N/A,90000.00,45000.00,535.71,44-4506057-3,820127000000,442-605-657-000,691295000000

attendance.csv – 4 Columns
Column Index	Header	Description	Example
0	Employee #	Employee ID	10001
1	Date	Attendance date (M/d/yyyy)	6/1/2024
2	Time In	Clock‑in time (H:mm)	8:00
3	Time Out	Clock‑out time (H:mm)	17:00


Sample Row:


10001,6/1/2024,8:00,17:00
🔢 Deduction Calculation Guide
1. SSS (Social Security System)
Based on monthly salary brackets.
Returns a fixed employee share (₱135 – ₱1,125).
Table: Included in the code (computeSSS method).

2. PhilHealth
Total Premium: 3% of monthly salary.
Minimum Total: ₱300 / Maximum Total: ₱1,800.
Employee Share: 50% of total premium (₱150 – ₱900).

3. Pag-IBIG
₱1,000 – ₱1,500: 1% contribution.
Over ₱1,500: 2% contribution.
Maximum Contribution: ₱100.

4. Withholding Tax (TRAIN Law)
Taxable Income = Monthly Gross – (SSS + PhilHealth + Pag‑IBIG).
Progressive monthly brackets:
₱0 – ₱20,832: 0%
₱20,833 – ₱33,332: 20% in excess of 20,833
₱33,333 – ₱66,666: ₱2,500 + 25% in excess of 33,333
₱66,667 – ₱166,666: ₱10,833 + 30% in excess of 66,667
₱166,667 – ₱666,666: ₱40,833.33 + 32% in excess of 166,667
₱666,667 and above: ₱200,833.33 + 35% in excess of 666,667

🚀 How to Run
Option 1: Using Command Line (JDK Required)
Ensure Java is installed:

java -version   # Should show Java 8 or higher
Compile the program:

javac MotorPHGUI.java
Run the program:

java MotorPHGUI
Login with:

Username: payroll_staff
Password: 12345

Option 2: Using NetBeans IDE
Create a new Java Project (File → New Project → Java with Ant → Java Application).

Name the project (e.g., MotorPH).

UNCHECK "Create Main Class".

Right‑click Source Packages → New → Java Class → Name: MotorPHGUI.

Replace the entire content with the provided code.

Place employees.csv and attendance.csv in the project root (or let the program auto‑create sample data).

Run the project (Shift+F6).

📖 User Guide
Login Screen
Enter Username: payroll_staff
Enter Password: 12345

Main Dashboard

Element	Description

Header	Shows system title, period selector, search bar, and logout button.
Sidebar	Action buttons: Add, Edit, Delete, Refresh, Backup, Import, Export, Generate Report.
Main Table	Displays all employee records with payroll data (hours, gross pay, deductions, net pay).
Status Bar	Shows system status, record count, attendance count, and current time.

Actions
Action	How To
Add Employee	Click Add Employee → Fill in all fields → Click Save.
Edit Employee	Select an employee → Click Edit Employee (or double‑click the row) → Modify fields → Click Save.
Delete Employee	Select an employee → Click Delete Employee → Confirm deletion.
Search	Type in the search bar (filters by ID, name, position, or supervisor).
Change Period	Use the Period: dropdown to view a specific month or all months.
Generate Report	Click Generate Report → A detailed payroll report appears.
Backup Data	Click Backup Data → All CSV data is copied to the backups/ folder.
Import CSV	Click Import CSV → Select a CSV file → Replaces current employee data.
Export CSV	Click Export CSV → Exports the current table data to a CSV file.

✅ Assessment Rubric Alignment
Rubric Element	How the Application Meets It
Modularity, Design, and Syntax	Code is organized into clear methods and classes. UI creation, data loading, payroll calculation, deduction computation, CRUD operations, file I/O, and report generation are all separated.
Algorithm, Data Structures, and Reusability	Uses List<Employee> and Map<String, AttendanceRecord> for efficient data handling. Deduction methods (computeSSS, computePhilHealth, etc.) are reusable. File operations are encapsulated.
Functional Suitability	All required features work correctly: add/edit/delete employees, payroll computation with deductions, month‑based filtering, attendance regeneration, backup, import/export CSV, and payroll report generation.
Maintainability	Methods are clearly named and focused. Changing deduction rates or CSV format requires updating only specific methods. Code is well‑commented.
Usability	Intuitive GUI with clear labels, search bar, month selector, “Back to Top” button, and detailed confirmation dialogs. Validation messages are specific (e.g., “Birthday is required.”) and error handling is user‑friendly.


🔧 Troubleshooting
Issue: "Could not find or load main class"
Solution: Ensure the file is named MotorPHGUI.java and contains the public class MotorPHGUI definition. Compile from the correct directory.

Issue: "Error: Could not find or load main class motorphguidesignpayroll.MotorPHGUIDesignPayroll"
Solution: Remove any package statement at the top of the file or ensure the file is in the correct package folder.

Issue: CSV files not loading
Solution: Place employees.csv and attendance.csv in the same folder as the compiled .class files (project root). The program will auto‑create sample data if files are missing.

Issue: Scientific notation in Excel (e.g., 8.20127E+11)
Solution: Had to add "'" on every cell so it will read as a whole number
