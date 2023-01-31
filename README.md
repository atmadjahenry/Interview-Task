# Interview-Task

Create Table Employee
mysql> create table employee (
    -> id int not null primary key auto_increment,
    -> employeeid char(10) not null,
    -> fullname char(100) not null,
    -> birthdate date not null,
    -> address varchar(500),
    -> unique(employeeid)
    -> );
	
	
Insert Value to Employee Table	
mysql> insert into employee values
    -> (null, '10105001', 'Ali Anton', '1982-08-19', 'Jakarta Utara'),
    -> (null, '10105002', 'Rara Siva', '1982-01-01', 'Mandalika'),
    -> (null, '10105003', 'Rini Aini', '1982-02-20', 'Sumbawa Besar'),
    -> (null, '10105004', 'Budi', '1982-02-22', 'Mataram Kota');
	

Create Table Position History
mysql> create table position_history (
    -> id int not null primary key auto_increment,
    -> posid char(10) not null,
    -> postitle char(100) not null,
    -> employeeid char(10) not null,
    -> startdate date not null,
    -> enddate date not null,
    -> check (startdate <= enddate)
    -> );
	
	
Insert Value to Position History Table	
mysql> insert into position_history values
    -> (null, '50000', 'IT Manager', '10105001', '2022-01-01', '2022-02-28'),
    -> (null, '50001', 'IT Sr. Manager', '10105001', '2022-03-01', '2022-12-31'),
    -> (null, '50002', 'Programmer Analyst', '10105002', '2022-01-01', '2022-02-28'),
    -> (null, '50003', 'Sr. Programmer Analyst', '10105002', '2022-03-01', '2022-12-31'),
    -> (null, '50004', 'IT Admin', '10105003', '2022-01-01', '2022-02-28'),
    -> (null, '50005', 'IT Secretary', '10105003', '2022-03-01', '2022-12-31')
    -> ;
	
display all employee (EmployeeId, FullName, BirthDate, Address) data with their current position information (PosId, PosTitle, EmployeeId, StartDate, EndDate).
mysql> select a.employeeid, a.fullname, a.birthdate, a.address, b.posid, b.postitle, b.employeeid, b.startdate, b.enddate from employee a
    -> join position_history b on a.employeeid = b.employeeid;
    -> where enddate >= date(curdate());
