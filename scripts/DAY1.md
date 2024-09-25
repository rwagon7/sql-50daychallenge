# Problem Statement

Table: Products

-------------------------
| Column Name | Type    |
-------------------------
| productId  | int      |
| lowFats    | enum     |
| recyclable | enum     |
-------------------------
productId is the primary key (column with unique values) for this table.
lowFats is an ENUM (category) of type ('Y', 'N') where 'Y' means this product is low fat and 'N' means it is not.
recyclable is an ENUM (category) of types ('Y', 'N') where 'Y' means this product is recyclable and 'N' means it is not.
 

Write a solution to find the ids of products that are both low fat and recyclable.

Return the result table in any order.

The result format is in the following example.

 

Example 1:

Input: 
Products table:

----------------------------------------
| productId   | lowFats  | recyclable  |
----------------------------------------
| 0           | Y        | N           |
| 1           | Y        | Y           |
| 2           | N        | Y           |
| 3           | Y        | Y           |
| 4           | N        | N           |
----------------------------------------

| productId   | lowfats  | recyclable  |
|



Output: 

---------------
| productId   |
---------------
| 1           |
| 3           |
---------------
Explanation: Only products 1 and 3 are both low fat and recyclable.


# Solution

- select productId from table Products where recyclable = 'Y' and lowFats = 'Y';

