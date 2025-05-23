#Using following code generate the schema Person 

#Create table If Not Exists Person (Id int, Email varchar(255))

#Truncate table Person

#insert into Person (id, email) values ('1', 'john@example.com')

#insert into Person (id, email) values ('2', 'bob@example.com')

#insert into Person (id, email) values ('3', 'john@example.com')



Delete p1 from person p1 INNER JOIN person p2 on p1.email = p2.email where p1.id > p2.id
