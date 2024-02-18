# SQL_queries
where I am putting my queries as i learn SQLite

.open test.db		      	<- opens the db file you have stored data in
.mode column	      		<- changes the view to one that shows headers and data
select * from table	  	<- shows everything in the table
select col from table		<- shows just that column's data

ALTER TABLE my_table
  ADD column1 INT;	    	<- changes a table by adding a column

update Sharret_family
  set fav_food = 'pizza'
  where row = 1;        <- this updates column 'fav_food' with value 'pizza' where the value of 'row' column equals 1

update Sharret_family
  set fav_food =
  case
           when Name = 'robin' then 'cheese'
           when name = 'caleb' then 'noodles'
           when Name = 'samantha' then 'cereal'
           when Name = 'parker' then 'yogurt'
           else fav_food
  end
  where Name IN ('robin', 'caleb', 'samantha', 'parker');    <- this updates sever fields at once. can alter the 'else' statement to a default value

insert into Kamin (row, Name, bday, age, fav_food)
   values (2, 'rachel', '1984-11-30',39, 'tea'),
   (3, 'nathan', '2016-03-02',8, 'pizza'),
   (4, 'faye', '2017-05-18',7, 'pizza'),
   (5, 'sandra', '2019-10-05',3, 'hotdog');   <- inserts data into the table. list the desired columns to update. use values once. have comma at end. 

 select Name from Sharret_family where fav_food = 'pizza'
 union
 select Name from kamin where fav_food = 'pizza';    <-- this returns the names where fav-food = pizza from two tables


select *
  from Kamin
  where bday like '1984-%';         <- this searches a col for a specific set of characters in one table

select *
  from (
    select *,'Sharret_family' AS source_table
    from Sharret_family
    where bday like '1984-%'
    union all
    select *,'Kamin' AS source_table
    from Kamin
    where bday like '1984-%'
    ) as combined_tables;          <- this searches col in seperate DB for a specific set of char in two DB and adds a col describing which table it came from.


select Sharret_family.bday, Sharret_family.Name, Kamin.bday, Kamin.Name
  from Sharret_family
  inner JOIN Kamin on Sharret_family.fav_food = Kamin.fav_food;  <-- this searches for the data where both have matching foods. the out put is for each match.

SELECT Sharret_family.bday, Sharret_family.Name, Kamin.bday, Kamin.Name
  FROM Sharret_family
  INNER JOIN Kamin ON strftime('%Y', Sharret_family.bday) = strftime('%Y', Kamin.bday)
  WHERE strftime('%Y', Sharret_family.bday) = '1984';            <-- this searches for the data where both have matching dates. the out put is for each match.
