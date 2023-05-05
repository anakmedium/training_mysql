# training_mysql
traing mysql neuron

**1. Mengetahui tempat bekerja employee**
```sql
select * from employees as e
join offices as o on e.officeCode = o.officeCode;

```
<details><summary>result</summary>

![image](https://user-images.githubusercontent.com/56218029/236399853-68754bc4-2cea-472e-8671-687fdb7e31ac.png)

</details>

**2.  mengambil data employee yang bekerja di kota tertentu** 
```sql

select * from employees as e
join offices as o on e.officeCode = o.officeCode
where o.city = 'Boston';

```
<details><summary>result</summary>

![image](https://user-images.githubusercontent.com/56218029/236400415-5271c87e-bebf-4c1b-8129-21835b81abb6.png)

</details>

**3.   mengambil data prodak beserta product line nya** 
```sql

select * from products p 
join productlines as pr on p.productLine = pr.productLine ;

```
<details><summary>result</summary>

![image](https://user-images.githubusercontent.com/56218029/236400546-19e3522f-61ec-4461-8944-964c21fb667d.png)

</details>

**4.  mengambil data prodak dengan product line tertentu** 
```sql

select * from products p 
join productlines as pr on p.productLine = pr.productLine 
where pr.productLine = 'Vintage Cars';

```
<details><summary>result</summary>

![image](https://user-images.githubusercontent.com/56218029/236400707-a4566128-5b25-4408-b405-355ce531fa03.png)

</details>

**5.  mengambil data prodak vintage diurutkan dari harga paling murah** 
```sql

select * from products p 
join productlines as pr on p.productLine = pr.productLine 
where pr.productLine = 'Vintage Cars'
order by p.buyPrice asc ;

```
<details><summary>result</summary>

![image](https://user-images.githubusercontent.com/56218029/236401011-ebc8187f-f326-4d16-a4fc-8b9167e31185.png)

</details>

**6.  mengambil data prodak vintage diurutkan dari harga paling mahal** 
```sql

select * from products p 
join productlines as pr on p.productLine = pr.productLine 
where pr.productLine = 'Vintage Cars'
order by p.buyPrice desc ;

```
<details><summary>result</summary>

![image](https://user-images.githubusercontent.com/56218029/236401144-d218a5a2-28c8-4afb-ad5f-3f4dd75f3ff8.png)

</details>

**7.  mengambil data customer yang transaksi di tahun 2004 dan mengurutkan berdasarkan pembelian termahal** 
```sql

select * from payments as p 
join customers as c 	
where year(p.paymentDate) = 2004 order by p.amount desc;

```
<details><summary>result</summary>

![image](https://user-images.githubusercontent.com/56218029/236401562-87db4840-2318-4b10-9180-899cba714c3a.png)

</details>

**8.  mengambil jumlah pembelian dari setiap custemer** 
```sql

select sum(p.amount) as total_payments, c.*  from customers as c 
join payments as p on c.customerNumber =p.customerNumber group by c.customerNumber ;

```
<details><summary>result</summary>

![image](https://user-images.githubusercontent.com/56218029/236403709-c5ec7af5-8fca-4b2e-8429-046563f380a0.png)

</details>

**9.  mengambil detail data pembelian dari customer dengan mama Blauer See Auto, Co.** 
```sql

select * from customers as c 
join orders as o on c.customerNumber = o.customerNumber
join orderdetails as od on o.orderNumber = od.orderNumber 
join products as p on od.productCode = p.productCode
join productlines as pl on p.productLine = pl.productLine 
where c.customerName like '%Blauer%';

```
<details><summary>result</summary>

![image](https://user-images.githubusercontent.com/56218029/236403857-cca906e7-3c05-466e-8b07-a680139b81d5.png)

</details>

**10.  mengambil data performance employe, customer mana saja yang pernah dilayani** 
```sql

select e.employeeNumber , e.firstName, e.lastName , c.* from employees as e 
join customers as c on e.employeeNumber = c.salesRepEmployeeNumber
where e.employeeNumber = 1286;

```
<details><summary>result</summary>

![image](https://user-images.githubusercontent.com/56218029/236404015-d11b4f49-99b4-4496-aecc-aa1e57a2da0d.png)

</details>

**11.  mengambil total penjualan setiap kariawan** 
```sql

select e.employeeNumber , e.firstName, e.lastName , count(*) as purchase_totals from employees as e 
join customers as c on e.employeeNumber = c.salesRepEmployeeNumber group by e.employeeNumber ;

```
<details><summary>result</summary>

![image](https://user-images.githubusercontent.com/56218029/236404425-ddea0217-c6d9-4965-9c52-b370fb19c35b.png)

</details>

