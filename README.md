# Library-Management-System
This Library Management System developed by using SQL

CREATE DATABASE LIBRARY


-------------------------ADD TABLE LOGIN--------------
CREATE TABLE Log_In 
(
Roll_Id				INT				NOT NULL,
L_User_Name			VARCHAR(50)		NOT NULL  UNIQUE ,
L_Password			VARCHAR(20)		NOT NULL,
E_mail				VARCHAR(20)				,
Librarian_id		INTEGER			NOT NULL,

CONSTRAINT PK_Log_In PRIMARY KEY ( Roll_Id ),
CONSTRAINT FK_Log_In FOREIGN KEY ( Librarian_id ) REFERENCES Librarian(Librarian_id)
);

INSERT INTO Log_In VALUES(50001,'N.G Harry','MASE2020harry','harry120@gmail.com',20001);
DELETE FROM Log_In 
Where Roll_Id='50001'


INSERT INTO Log_In VALUES(50002,'N.V Harry','MASE2021harry','harry129@gmail.com',20001);


 --------------ADD TABLE LIBRARIAN----------------------------
CREATE TABLE  Librarian
(
Librarian_id		INTEGER			NOT NULL,
First_name			VARCHAR(50)		NOT NULL,
Middle_name			VARCHAR(50)				,
Surname				VARCHAR(50)				,
L_Address			VARCHAR(50)		NOT NULL,
L_dob				DATE			NOT NULL,
L_Tele_No			INT				NOT NULL,
Lib_Salary			DECIMAL			NOT NULL,

CONSTRAINT PK_Librarian PRIMARY KEY ( Librarian_id )
);

INSERT INTO Librarian VALUES(20001,'Harry','karthik','Gunawardhene','No:85/A francy road clombo 7','1995-02-10',0771125864,75000);


--------------ADD TABLE MEMBER----------------
CREATE TABLE Member
(
Member_Id			INT				NOT NULL,
First_name			VARCHAR(50)		NOT NULL,
Middle_name			VARCHAR(50)				,
Surname				VARCHAR(50)		NOT NULL,
M_Address			VARCHAR(50)		NOT NULL,
M_dob				DATE			NOT NULL,
M_Tele_No			INT				NOT NULL,
Member_type			VARCHAR(50)				,
Gender				VARCHAR(50)				,	
Email				VARCHAR(50)				,
Active				CHAR(6)					,
Librarian_id		INTEGER			NOT NULL,

CONSTRAINT PK_Member PRIMARY KEY ( Member_Id ),
CONSTRAINT FK_Member FOREIGN KEY ( Librarian_id ) REFERENCES Librarian	
);	

INSERT INTO Member VALUES(10001,'Hesh','Nirmal','Nanayakkara','No:52/A Galle road,Matara','1999-05-20',0774558215,'student','Male',
'hes125@gmail.com','active',20001);
INSERT INTO Member VALUES(10002,'kalidu','mihisara','ferando','No:12/A zeiya road,galle','1995-05-21',0774452158,'student','Male',
'kalidu45@gmail.com','active',20001);
INSERT INTO Member VALUES(10003,'shihan','mihiranga','kulathunga','No:11/B Nawam mawatha,galle 7','1995-02-21',0775522158,'student','Male',
'shihan525v@gmail.com','active',20001);
INSERT INTO Member VALUES(10004,'lakmali','sehansa','samarathunga','No:10/B jeliya mawatha,matara','1999-02-25',0778522158,'staff','Female',
'lakmali562gm@gmail.com','active',20001);
INSERT INTO Member VALUES(10005,'jhen','zoysa','ferando','No:03/B hasiya road,godagama','1998-02-21',0778854582,'student','Male',
'jhen125km@gmail.com','active',20001);
INSERT INTO Member VALUES(10006,'gayan','sadakelum','gunawardhena','No:14/A kenya road,colombo 6','1995-02-05',0772254558,'staff','Male',
'gay4582gn@gmail.com','active',20001);
INSERT INTO Member VALUES(10007,'dilara','sewwandi','Aarachchi','No:15/V niman road,kelaniya','1998-06-12',0785545852,'student','Female',
'dil4520dmv@gmail.com','active',20001);
INSERT INTO Member VALUES(10008,'zayuri','nimthera','vitharana','No:14/A leniya road,ekala,jaela','1994-02-21',0774458552,'student','Female',
'zayu4582cv@gmail.com','active',20001);
INSERT INTO Member VALUES(10009,'thulini','madushika','vithanage','No:14/B hitetiya road,matara','1999-05-28',0707633468,'student','Female',
'thili196mv@gmail.com','active',20001);
INSERT INTO Member VALUES(10010,'purna','hashen','paliyaguru','No:12/B jeliya road,rathnapura','1998-02-02',0778542254,'student','Male',
'purna458gm@gmail.com','active',20001);


 -----------ADD TABLE FIND TRANSCATION----------

