5. select * from customers where city like 'Kansas%' and fname like 'Bridget';
Bridget Burch (1139477)

13.
select * from products order by cost desc limit 3;

+---------+------------+-----------------------------------------------+--------+--------+-------------+
| prod_id | brand      | name                                          | price  | cost   | shipping_wt |
+---------+------------+-----------------------------------------------+--------+--------+-------------+
| 1274321 | Byteweasel | Hadoop Cluster, Economy (4-node)              | 975149 | 952934 | 570         |
| 1274308 | Gigabux    | Server (2U rackmount, eight-core, 64GB, 12TB) | 614559 | 556183 | 121         |
| 1274307 | Krustybitz | Server (2U rackmount, eight-core, 64GB, 12TB) | 599319 | 542497 | 121         |
+---------+------------+-----------------------------------------------+--------+--------+-------------+
Fetched 3 row(s) in 0.49s

19.
training@localhost queries]$ impala-shell -f verify_tablet_order.sql
Starting Impala Shell without Kerberos authentication
Connected to localhost.localdomain:21000
Server version: impalad version 2.6.0-cdh5.8.0 RELEASE (build 8d8652f69461f0dd8d5f474573fb5de7ceb0ee6b)
Query: -- Query to find the order for the
-- tablet (product ID 1274348) from the
-- contest winner (customer ID 1139477)
SELECT o.order_id, fname, lname, o.order_date
FROM customers c
JOIN orders o
   ON (c.cust_id = o.cust_id)
JOIN order_details d
   ON (o.order_id = d.order_id)
WHERE d.prod_id=1274348
  AND c.cust_id=1139477

+----------+---------+-------+---------------------+
| order_id | fname   | lname | order_date          |
+----------+---------+-------+---------------------+
| 6662689  | Bridget | Burch | 2013-05-31 17:31:11 |
| 6621368  | Bridget | Burch | 2013-05-20 21:17:03 |
+----------+---------+-------+---------------------+
Fetched 2 row(s) in 9.71s
