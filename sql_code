-- Creating database 

create database cereal;
use cereal;

-- The average content of each nutrient and element per manufacturer

select
	case
		when mfr = 'A' then 'American Home Food Products'
        when mfr = 'G' then 'General Mills'
        when mfr = 'K' then 'Kelloggs'
        when mfr = 'N' then 'Nabisco'
        when mfr = 'P' then 'Post'
        when mfr = 'Q' then 'Quaker Oats'
        when mfr = 'R' then 'Ralston Purina'
	end as 'Manufacter',
    count(*) as 'Quantinty of breakfast cereal brands',
	avg(calories) as 'Average calories per serving', 
	avg(protein) as 'Average grams of protein', 
    avg(fat) as 'Average grams of fat', 
    avg(sodium) as 'Average milligrams of sodium', 
    avg(fiber) as 'Average grams of dietary fiber', 
    avg(carbo) as 'Average grams of complex carbohydrates', 
    avg(sugars) as 'Average grams of sugars',
	avg(potass) as 'Average milligrams of potassium',
    round(avg(rating), 2) as 'Average rating of the cereals'
from cereal
group by mfr
order by mfr;
    
--  Top 10 breakfast cereal with the highest protein to calorie ratio
    
select
  name as 'Cereal name',
  protein,
  calories,
  protein / calories as 'Protein-to-Calories Ratio'
from cereal
order by protein / calories desc
limit 10;

-- Breakfast cereal with higher calorie and sugar content than average

select
	name as 'Cereal name',
    calories,
    sugars
from cereal 
where calories > (select avg(calories) from cereal)
	and sugars > (select avg(sugars) from cereal)
order by name;

-- The breakfast cereal with the lowest protein to carbohydrate ratio and the highest fiber to calorie ratio

select
  name as 'Cereal Name',
  protein,
  carbo,
  fiber,
  calories
from cereal
order by (protein/carbo) asc, (fiber/calories) desc
limit 3;

-- The breakfast cereal with the highest level of sodium on shelf number 3

select
  name as 'Cereal Name',
  sodium,
  shelf
from cereal
where shelf = 3
order by sodium desc
limit 1;

-- The breakfast cereal that has the fewest calories per serving and the highest rating

select
  name as 'Cereal Name',
  calories,
  rating
from cereal
order by calories asc, rating desc
limit 1;

-- Top-rated cereals by shelf

select 
	Name,
    Shelf,
    Rating
from cereal
where (Shelf, Rating) in (
    select Shelf, MAX(Rating)
    from cereal
    group by Shelf
);