CREATE TABLE Fine
(
Fine_Num			INT				NOT NULL,
Reason				VARCHAR(50)				,
F_Date				DATE			NOT NULL,
F_Time				TIME			NOT NULL,
F_Type				VARCHAR(20)				,
Member_Id			INT				NOT NULL,

CONSTRAINT PK_Fine PRIMARY KEY ( Fine_Num ),
CONSTRAINT FK_Fine FOREIGN KEY ( Member_Id ) REFERENCES Member	
);

INSERT INTO Fine VALUES(101,'Damage Book','2020-02-05','13:30','Bringing a new book',10001); 
INSERT INTO Fine VALUES(131,'The book is lost','2020-07-14','09:45','Bringing a new book',10006); 
INSERT INTO Fine VALUES(103,'The book is lost','2019-04-25','08:15','Bringing a new book',10003); 
INSERT INTO Fine VALUES(104,'damage book pages','2018-02-05','13:30','Bringing a new book',10004); 
INSERT INTO Fine VALUES(106,'coverof the book is damge','2019-03-12','11:30','Bringing a new book',10006); 
INSERT INTO Fine VALUES(107,'The book is lost','2018-02-05','13:30','Bringing a new book',10007); 
INSERT INTO Fine VALUES(110,'Damage Book','2019-12-01','14:45','Bringing a new book',10010); 
INSERT INTO Fine VALUES(112,'Damage Book','2019-10-01','12:45','Bringing a new book',10005); 
INSERT INTO Fine VALUES(113,'The front page of the bok is damaged','2020-05-12','14:30','Bringing a new book',10002); 



--------------ADD TABLE MEMBERSHIP FEE-------------
CREATE TABLE Membership_Fee
(
Invoice_Number				INT			NOT NULL,
Issue_Date					DATE				,
Issue_Time					TIME				,
Membership_expire_date		DATE				,
Member_Id					INT			NOT NULL,

CONSTRAINT PK_Membership_Fee PRIMARY KEY ( Invoice_Number )	,
CONSTRAINT FK_Membership_Fee FOREIGN KEY ( Member_Id ) REFERENCES Member
);
 

INSERT INTO Membership_Fee VALUES(60001,'2020-02-05','13:30','2022-02-05',10001);
INSERT INTO Membership_Fee VALUES(60002,'2020-02-12','14:12','2022-02-12',10002);
INSERT INTO Membership_Fee VALUES(60003,'2019-01-25','11:15','2021-01-25',10003);
INSERT INTO Membership_Fee VALUES(60004,'2018-02-05','08:30','2020-02-05',10004);
INSERT INTO Membership_Fee VALUES(60005,'2020-12-01','13:30','2022-12-01',10005);
INSERT INTO Membership_Fee VALUES(60006,'2019-10-03','09:30','2021-10-03',10006);
INSERT INTO Membership_Fee VALUES(60007,'2018-03-12','10:45','2020-03-12',10007);
INSERT INTO Membership_Fee VALUES(60008,'2019-08-12','13:45','2021-08-12',10008);
INSERT INTO Membership_Fee VALUES(60009,'2020-02-14','14:10','2022-02-14',10009);
INSERT INTO Membership_Fee VALUES(60010,'2019-05-15','14:40','2021-05-15',10010);



-------------------ADD TABLE BOOKS--------------------
CREATE TABLE Book
(
ISBN				CHAR(20)		NOT NULL,
Book_Title			VARCHAR (50)	NOT NULL,
Category			VARCHAR(50)		NOT NULL,
B_Status			VARCHAR(50)				,
Num_of_copies		INTEGER					,
B_State				VARCHAR	(50)			,
Catalog_number		INTEGER					,
Store_row_number	INT						,

Publisher_id		INT				NOT NULL,
Supplier_Id			INT				NOT NULL,

CONSTRAINT PK_Book PRIMARY KEY ( ISBN )		,
CONSTRAINT FK_Book FOREIGN KEY ( Publisher_id ) REFERENCES Publisher ,
				   FOREIGN KEY ( Supplier_Id ) REFERENCES Supplier
);


