
SELECT COUNT(*) FROM bankloandataset;
select * from bankloandataset;
select count(id) as Total_Loan_Applications from bankloandataset;
select count(id) as MTD_Total_Loan_Applications from bankloandataset
where month(issue_date) = 12 and year(issue_date) = 2021;
DESCRIBE bankloandataset;
SELECT DISTINCT issue_date FROM bankloandataset LIMIT 10;
ALTER TABLE bankloandataset ADD issue_date_converted DATE;
UPDATE bankloandataset
SET issue_date_converted = STR_TO_DATE(issue_date, '%Y-%m-%d');

SET SQL_SAFE_UPDATES = 0;
UPDATE bankloandataset
SET issue_date_converted = STR_TO_DATE(issue_date, '%Y-%m-%d');

SET SQL_SAFE_UPDATES = 1;
SELECT DISTINCT issue_date, issue_date_converted FROM bankloandataset LIMIT 10;
ALTER TABLE bankloandataset DROP COLUMN issue_date;

SHOW COLUMNS FROM bankloandataset;

ALTER TABLE bankloandataset DROP COLUMN issue_date;
ALTER TABLE bankloandataset CHANGE issue_date_converted issue_date DATE;

select count(id) as MTD_Total_Loan_Applications from bankloandataset
where month(issue_date) = 12 and year(issue_date) = 2021;

select count(id) as PMTD_Total_Loan_Applications from bankloandataset
where month(issue_date) = 11 and year(issue_date) = 2021;
-- (MTD-PMTD)/PMTD

select sum(loan_amount) as MTD_Total_Funded_Amount from bankloandataset
where month(issue_date) = 12 and year(issue_date) = 2021;

select sum(loan_amount) as PMTD_Total_Funded_Amount from bankloandataset
where month(issue_date) = 11 and year(issue_date) = 2021;

select sum(total_payment) as MTD_Total_Amount_Received from bankloandataset
where month(issue_date) = 12 and year(issue_date) = 2021;

select sum(total_payment) as PMTD_Total_Amount_Received from bankloandataset
where month(issue_date) = 11 and year(issue_date) = 2021;

select round(avg(int_rate) * 100, 4)  as MTD_Avg_Interest_Rate from bankloandataset
where month(issue_date) = 12 and year(issue_date) = 2021;

select round(avg(int_rate) * 100 , 4) as PMTD_Avg_Interest_Rate from bankloandataset
where month(issue_date) = 11 and year(issue_date) = 2021;

select round(avg(dti) * 100 , 4) as MTD_Avg_DTI from bankloandataset
where month(issue_date) = 12 and year(issue_date) = 2021;

select round(avg(dti) * 100 , 4)  as PMTD_Avg_DTI from bankloandataset
where month(issue_date) = 11 and year(issue_date) = 2021;

select loan_status from bankloandataset;

select
     round(
     (count(case when loan_status = 'Fully Paid' or loan_status = 'Current' then id end) * 100) 
      / count(id) , 2) as Good_Loan_Percentage 
from bankloandataset;

select count(id) as Good_Loan_Applications from bankloandataset
where loan_status = 'Fully Paid' or loan_status = 'Current';

select sum(loan_amount) as Good_Loan_Funded_Amount from bankloandataset
where loan_status = 'Fully Paid' or loan_status = 'Current';
 
select sum(total_payment) as Good_Loan_Recieved_Amount from bankloandataset
where loan_status = 'Fully Paid' or loan_status = 'Current';

SELECT
    (COUNT(CASE WHEN loan_status = 'Charged Off' THEN id END) * 100.0) / 
	COUNT(id) AS Bad_Loan_Percentage
FROM bankloandataset;

select count(id) as Bad_Loan_Applications from bankloandataset
where loan_status = 'Charged Off';

select sum(loan_amount) as Bad_Loan_Funded_Amount from bankloandataset
where loan_status = 'Charged Off';

