# SQL Security Log Analysis Portfolio

## Project Overview
This project demonstrates how SQL can be used by a security analyst to investigate suspicious activity, identify unauthorized access, and support incident response. The queries simulate real SOC workflows using login activity and employee asset data.

## Skills Demonstrated
- Filtering security logs using `AND`, `OR`, and `NOT`
- Investigating failed authentication attempts
- Analyzing login activity by time, date, and geography
- Identifying affected users and departments during incidents
- Writing clear, security-focused documentation

---

## 🔍 After-Hours Failed Login Attempts
**Purpose:** Identify failed login attempts occurring after business hours, which may indicate brute-force or credential-stuffing activity.

📅 Login Attempts on Suspicious Dates
Purpose: Review authentication activity around a known security incident.
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00'
AND success = 0;

🌍 Login Attempts Outside of Mexico
Objective: Identify login attempts that did not originate from Mexico.
Security Value:
Supports geographic anomaly detection and potential account compromise investigations.
SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-09'
OR login_date = '2022-05-08';

🏢 Employees in Marketing (East Building)
Objective: Identify Marketing employees located in East offices.
Security Value:
Used to target security updates to specific departments and locations.
SELECT *
FROM log_in_attempts
WHERE NOT country LIKE 'MEX%';

🏢 Employees in Marketing (East Building)
Objective: Identify Marketing employees located in East offices.
Security Value:
Used to target security updates to specific departments and locations.
SELECT *
FROM employees
WHERE department = 'Marketing'
AND office LIKE 'East%';

💰 Employees in Finance or Sales
Objective: Retrieve employees in Finance or Sales departments.
Security Value:
Supports role-based security updates and compliance operations.
Query Used:
SELECT *
FROM employees
WHERE department = 'Finance'
OR department = 'Sales';

🚫 Employees Not in IT
Objective: Identify employees outside the IT department.
Security Value:
Ensures non-IT endpoints receive required security updates.
SELECT *
FROM employees
WHERE NOT department = 'Information Technology';

🧠 SOC Analyst Skills Demonstrated
SQL filtering with AND / OR / NOT
Pattern matching using LIKE
Authentication log analysis
Endpoint targeting based on department and location
Translating technical queries into security use cases

🛠 Tools Used
MariaDB / MySQL
SQL
GitHub for documentation

📈 Why This Matters
These queries reflect real SOC workflows used in incident response, threat hunting, and operational security tasks.