INSERT INTO BOOK VALUES(20201,'Sybil','comedy','available',10,'exellent',5,2,70001,60001);
INSERT INTO BOOK VALUES(20202,'The pilgrim Progress','classic','available',20,'exellent',5,2,70001,60001);
INSERT INTO BOOK VALUES(20203,'Gullivers travel','love','available',05,'good',5,2,70001,60001);
INSERT INTO BOOK VALUES(20204,'Clarissa','romance','available',06,'exellent',5,2,70001,60003);
INSERT INTO BOOK VALUES(20205,'Tom jhones','classic','available',10,'normal',5,2,70001,60011);
INSERT INTO BOOK VALUES(20206,'Emma','sad','available',20,'exellent',5,2,70001,60013);
INSERT INTO BOOK VALUES(20207,'Frankenstein','horror','available',10,'exellent',5,2,70001,60001);
INSERT INTO BOOK VALUES(20208,'Nightmare abbey','romantic''available',09,'bad',5,2,70001,60011);
INSERT INTO BOOK VALUES(20211,'Nightmare abbility','romantic','available',09,'good',5,2,70001,60011);
INSERT INTO BOOK VALUES(20209,'Jane eyre','classic','available',15,'exellent',5,2,70001,60009);
INSERT INTO BOOK VALUES(20210,'Vanity Fair','commedy','available',16,'good',5,2,70001,60013);
INSERT INTO BOOK VALUES(20215,'far a cross','travel','not-available',10,'good',5,1,70001,60013);

UPDATE Book SET Catalog_number=4
where ISBN='20215'

update Book set Catalog_number=2
where ISBN='20204'
UPDATE Book SET Catalog_number=3
where ISBN='20202'

-------ADD TABLE MEMBER_BOOK-------------
CREATE TABLE Member_Book
(
ISBN				CHAR(20)		NOT NULL,
Member_Id			INT				NOT NULL,
Borrow_Date         DATE			NOT NULL,
Borrow_Time         TIME			NOT NULL,
Submit_Date         DATE			NOT NULL,
Submit_Time         TIME			NOT NULL,

CONSTRAINT PK_Member_Book PRIMARY KEY ( ISBN , Member_Id ) ,
CONSTRAINT FK_Member_Book FOREIGN KEY ( ISBN ) REFERENCES Book ,
						  FOREIGN KEY ( Member_Id ) REFERENCES Member 
);

INSERT INTO Member_Book VALUES(20201,10001,'2020-03-10','12:30','2020-04-10','13:30');
INSERT INTO Member_Book VALUES(20203,10001,'2020-03-16','08:30','2020-04-30','11:30');
INSERT INTO Member_Book VALUES(20204,10002,'2020-04-10','12:30','2020-05-10','13:45');
INSERT INTO Member_Book VALUES(20206,10003,'2020-09-10','11:30','2020-10-10','09:30');
INSERT INTO Member_Book VALUES(20206,10009,'2020-10-10','11:30','2020-11-10','09:30');
INSERT INTO Member_Book VALUES(20204,10005,'2020-05-12','08:30','2020-06-12','13:30');
INSERT INTO Member_Book VALUES(20209,10003,'2020-06-03','11:30','2020-07-10','09:12');
INSERT INTO Member_Book VALUES(20201,10007,'2020-04-11','12:30','2020-05-11','09:30');
INSERT INTO Member_Book VALUES(20201,10010,'2020-04-10','12:25','2020-05-10','09:25');
INSERT INTO Member_Book VALUES(20202,10005,'2020-04-04','09:30','2020-05-04','14:30');


-------ADD TABLE PUBLISHER-------------
CREATE TABLE Publisher
(
Publisher_id		INT				NOT NULL,
Publiser_name		VARCHAR(50)		NOT NULL,
Publisher_year		INT				NOT NULL,

CONSTRAINT PK_Publisher PRIMARY KEY ( Publisher_id )
);

INSERT INTO Publisher VALUES(70001,'R.W James',1998),(70002,'V.A Harry',1999),(70003,'F.A Resh',1995),(70004,'K.V Kushi',1999),
(70005,' L.K Genny',2001),(70006,'W.M Hesh',2002),
(70007,'G.D Samuel',2003),(70008,'F.A Rom',1996),(70009,'D.V Farcy',2001),(70010,'A.V Ema',1996);