select sum(total_payment) as Bad_Loan_Amount_Received from bankloandataset
where loan_status = 'Charged Off';

SELECT
        loan_status,
        COUNT(id) AS Total_Loan_Applications,
        SUM(total_payment) AS Total_Amount_Received,
        SUM(loan_amount) AS Total_Funded_Amount,
        AVG(int_rate * 100) AS Interest_Rate,
        AVG(dti * 100) AS DTI
    FROM
        bankloandataset
    GROUP BY
        loan_status;

  SELECT 
	loan_status, 
	SUM(total_payment) AS MTD_Total_Amount_Received, 
	SUM(loan_amount) AS MTD_Total_Funded_Amount 
FROM bankloandataset
WHERE MONTH(issue_date) = 12 
GROUP BY loan_status;

/*SELECT 
	MONTH(issue_date) AS Month_Number, 
	MONTHNAME(MONTH, issue_date) AS Month_Name, 
	COUNT(id) AS Total_Loan_Applications,
	SUM(loan_amount) AS Total_Funded_Amount,
	SUM(total_payment) AS Total_Received_Amount
FROM bankloandataset
GROUP BY MONTH(issue_date), DATENAME(MONTH, issue_date)
ORDER BY MONTH(issue_date); */

SELECT 
  MONTH(issue_date) AS Month_Number, 
  MONTHNAME(issue_date) AS Month_Name, 
  COUNT(id) AS Total_Loan_Applications,
  SUM(loan_amount) AS Total_Funded_Amount,
  SUM(total_payment) AS Total_Received_Amount
FROM bankloandataset
GROUP BY MONTH(issue_date), MONTHNAME(issue_date)
ORDER BY MONTH(issue_date);

SELECT 
	address_state AS State, 
	COUNT(id) AS Total_Loan_Applications,
	SUM(loan_amount) AS Total_Funded_Amount,
	SUM(total_payment) AS Total_Received_Amount
FROM bankloandataset
GROUP BY address_state
ORDER BY COUNT(id) DESC;

SELECT 
	term AS Term, 
	COUNT(id) AS Total_Loan_Applications,
	SUM(loan_amount) AS Total_Funded_Amount,
	SUM(total_payment) AS Total_Received_Amount
FROM bankloandataset
GROUP BY term
ORDER BY term;

SELECT 
	emp_length AS Employee_Length, 
	COUNT(id) AS Total_Loan_Applications,
	SUM(loan_amount) AS Total_Funded_Amount,
	SUM(total_payment) AS Total_Received_Amount
FROM bankloandataset
GROUP BY emp_length
ORDER BY emp_length;

SELECT 
	emp_length AS Employee_Length, 
	COUNT(id) AS Total_Loan_Applications,
	SUM(loan_amount) AS Total_Funded_Amount,
	SUM(total_payment) AS Total_Received_Amount
FROM bankloandataset
GROUP BY emp_length
ORDER BY COUNT(id) DESC;

SELECT 
	purpose AS PURPOSE, 
	COUNT(id) AS Total_Loan_Applications,
	SUM(loan_amount) AS Total_Funded_Amount,
	SUM(total_payment) AS Total_Received_Amount
FROM bankloandataset
GROUP BY purpose
ORDER BY purpose;

SELECT 
	purpose AS PURPOSE, 
	COUNT(id) AS Total_Loan_Applications,
	SUM(loan_amount) AS Total_Funded_Amount,
	SUM(total_payment) AS Total_Received_Amount
FROM bankloandataset
GROUP BY purpose
ORDER BY COUNT(id) DESC;

SELECT 
	home_ownership AS Home_Ownership, 
	COUNT(id) AS Total_Loan_Applications,
	SUM(loan_amount) AS Total_Funded_Amount,
	SUM(total_payment) AS Total_Received_Amount
FROM bankloandataset
GROUP BY home_ownership
ORDER BY count(id) DESC;
