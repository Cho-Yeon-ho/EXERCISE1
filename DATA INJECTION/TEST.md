1.   1)쿼리
select name from products c join (select b.prod_id, count(*) as cc from order_details a join products b on a.prod_id = b.prod_id group by b.prod_id order by cc desc limit 3) d
 on c.prod_id = d.prod_id;
    2) 결과

     Tablet PC (10 in. display, 64 GB)
2	8GB DDR3-1600 (PC3-12800) Dual Channel Desktop Memory Kit (2x4GB)
3	F Jack Male-to-Male Cable (12 in.)

2.
1) 쿼리
 select * from order_details a join products b on a.prod_id = b.prod_id order by b.price desc limit 10;

2) 결과

5067798	1274315	1274315	Sparky	Server (1U rackmount, hex-core, 16GB, 8TB)	470019	378842	79
2	5430556	1274315	1274315	Sparky	Server (1U rackmount, hex-core, 16GB, 8TB)	470019	378842	79
3	5498245	1274315	1274315	Sparky	Server (1U rackmount, hex-core, 16GB, 8TB)	470019	378842	79
4	5233610	1274315	1274315	Sparky	Server (1U rackmount, hex-core, 16GB, 8TB)	470019	378842	79
5	5442003	1274315	1274315	Sparky	Server (1U rackmount, hex-core, 16GB, 8TB)	470019	378842	79
6	5151385	1274315	1274315	Sparky	Server (1U rackmount, hex-core, 16GB, 8TB)	470019	378842	79
7	5197693	1274315	1274315	Sparky	Server (1U rackmount, hex-core, 16GB, 8TB)	470019	378842	79
8	5441754	1274315	1274315	Sparky	Server (1U rackmount, hex-core, 16GB, 8TB)	470019	378842	79
9	5070376	1274315	1274315	Sparky	Server (1U rackmount, hex-core, 16GB, 8TB)	470019	378842	79
10	5274191	1274315	1274315	Sparky	Server (1U rackmount, hex-core, 16GB, 8TB)	470019	378842	79

3. 
