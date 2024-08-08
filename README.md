# Zomato-case-study-sql-
This is a case study on Zomato solved using SQL queries 

questions 
/*Business Questions: 
1) Help Zomato in identifying the cities with poor Restaurant ratings
2) Mr.roy is looking for a restaurant in kolkata which provides online 
delivery. Help him choose the best restaurant
3) Help Peter in finding the best rated Restraunt for Pizza in New Delhi.
4)Enlist most affordable and highly rated restaurants city wise.
5)Help Zomato in identifying the restaurants with poor offline services
6) What are the top 5 countries with most restaurants linked with Zomato?

*/



select * from zomato;
select * from countrytable;
-- question 1
select city, rating
from zomato
order by rating asc;  

-- question 2
select restaurantID, city, has_online_delivery, rating
from zomato
where has_online_delivery= "Yes" and city= "Kolkata"
order by rating desc;
-- question 3
select city, rating, cuisines
from zomato
where city= "New Delhi" and cuisines= "Pizza"
order by rating desc;

-- question 4
select city,rating,Price_range
from zomato
order by rating desc, Price_range asc;

-- question 5
select RestaurantID,Is_delivering_now
from zomato
where Is_delivering_now= "No";

-- question 6
select z.rating, c.country
from zomato z inner join countrytable c on z.countrycode=c.countrycode
order by z.rating desc
limit 5;