-----------------ADD TABLE AUTHOR---------------------
CREATE TABLE Author
(
Author_id			INT				NOT NULL,
Author_name			VARCHAR(50)		NOT NULL,

CONSTRAINT PK_Author PRIMARY KEY ( Author_id )
);

INSERT INTO Author VALUES(701,'Benjamin'),(7002,'Jhon'),(703,'Jonathan '),(704,'Samuelnricherd'),(705,'L.K  Genny'),
(706,'Jane austiene'),(707,'Thomas '),(708,'Henry felding'),(709,'bronte raham' ),(710, 'shelly');



-----------------ADD TABLE AUTHOR_BOOK----------------------------
CREATE TABLE Author_Book
(
Author_id			INT				NOT NULL,
ISBN				CHAR(20)		NOT NULL,

CONSTRAINT PK_Author_Book PRIMARY KEY ( Author_id , ISBN ) ,
CONSTRAINT FK_Author_Book FOREIGN KEY ( Author_id ) REFERENCES Author ,
						  FOREIGN KEY ( ISBN )  REFERENCES Book
);

INSERT INTO Author_Book VALUES(701,20201);
INSERT INTO Author_Book VALUES(701,20202 );
INSERT INTO Author_Book VALUES(701,20203);
INSERT INTO Author_Book VALUES(704,20204 ),(705 , 20210);
INSERT INTO Author_Book VALUES(706,20206 );
INSERT INTO Author_Book VALUES(707,20209 );
INSERT INTO Author_Book VALUES(708,20205 );
INSERT INTO Author_Book VALUES(709,20211 );
INSERT INTO Author_Book VALUES(710,20207 );



-----------------ADD TABLE SUPPLIER---------------------
CREATE TABLE Supplier
(
Supplier_Id			INT				NOT NULL,
S_First_name		VARCHAR(50)		NOT NULL,
S_Middle_name		VARCHAR(50)				,
S_Surname			VARCHAR(50)		NOT NULL,
S_Address			VARCHAR(50)		NOT NULL,
S_Tele_No			INT				NOT NULL,
Supply_Date			DATE	        NOT NULL,
Supply_Time			TIME			NOT NULL,

CONSTRAINT PK_Supplier PRIMARY KEY ( Supplier_Id )
);

INSERT INTO Supplier VALUES(60001,'Harith','goyuman','Gajadeera','No:12/A dadalla road,colombo 7',0788854759,'2019-02-12','12:30');
INSERT INTO Supplier VALUES(60002,'rahul','shekar','ferando','No:11/A zeniya road,gampaha 7',0778554589,'2019-10-12','11:30');
INSERT INTO Supplier VALUES(60003,'suhan','nayanajith','wikramasinghe','No:14/A lakehouse road,ekala',0701125645,'2018-01-13','12:45');
INSERT INTO Supplier VALUES(60011,'raham','fenith','witharana','No:10/A heenma road,rathmalana',0778556854,'2005-05-25','10:12');
INSERT INTO Supplier VALUES(60012,'kelum','sadapahn','ekenayake','No:12/A dadalla road,jaela',0785545852,'2007-04-04','14:45');
INSERT INTO Supplier VALUES(60007,'wikram','goyumantha','abeynayaka','No:12/A dadalla road,dewinuwara',0778554856,'2010-08-01','12:30');
INSERT INTO Supplier VALUES(60013,'Harithya','hennada','wikram','No:12/A dadalla road,matara',0774458521,'2005-02-06','08:30');
INSERT INTO Supplier VALUES(60009,'hasuntha','lakmal','vithana','No:12/A dadalla road,godagama',0712245214,'2013-02-01','15:12');
INSERT INTO Supplier VALUES(60010,'pethum','nirmantha','darmasena','No:32/V sarasa road,kandy',0785554136,'2012-02-25','09:30');


------SELECT AVAILABLE BOOK WITH THEIR BOOK_TITLE,AURTHOR,-----
SELECT Book_Title,Category
FROM Book
WHERE B_Status='available'


----Dispaly the Book_titles which took the Category classic------
SELECT Book_Title ,Catalog_number,Store_row_number 
FROM Book WHERE Category='classic' ;


