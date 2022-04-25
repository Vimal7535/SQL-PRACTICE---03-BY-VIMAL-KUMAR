# SQL-PRACTICE---03-BY-VIMAL-KUMAR



create database project
use project

create table Employee_Details(ID int primary key not null,F_Name varchar(20),
L_NAme varchar(20),Salary money,Joining_Date date,Department varchar(20),Gender varchar(20))

insert into Employee_Details values
(2,'vikash','ahalabat',60000,'2013-02-15','IT','Male'),
(3,'nikite','jain',53000,'2014-01-09','HR','Female'),
(4,'shweta','sharma',50000,'2013-02-15','IT','Female'),
(5,'moham','rana',60000,'2013-02-15','HR','Male'),
(6,'Raju','ram',45000,'2013-02-20','IT','Male'),
(7,'sanjeev','kumar',60000,'2013-02-15','IT','Male')

create table Project_Details(PD_ID int primary key identity , ED_ID int , Project_Name varchar(20))

insert into Project_Details values
(1,'Task Track'),
(1,'HRM'),
(2,'CRM'),
(3,'Policy Management'),
(3,'Sales Management'),
(3,'GRS'),
(4,'DDS'),
(6,'CLP'),
(7,'Survey Management')

select * from Employee_Details
select * from Project_Details

select * from Employee_Details a inner join Project_Details b on a.ID = b.ED_ID order by f_name


select f_name,project_name from Employee_Details a inner join Project_Details b on a.ID = b.ED_ID order by f_name

select f_name,project_name from Employee_Details a left join Project_Details b on a.ID = b.ED_ID order by f_name

select f_name,isnull(Project_Name,'No Project') from Employee_Details a right join Project_Details b on a.ID = b.ED_ID order by f_name

select f_name,project_name from Employee_Details a right join Project_Details b on a.ID = b.ED_ID order by f_name

select f_name,project_name from Employee_Details a full join Project_Details b on a.ID = b.ED_ID order by f_name

select F_Name,isnull(Project_Name,'Not Project Assigned') from Employee_Details a left join Project_Details b on a.ID = b.ED_ID order by f_name

select project_name from Employee_Details a right join Project_Details b on a.ID = b.ED_ID  where f_name is null

select f_name,project_name from Employee_Details a inner join Project_Details b on a.ID = b.ED_ID where ID in
(select ED_ID from Project_Details group by ED_ID having count(*)>1)
