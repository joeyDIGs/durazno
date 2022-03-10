# A&M SQL Interview Question - Guest Requests - Last 3

## Motivation
We are developing a dashboard for our hotel's concierge services to improve guest relations and provide better service.

## Tables

### Guests

| Column Name   | Type    |
|--------------- | --------- |
| guest_id   | int     |
| name          | varchar |

`guest_id` is the primary key for this table.
This table contains information about Guests.
 

### Requests

| Column Name   | Type    |
| --------------- | --------- |
| request_id      | int     |
| request_date    | date    |
| guest_id   | int     |
| estimated_cost          | int     |

`request_id` is the primary key for this table.
This table contains information about the requests made by `guest_id`.
Each guest can make at most one request per day.
 
## Task
We need to summarize the most recent `three` requests of each guest, but if a guest has made less than that many requests, return all of them.

The request of the results should be by `guest_name` ascending first. In case of a tie, then ascending by `guest_id`, if there's still a tie, then descending by `request_date`

## Examples

Example 1:

Input: 
Guests table:

| guest_id | name      |
| ------------- | ----------- |
| 1           | Phil   |
| 2           | John  |
| 3           | Anna |
| 4           | Marina    |
| 5           | Kai    |

Requests table:

| request_id | request_date | guest_id | estimated_cost |
| ---------- | ------------ | ------------- | ------ |
| 1        | 2020-07-31 | 1           | 30   |
| 2        | 2020-07-30 | 2           | 40   |
| 3        | 2020-07-31 | 3           | 70   |
| 4        | 2020-07-29 | 4           | 100  |
| 5        | 2020-06-10 | 1           | 1010 |
| 6        | 2020-08-01 | 2           | 102  |
| 7        | 2020-08-01 | 3           | 111  |
| 8        | 2020-08-03 | 1           | 99   |
| 9        | 2020-08-07 | 2           | 32   |
| 10       | 2020-07-15 | 1           | 2    |

Output: 

| guest_name | guest_id | request_id | request_date |
| --------------- | ------------- | ---------- | ------------ |
| Anna     | 3           | 7        | 2020-08-01 |
| Anna     | 3           | 3        | 2020-07-31 |
| John      | 2           | 9        | 2020-08-07 |
| John      | 2           | 6        | 2020-08-01 |
| John      | 2           | 2        | 2020-07-30 |
| Marina        | 4           | 4        | 2020-07-29 |
| Phil       | 1           | 8        | 2020-08-03 |
| Phil       | 1           | 1        | 2020-07-31 |
| Phil       | 1           | 10       | 2020-07-15 |

Explanation: 
Phil has 4 requests, we discard the request of "2020-06-10" because it is the oldest request.
Anna has only 2 requests, we return them.
John has exactly 3 requests.
Marina requested only one time.
We sort the result table by guest_name in ascending request, by guest_id in ascending request, and by request_date in descending request in case of a tie.

```sql
Create table If Not Exists Guests (guest_id int, name varchar(10));
Create table If Not Exists Requests (request_id int, request_date date, guest_id int, estimated_cost int);

-- Truncate table Guests

insert into Guests (guest_id, name) values ('1', 'Phil');
insert into Guests (guest_id, name) values ('2', 'John');
insert into Guests (guest_id, name) values ('3', 'Anna');
insert into Guests (guest_id, name) values ('4', 'Marina');
insert into Guests (guest_id, name) values ('5', 'Kai');

-- Truncate table Requests

insert into Requests (request_id, request_date, guest_id, estimated_cost) values ('1', '2020-07-31', '1', '30');
insert into Requests (request_id, request_date, guest_id, estimated_cost) values ('2', '2020-7-30', '2', '40');
insert into Requests (request_id, request_date, guest_id, estimated_cost) values ('3', '2020-07-31', '3', '70');
insert into Requests (request_id, request_date, guest_id, estimated_cost) values ('4', '2020-07-29', '4', '100');
insert into Requests (request_id, request_date, guest_id, estimated_cost) values ('5', '2020-06-10', '1', '1010');
insert into Requests (request_id, request_date, guest_id, estimated_cost) values ('6', '2020-08-01', '2', '102');
insert into Requests (request_id, request_date, guest_id, estimated_cost) values ('7', '2020-08-01', '3', '111');
insert into Requests (request_id, request_date, guest_id, estimated_cost) values ('8', '2020-08-03', '1', '99');
insert into Requests (request_id, request_date, guest_id, estimated_cost) values ('9', '2020-08-07', '2', '32');
insert into Requests (request_id, request_date, guest_id, estimated_cost) values ('10', '2020-07-15', '1', '2');

```