------Dispaly all contents in Book stable where book_id of book table and Author-Book table are equal------
SELECT b.* FROM Book b,Author_Book r WHERE b.ISBN=r.ISBN ;

SELECT DISTINCT Author_id FROM Author_Book

SELECT DISTINCT b.Book_Title,r.Author_id FROM Book b,Author_Book r WHERE b.ISBN=r.ISBN ;

-----------------------stored procedure----------------------------------------
GO
CREATE PROCEDURE Getmembername
(
@membid INT
)
AS BEGIN 
SELECT First_name FROM Member
WHERE Member_Id=@membid
END



GO
CREATE PROCEDURE BookAdd(
@ISBN				CHAR(20),
@Book_Title			VARCHAR (50),
@Category			VARCHAR(50),
@B_Status			VARCHAR(50),
@Num_of_copies		INTEGER	,
@B_State			VARCHAR	(50),
@Catalog_number		INTEGER	,
@Store_row_number	INT,

@Publisher_id	INT,
@Supplier_Id INT	
)

AS BEGIN
INSERT INTO BOOK VALUES(@ISBN,@Book_Title,@Category,@B_Status,@Num_of_copies,@B_State,@Catalog_number,@Store_row_number,
@Publisher_id,@Supplier_Id)
END


GO
CREATE PROCEDURE Member_select
AS BEGIN
SELECT * FROM Member
END


GO 
CREATE PROCEDURE select_category(
@isbn AS INT
)
AS BEGIN
SELECT Book_Title, Category FROM Book WHERE ISBN=@isbn
END

---------------------ORDER BY NAME & SALARY------------------------
SELECT Member_Id,First_name
FROM Member
ORDER BY First_name ASC

SELECT Librarian_id,First_name,Lib_Salary
FROM Librarian
ORDER BY First_name ASC


SELECT ISBN,Book_Title,Category,Catalog_number
FROM Book
ORDER BY Catalog_number ASC ,Book_Title DESC


----------------COUNT THE NUMBER OF AVAILABLE BOOKS----------------------
SELECT COUNT(Book_Title)
FROM Book
WHERE B_Status='available'

-----FIND MINIUM catalog number OF AVAILBLE  BOOK--------
SELECT MIN(Catalog_number) FROM Book WHERE B_Status='available'

SELECT Book_Title,MAX (Num_of_copies) as copies
FROM Book
GROUP BY Book_Title,Category


----JOIN MEMBERS & MEMBERSHIP FEE TABLE DATA-----
SELECT * FROM Member m1, Membership_Fee m2 WHERE m1.Member_Id=m2.Member_Id 

SELECT Book_Title,SUM (Num_of_copies) FROM Book WHERE num_of_copies>15
GROUP BY Book_Title
HAVING SUM(Num_of_copies)>12


-------------------VIEW STUDENT MEMBERS-------------------------

CREATE VIEW STAF_MEMBERS AS
SELECT First_name,Email,M_Tele_No
FROM Member
WHERE Member_type='student';


CREATE VIEW ST_MEMBERS AS
SELECT First_name,Email,M_Tele_No
FROM Member
WHERE Member_type='student';

CREATE VIEW Active_participant As
SELECT First_name
FROM Member
WHERE active='active'
DROP VIEW Active_participant

CREATE VIEW MINIMUM_COPIES_Of_BOKS AS
SELECT Book_Title,Category ,Catalog_number
FROM Book
WHERE B_Status='available' and Num_of_copies<16 ;


---------------To find a copies of supplier book----------
SELECT(Book.num_of_copies-temp.supplier_book) as available_copies
FROM Book LEFT JOIN(
 SELECT COUNT(*)AS supplier_book
 FROM Supplier
 WHERE Supplier_Id='60002'
 AND Supply_Date='2019-02-12'
 )as temp ON Book.ISBN='20203'
	WHERE Book.ISBN='20203';


--------------To find book with submit date-------------
SELECT Book.Book_Title,Book.Category,Member_Book.Submit_Date
FROM Member_Book
LEFT JOIN Book ON Member_Book.ISBN=Book.ISBN
WHERE Submit_Date='2020-04-30';


------------some other functions---------------
SELECT Member_Id,First_name,Librarian_id FROM Member
WHERE M_dob>'1998-06-12';

SELECT Member_type,First_name,Email FROM Member
WHERE Member_type!='student'

SELECT First_name,Member_type,Gender
FROM Member ORDER BY First_name DESC;
