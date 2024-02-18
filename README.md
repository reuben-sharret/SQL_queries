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
 select Name from kamin where fav_food = 'pizza';    <-- this returns the names where fav-food = pizza
