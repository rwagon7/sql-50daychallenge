# PROBLEM STATEMENT

Table: Customer

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| name        | varchar |
| referee_id  | int     |
+-------------+---------+
In SQL, id is the primary key column for this table.
Each row of this table indicates the id of a customer, their name, and the id of the customer who referred them.
 

Find the names of the customer that are not referred by the customer with id = 2.

Return the result table in any order.

The result format is in the following example.

 

Example 1:

Input: 
Customer table:
+----+------+------------+
| id | name | referee_id |
+----+------+------------+
| 1  | Will | null       |
| 2  | Jane | null       |
| 3  | Alex | 2          |
| 4  | Bill | null       |
| 5  | Zack | 1          |
| 6  | Mark | 2          |
+----+------+------------+
Output: 
+------+
| name |
+------+
| Will |
| Jane |
| Bill |
| Zack |
+------+

# SOLUTION

1. Approach: Using <>(!=) and IS NULL [Accepted]
Intuition

2. Some people come out the following solution by intuition.

3. SELECT name FROM customer WHERE referee_Id <> 2;
However, this query will only return one result:Zack although there are 4 customers not referred by Jane (including Jane herself). All the customers who were referred by nobody at all (NULL value in the referee_id column) don’t show up. But why?

Algorithm

1. MySQL uses three-valued logic -- TRUE, FALSE and UNKNOWN. Anything compared to NULL evaluates to the third value: UNKNOWN. That “anything” includes NULL itself! That’s why MySQL provides the IS NULL and IS NOT NULL operators to specifically check for NULL.

2. Thus, one more condition 'referee_id IS NULL' should be added to the WHERE clause as below.

MySQL

1. SELECT name FROM customer WHERE referee_id <> 2 OR referee_id IS NULL;
or

2. SELECT name FROM customer WHERE referee_id != 2 OR referee_id IS NULL;

Tips

1. The following solution is also wrong for the same reason as mentioned above. The key is to always use IS NULL or IS NOT NULL operators to specifically check for NULL value.

2. SELECT name FROM customer WHERE referee_id = NULL OR referee_id <> 2;
