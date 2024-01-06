--List all customers who live in Texas (use
JOINs)
SELECT customer.customer_id, customer.first_name, customer.last_name
FROM customer
JOIN address ON customer.address_id = address.address_id
WHERE address.district = 'Texas';
--Get all payments above $6.99 with the Customer's Full
Name
SELECT customer.first_name || ' ' || customer.last_name AS customer_name,
       payment.payment_id,
       payment.amount
FROM payment
JOIN customer ON payment.customer_id = customer.customer_id
WHERE payment.amount > 6.99;
--Show all customers names who have made payments over $175(use subqueries)
SELECT first_name || ' ' || last_name AS customer_name
FROM customer
WHERE customer_id IN (
    SELECT DISTINCT payment.customer_id
    FROM payment
    WHERE amount > 175
);
-- List all customers that live in Nepal (use the city
table)
SELECT customer.customer_id, customer.first_name, customer.last_name
FROM customer
JOIN address ON customer.address_id = address.address_id
JOIN city ON address.city_id = city.city_id
WHERE city.country_id = (
    SELECT country_id
    FROM country
    WHERE country = 'Nepal'
);
--Which staff member had the most
transactions?
SELECT staff.staff_id, staff.first_name, staff.last_name, COUNT(payment.payment_id) AS TransactionCount
FROM staff
JOIN payment ON staff.staff_id = payment.staff_id
GROUP BY staff.staff_id, staff.first_name, staff.last_name
ORDER BY TransactionCount DESC
LIMIT 1;
--How many movies of each rating are there?
SELECT rating, COUNT(*) AS NumberOfMovies
FROM film
GROUP BY rating;
--Show all customers who have made a single payment above $6.99 (Use Subqueries)
SELECT customer.customer_id, customer.first_name, customer.last_name
FROM customer
WHERE customer.customer_id IN (
    SELECT payment.customer_id
    FROM payment
    GROUP BY payment.customer_id
    HAVING COUNT(payment.payment_id) = 1 AND MAX(payment.amount) > 6.99
);
-- How many free rentals did our store give away?

SELECT COUNT(*) AS NumberOfFreeRentals
FROM payment  
WHERE amount = 0;

