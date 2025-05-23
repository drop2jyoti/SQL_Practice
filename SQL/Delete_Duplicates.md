#Using following code generate the schema Person 

#Create table If Not Exists Person (Id int, Email varchar(255))

#Truncate table Person

#insert into Person (id, email) values ('1', 'john@example.com')

#insert into Person (id, email) values ('2', 'bob@example.com')

#insert into Person (id, email) values ('3', 'john@example.com')

--- This query works in MS SQL. USing CTE was causing CTE not updatable error. So using simple approach of inner joins

Delete p1 from person p1 INNER JOIN person p2 on p1.email = p2.email where p1.id > p2.id;

--- This query will work in Postgres ---

DELETE FROM person
WHERE id IN
    (SELECT id
    FROM
        (SELECT id,email,
         ROW_NUMBER() OVER( PARTITION BY email
        ORDER BY  id ) AS row_num
        FROM person ) t
        WHERE t.row_num > 1 );
