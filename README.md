# Hospital Information Management & Analytics System — PostgreSQL

Organization: ABC Multispeciality Hospital (fictional portfolio case study)  
Database: PostgreSQL  
Level: Beginner to advanced SQL analytics

Project overview
Designed a relational hospital database covering departments, doctors, employees, patients, appointments, admissions, rooms, diagnoses, prescriptions,
medicines, laboratory tests, payments, insurance, and analytics reporting tables. The project uses illustrative sample data and is intended for SQL practice;
it is not a real hospital dataset.

How to run
1. Install PostgreSQL and open pgAdmin 4 (or use psql).
2. Create/open a practice database.
3. Open `hospital_information_management_analytics.sql` in Query Tool.
4. Execute the script. It creates a schema named `abc_hospital`, drops that schema first if it already exists, creates tables and indexes, inserts sample records,
    and runs the practice queries.
5. To rerun individual questions, execute the selected query under its `Qxx` comment.

Main tables
- Master data: `departments`, `doctors`, `employees`, `patients`, `rooms`, `medicines`
- Clinical/operations: `appointments`, `admissions`, `diagnoses`, `prescriptions`, `lab_tests`, `insurance`
- Finance: `payments`
- Reporting: `doctor_performance`, `patient_analytics`, `revenue_analytics`

SQL concepts demonstrated
- DDL, DML, primary/foreign keys, unique/check constraints
- INNER/LEFT JOIN, aggregates, GROUP BY, HAVING
- Correlated and non-correlated subqueries, EXISTS / NOT EXISTS, ANY / ALL
- INTERSECT and EXCEPT
- CTEs and recursive CTEs
- Window functions: ROW_NUMBER, RANK, DENSE_RANK, LAG, running totals
- Views, indexes, EXPLAIN ANALYZE
- Transactions and safe duplicate-review/deletion template
- Patient, doctor, department, billing and revenue analytics

Business questions covered
Salary ranking; top doctors by department; salary comparisons against hospital/department averages; doctors without appointments; patient appointment/admission 
history; oldest patient; repeat admissions; department staffing and patient counts; duplicate patients/emails; missing phone numbers; expired medicines;
unpaid bills and outstanding balances; total/monthly revenue; highest revenue month; running revenue; month-over-month change; doctor revenue; treatment 
cost by department; recursive employee hierarchy; and query plan inspection.

 Important assumptions
- “Patients treated” is calculated using distinct patients with `Completed` appointments.
- “Revenue” is shown as **billed**, **collected**, and **outstanding** separately. Collected revenue is `amount_paid`; billed revenue is `bill_amount`.
- Doctor/department revenue attribution is only possible where a payment links to an appointment or admission with a doctor.
  Payments without such a link should be reported separately in a production model.
- Salary queries refer to the `doctors.salary` column unless explicitly described as employee hierarchy.
- The duplicate patient cleanup is commented out and uses `ROLLBACK` by default. Back up data, check foreign-key dependencies, and review candidate
   duplicates before deleting anything.
- The billing transaction is a demonstration and rolls back by default.
- The sample is small so the queries are easy to verify; it does not simulate hundreds of doctors or thousands of patients.




