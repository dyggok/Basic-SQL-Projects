# Basic-SQL-Project12

Aşağıdaki sorgu senaryoları dvdrental örnek veri tabanı üzerinden gerçekleştirilmiştir.

1. **film** tablosunda film uzunluğu **length** sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?

```sql
SELECT COUNT(length) FROM film 
WHERE length > (SELECT AVG(length) FROM film);

```

2. **film** tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?

```sql
SELECT COUNT(film) FROM film 
WHERE rental_rate = (
SELECT MAX(rental_rate) FROM film	
)
```

3. **film** tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.

```sql
SELECT * FROM film 
WHERE rental_rate = 
(
SELECT MIN(rental_rate) FROM film	
) 
AND replacement_cost =
(
SELECT MIN(replacement_cost) FROM film
)
```

4. **payment** tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.

```sql
SELECT first_name, last_name, COUNT(first_name) FROM payment
INNER JOIN customer ON customer.customer_id = payment.customer_id
GROUP BY first_name,last_name
ORDER BY COUNT(first_name) DESC;
```

