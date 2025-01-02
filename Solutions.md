# 📈Solutions for the Challenge🤔

## Day 1: 

A ski resort company want to know which customers rented ski equipment for more than one type of activity (e.g., skiing and snowboarding). List the customer names and the number of distinct activities they rented equipment for.

**Table name:** rentals

| rental_id | customer_name | activity     | rental_date |
|-----------|---------------|--------------|-------------|
| 1         | Emily         | Skiing       | 2024-01-01  |
| 2         | Michael       | Snowboarding | 2024-01-02  |
| 3         | Emily         | Snowboarding | 2024-01-03  |
| 4         | Sarah         | Skiing       | 2024-01-01  |
| 5         | Michael       | Skiing       | 2024-01-02  |
| 6         | Michael       | Snowtubing   | 2024-01-02  |

<br>

***Difficulty Level:*** Meduim

<br>

*Query*

```sql
SELECT customer_name, COUNT(DISTINCT activity) AS distinct_activity
FROM rentals
GROUP BY customer_name
HAVING COUNT(DISTINCT activity) > 1
```

| customer_name | distinct_activity |
|---------------|-------------------|
| Emily         | 2                 |
| Michael       | 3                 |

---

## Day 2:
Santa wants to know which gifts weigh more than 1 kg. Can you list them?

**Table name:** gifts

| gift_name     | recipient | weight_kg |
|---------------|-----------|-----------|
| Toy Train     | John      | 2.5       |
| Chocolate Box | Alice     | 0.8       |
| Teddy Bear    | Sophia    | 1.2       |
| Board Game    | Liam      | 0.9       |

<br>

***Difficulty Level:*** Easy

<br>

*Query*

```sql
SELECT *
FROM gifts
WHERE weight_kg > 1.0
```

| gift_name  | recipient | weight_kg |
|------------|-----------|-----------|
| Toy Train  | John      | 2.5       |
| Teddy Bear | Sophia    | 1.2       |

---


## Day 3:
You’re trying to identify the most calorie-packed candies to avoid during your holiday binge. Write a query to rank candies based on their calorie count within each category. Include the candy_name, candy_category, calories, and rank (rank_in_category) within the category.

**Table name:** candy_nutrition

| candy_id | candy_name             | calories | candy_category |
|----------|------------------------|----------|----------------|
| 1        | Candy Cane             | 200      | Sweets         |
| 2        | Chocolate Bar          | 250      | Chocolate      |
| 3        | Gingerbread Cookie     | 150      | Baked Goods    |
| 4        | Lollipop               | 100      | Sweets         |
| 5        | Dark Chocolate Truffle | 180      | Chocolate      |
| 6        | Marshmallow            | 900      | Sweets         |
| 7        | Sugar Cookie           | 140      | Baked Goods    |

<br>

***Difficulty Level:*** Hard

<br>

*Query*

```sql
SELECT candy_name, candy_category, calories,
RANK() OVER (
    PARTITION BY candy_category
    ORDER BY calories DESC
    ) as rank_in_category
FROM candy_nutrition
```

| candy_name             | candy_category | calories | rank_in_category |
|------------------------|----------------|----------|------------------|
| Gingerbread Cookie     | Baked Goods    | 150      | 1                |
| Sugar Cookie           | Baked Goods    | 140      | 2                |
| Chocolate Bar          | Chocolate      | 250      | 1                |
| Dark Chocolate Truffle | Chocolate      | 180      | 2                |
| Marshmallow            | Sweets         | 900      | 1                |
| Candy Cane             | Sweets         | 200      | 2                |
| Lollipop               | Sweets         | 100      | 3                |

---

## Day 4:
You’re planning your next ski vacation and want to find the best regions with heavy snowfall. Given the tables resorts and snowfall, find the average snowfall for each region and sort the regions in descending order of average snowfall. Return the columns region and average_snowfall.

**Table name:** ski_resorts

| resort_id | resort_name       | region          |
|-----------|-------------------|-----------------|
| 1         | Snowy Peaks       | Rocky Mountains |
| 2         | Winter Wonderland | Wasatch Range   |
| 3         | Frozen Slopes     | Alaska Range    |
| 4         | Powder Paradise   | Rocky Mountains |


**Table name:** snowfall
| resort_id | snowfall_inches |
|-----------|-----------------|
| 1         | 60              |
| 2         | 45              |
| 3         | 75              |
| 4         | 55              |

<br>

***Difficulty Level:*** Medium

<br>

*Query*

```sql
SELECT sr.region, AVG(sf.snowfall_inches) as average_snowfall
FROM
ski_resorts sr
JOIN snowfall sf
ON sr.resort_id = sf.resort_id
GROUP BY sr.region
ORDER BY AVG(sf.snowfall_inches) DESC
```

| region          | average_snowfall |
|-----------------|------------------|
| Alaska Range    | 75               |
| Rocky Mountains | 57.5             |
| Wasatch Range   | 45               |

---

## Day 5:
This year, we're celebrating Christmas in the Southern Hemisphere! Which beaches are expected to have temperatures above 30°C on Christmas Day?

**Table name:** beach_temperature_predictions

| beach_name       | country      | expected_temperature_c | date       |
|------------------|--------------|------------------------|------------|
| Bondi Beach      | Australia    | 32                     | 2024-12-24 |
| Copacabana Beach | Brazil       | 28                     | 2024-12-24 |
| Clifton Beach    | South Africa | 31                     | 2024-12-25 |
| Brighton Beach   | New Zealand  | 25                     | 2024-12-25 |

<br>

***Difficulty Level:*** Easy

<br>

*Query*

```sql
SELECT beach_name
FROM beach_temperature_predictions
WHERE expected_temperature_c > 30 and date = '2024-12-25'
```

| beach_name    |
|---------------|
| Clifton Beach |

---

## Day 6:
Scientists are tracking polar bears across the Arctic to monitor their migration patterns and caloric intake. Write a query to find the top 3 polar bears that have traveled the longest total distance in December 2024. Include their bear_id, bear_name, and total_distance_traveled in the results.

**Table name:** polar_bears

| bear_id | bear_name | age |
|---------|-----------|-----|
| 1       | Snowball  | 10  |
| 2       | Frosty    | 7   |
| 3       | Iceberg   | 15  |
| 4       | Chilly    | 5   |


**Table name:** tracking

| tracking_id | bear_id | distance_km | date       |
|-------------|---------|-------------|------------|
| 1           | 1       | 25          | 2024-12-01 |
| 2           | 2       | 40          | 2024-12-02 |
| 3           | 1       | 30          | 2024-12-03 |
| 4           | 3       | 50          | 2024-12-04 |
| 5           | 2       | 35          | 2024-12-05 |
| 6           | 4       | 20          | 2024-12-06 |
| 7           | 3       | 55          | 2024-12-07 |
| 8           | 1       | 45          | 2024-12-08 |

<br>

***Difficulty Level:*** Hard

<br>

*Query*

```sql
SELECT pb.bear_id, pb.bear_name, SUM(t.distance_km) as total_distance_traveled
FROM polar_bears pb
JOIN tracking t ON pb.bear_id = t.bear_id
WHERE t.date BETWEEN '2024-12-01' AND '2024-12-31'
GROUP BY pb.bear_id
HAVING SUM(distance_km) > 0
ORDER BY 3 DESC
LIMIT 3
```

| bear_id | bear_name | total_distance_traveled |
|---------|-----------|-------------------------|
| 3       | Iceberg   | 105                     |
| 1       | Snowball  | 100                     |
| 2       | Frosty    | 75                      |

---

## Day 7:
The owner of a winter market wants to know which vendors have generated the highest revenue overall. For each vendor, calculate the total revenue for all their items and return a list of the top 2 vendors by total revenue. Include the vendor_name and total_revenue in your results.

**Table name:** vendors

| vendor_id | vendor_name    | market_location |
|-----------|----------------|-----------------|
| 1         | Cozy Crafts    | Downtown Square |
| 2         | Sweet Treats   | Central Park    |
| 3         | Winter Warmers | Downtown Square |


**Table name:** sales

| sale_id | vendor_id | item_name          | quantity_sold | price_per_unit |
|---------|-----------|--------------------|---------------|----------------|
| 1       | 1         | Knitted Scarf      | 15            | 25             |
| 2       | 2         | Hot Chocolate      | 50            | 3.5            |
| 3       | 3         | Wool Hat           | 20            | 18             |
| 4       | 1         | Handmade Ornament  | 10            | 15             |
| 5       | 2         | Gingerbread Cookie | 30            | 5              |

<br>

***Difficulty Level:*** Medium

<br>

*Query*

```sql
SELECT v.vendor_name, 
       SUM(s.quantity_sold * s.price_per_unit) AS total_revenue 
FROM vendors v
JOIN sales s 
ON v.vendor_id = s.vendor_id
GROUP BY v.vendor_id
ORDER BY 2 DESC
LIMIT 2
```

| vendor_name    | total_revenue |
|----------------|---------------|
| Cozy Crafts    | 525           |
| Winter Warmers | 360           |

---

## Day 8:
You are managing inventory in Santa's workshop. Which gifts are meant for "good" recipients? List the gift name and its weight.

**Table name:** gifts

| gift_id | gift_name     | recipient_type | weight_kg |
|---------|---------------|----------------|-----------|
| 1       | Toy Train     | good           | 2.5       |
| 2       | Lumps of Coal | naughty        | 1.5       |
| 3       | Teddy Bear    | good           | 1.2       |
| 4       | Chocolate Bar | good           | 0.3       |
| 5       | Board Game    | naughty        | 1.8       |

<br>

***Difficulty Level:*** Easy

<br>

*Query*

```sql
SELECT gift_name, weight_kg
FROM gifts
where recipient_type = 'good'
```

| gift_name     | weight_kg |
|---------------|-----------|
| Toy Train     | 2.5       |
| Teddy Bear    | 1.2       |
| Chocolate Bar | 0.3       |

---

## Day 9:
A community is hosting a series of festive feasts, and they want to ensure a balanced menu. Write a query to identify the top 3 most calorie-dense dishes (calories per gram) served for each event. Include the dish_name, event_name, and the calculated calorie density in your results.

**Table name:** events

| event_id | event_name              |
|----------|-------------------------|
| 1        | Christmas Eve Dinner    |
| 2        | New Years Feast         |
| 3        | Winter Solstice Potluck |

<br>

**Table name:** menu

| dish_id | dish_name          | event_id | calories | weight_g |
|---------|--------------------|----------|----------|----------|
| 1       | Roast Turkey       | 1        | 3500     | 5000     |
| 2       | Chocolate Yule Log | 1        | 2200     | 1000     |
| 3       | Cheese Fondue      | 2        | 1500     | 800      |
| 4       | Holiday Fruitcake  | 3        | 4000     | 1200     |
| 5       | Honey Glazed Ham   | 2        | 2800     | 3500     |

<br>

***Difficulty Level:*** Hard

<br>

*Query*

```sql
WITH cal as
(
       SELECT m.dish_name, e.event_name, 
              (m.calories/weight_g) as calculated_calories,
       RANK() OVER(
              PARTITION BY e.event_id
              ORDER BY (m.calories/weight_g) DESC
              ) AS rank
       FROM events e
       JOIN menu m ON e.event_id = m.event_id
)
SELECT dish_name, event_name, calculated_calories
FROM cal
WHERE rank <= 3
ORDER BY calculated_calories
```

| dish_name          | event_name              | calculated_calories |
|--------------------|-------------------------|---------------------|
| Roast Turkey       | Christmas Eve Dinner    | 0                   |
| Honey Glazed Ham   | New Years Feast         | 0                   |
| Cheese Fondue      | New Years Feast         | 1                   |
| Chocolate Yule Log | Christmas Eve Dinner    | 2                   |
| Holiday Fruitcake  | Winter Solstice Potluck | 3                   |

---

## Day 10:
You are tracking your friends' New Year’s resolution progress. Write a query to calculate the following for each friend: number of resolutions they made, number of resolutions they completed, and success percentage (% of resolutions completed) and a success category based on the success percentage:
- Green: If success percentage is greater than 75%.
- Yellow: If success percentage is between 50% and 75% (inclusive).
- Red: If success percentage is less than 50%.

**Table name:** resolutions

| resolution_id | friend_name | resolution        | is_completed |
|---------------|-------------|-------------------|--------------|
| 1             | Alice       | Exercise daily    | 1            |
| 2             | Alice       | Read 20 books     | 0            |
| 3             | Bob         | Save money        | 0            |
| 4             | Bob         | Eat healthier     | 1            |
| 5             | Charlie     | Travel more       | 1            |
| 6             | Charlie     | Learn a new skill | 1            |
| 7             | Diana       | Volunteer monthly | 1            |
| 8             | Diana       | Drink more water  | 0            |
| 9             | Diana       | Sleep 8 hours     | 1            |

<br>

***Difficulty Level:*** Medium

<br>

*Query*

```sql
SELECT 
    friend_name,
    COUNT(*) AS total_resolutions,
    SUM(is_completed) AS completed_resolutions,
    ROUND(SUM(is_completed) * 100 / COUNT(*),2) AS success_percentage,
CASE
    WHEN SUM(is_completed) * 100 / COUNT(*) > 75 THEN 'GREEN'
    WHEN SUM(is_completed) * 100 / COUNT(*) BETWEEN 50 AND 75 THEN 'Yellow'
    ELSE 'RED'
    END AS success_category
FROM resolutions
GROUP BY 1
ORDER BY 4 DESC
```
<details>
<summary>
Using CTE
</summary>

```sql
WITH res_sum AS(
    SELECT
        friend_name,
        COUNT(*) AS total_resolutions,
        SUM(is_completed) AS completed_resolutions,
        ROUND(SUM(is_completed) * 100 / COUNT(*),2) AS success_percentage
    FROM resolutions
    GROUP BY friend_name
)
SELECT
    friend_name,
    total_resolutions,
    completed_resolutions,
    success_percentage,
CASE
    WHEN success_percentage > 75 THEN 'Green'
    WHEN success_percentage BETWEEN 50 AND 75 THEN 'Yellow'
    ELSE 'Red'
END AS success_category
FROM res_sum
ORDER BY success_percentage DESC
```
</details>

<br>


| friend_name | total_resolutions | completed_resolutions | success_percentage | success_category |
|-------------|-------------------|-----------------------|--------------------|------------------|
| Charlie     | 2                 | 2                     | 100                | GREEN            |
| Diana       | 3                 | 2                     | 66                 | Yellow           |
| Bob         | 2                 | 1                     | 50                 | Yellow           |
| Alice       | 2                 | 1                     | 50                 | Yellow           |

---


## Day 11:
You are preparing holiday gifts for your family. Who in the family_members table are celebrating their birthdays in December 2024? List their name and birthday.

**Table name:** family_members

| member_id | name    | relationship | birthday   |
|-----------|---------|--------------|------------|
| 1         | Dawn    | Sister       | 2024-12-24 |
| 2         | Bob     | Father       | 2024-05-20 |
| 3         | Charlie | Brother      | 2024-12-25 |
| 4         | Diana   | Mother       | 2024-03-15 |

<br>

***Difficulty Level:*** Easy

<br>

*Query*

```sql
SELECT name, birthday
FROM family_members
WHERE birthday like '2024-12-%'
```

| name    | birthday   |
|---------|------------|
| Dawn    | 2024-12-24 |
| Charlie | 2024-12-25 |
---

## Day 12:
A collector wants to identify the top 3 snow globes with the highest number of figurines. Write a query to rank them and include their globe_name, number of figurines, and material.

**Table name:** snow_globes

| globe_id | globe_name        | volume_cm3 | material |
|----------|-------------------|------------|----------|
| 1        | Winter Wonderland | 500        | Glass    |
| 2        | Santas Workshop   | 300        | Plastic  |
| 3        | Frozen Forest     | 400        | Glass    |
| 4        | Holiday Village   | 600        | Glass    |

<br>

**Table name:** figurines

| figurine_id | globe_id | figurine_type |
|-------------|----------|---------------|
| 1           | 1        | Snowman       |
| 2           | 1        | Tree          |
| 3           | 2        | Santa Claus   |
| 4           | 2        | Elf           |
| 5           | 2        | Gift Box      |
| 6           | 3        | Reindeer      |
| 7           | 3        | Tree          |
| 8           | 4        | Snowman       |
| 9           | 4        | Santa Claus   |
| 10          | 4        | Tree          |
| 11          | 4        | Elf           |
| 12          | 4        | Gift Box      |

<br>

***Difficulty Level:*** Hard

<br>

*Query*

```sql
SELECT
    s.globe_name, 
    COUNT(f.figurine_type) AS figurine_count, 
    s.material
FROM snow_globes s
JOIN figurines f ON s.globe_id = f.globe_id
GROUP BY s.globe_name
ORDER BY figurine_count DESC
LIMIT 3
```

| globe_name        | figurine_count | material |
|-------------------|----------------|----------|
| Holiday Village   | 5              | Glass    |
| Santas Workshop   | 3              | Plastic  |
| Winter Wonderland | 2              | Glass    |

---

## Day 13:
We need to make sure Santa's sleigh is properly balanced. Find the total weight of gifts for each recipient.

**Table name:** gifts

| gift_id | gift_name     | recipient | weight_kg |
|---------|---------------|-----------|-----------|
| 1       | Toy Train     | John      | 2.5       |
| 2       | Chocolate Box | Alice     | 0.8       |
| 3       | Teddy Bear    | Sophia    | 1.2       |
| 4       | Board Game    | John      | 0.9       |

<br>

***Difficulty Level:*** Medium

<br>

*Query*

```sql
SELECT
    recipient,
    SUM(weight_kg) AS total_weight
FROM gifts
GROUP BY 1
ORDER BY 2
```

| recipient | total_weight |
|-----------|--------------|
| Alice     | 0.8          |
| Sophia    | 1.2          |
| John      | 3.4          |

---

## Day 14:
Which ski resorts had snowfall greater than 50 inches?

**Table name:** snowfall

| resort_name       | location | snowfall_inches |
|-------------------|----------|-----------------|
| Snowy Peaks       | Colorado | 60              |
| Winter Wonderland | Utah     | 45              |
| Frozen Slopes     | Alaska   | 75              |

<br>

***Difficulty Level:*** Easy

<br>

*Query*

```sql
SELECT
    resort_name,
    location
FROM snowfall
WHERE snowfall_inches > 50
```

| resort_name   | location |
|---------------|----------|
| Snowy Peaks   | Colorado |
| Frozen Slopes | Alaska   |

---

## Day 15:
A family reunion is being planned, and the organizer wants to identify the three family members with the most children. Write a query to calculate the total number of children for each parent and rank them. Include the parent’s name and their total number of children in the result.

**Table name:** family_members

| member_id | name    | age |
|-----------|---------|-----|
| 1         | Alice   | 30  |
| 2         | Bob     | 58  |
| 3         | Charlie | 33  |
| 4         | Diana   | 55  |
| 5         | Eve     | 5   |
| 6         | Frank   | 60  |
| 7         | Grace   | 32  |
| 8         | Hannah  | 8   |
| 9         | Ian     | 12  |
| 10        | Jack    | 3   |

<br>

**Table name:** parent_child_relationships

| parent_id | child_id |
|-----------|----------|
| 2         | 1        |
| 3         | 5        |
| 4         | 1        |
| 6         | 7        |
| 6         | 8        |
| 7         | 9        |
| 7         | 10       |
| 4         | 8        |

<br>

***Difficulty Level:*** Hard

<br>

*Query*

```sql
SELECT
    fm.name parent_name,
    COUNT(pcr.child_id) total_children,
    RANK() OVER(ORDER BY COUNT(pcr.child_id) DESC) AS rank
FROM family_members fm
JOIN parent_child_relationships pcr ON fm.member_id = pcr.parent_id
GROUP BY fm.name
ORDER BY rank
LIMIT 3
```

| parent_name | total_children | rank |
|-------------|----------------|------|
| Grace       | 2              | 1    |
| Frank       | 2              | 1    |
| Diana       | 2              | 1    |

---

## Day 16:
As the owner of a candy store, you want to understand which of your products are selling best. Write a query to calculate the total revenue generated from each candy category.

**Table name:** candy_sales

| sale_id | candy_name             | quantity_sold | price_per_unit | category  |
|---------|------------------------|---------------|----------------|-----------|
| 1       | Candy Cane             | 20            | 1.5            | Sweets    |
| 2       | Chocolate Bar          | 10            | 2              | Chocolate |
| 3       | Lollipop               | 5             | 0.75           | Sweets    |
| 4       | Dark Chocolate Truffle | 8             | 2.5            | Chocolate |
| 5       | Gummy Bears            | 15            | 1.2            | Sweets    |
| 6       | Chocolate Fudge        | 12            | 3              | Chocolate |

<br>

***Difficulty Level:*** Medium

<br>

*Query*

```sql
SELECT
    category,
    SUM(quantity_sold*price_per_unit) AS total_revenue
FROM candy_sales
GROUP BY category
ORDER BY total_revenue DESC
```

| category  | total_revenue |
|-----------|---------------|
| Chocolate | 76            |
| Sweets    | 51.75         |

---

## Day 17:
The Grinch is planning out his pranks for this holiday season. Which pranks have a difficulty level of “Advanced” or “Expert"? List the prank name and location (both in descending order).

**Table name:** grinch_pranks

| prank_id | prank_name            | location             | difficulty |
|----------|-----------------------|----------------------|------------|
| 1        | Stealing Stockings    | Whoville             | Beginner   |
| 2        | Christmas Tree Topple | Whoville Town Square | Advanced   |
| 3        | Present Swap          | Cindy Lous House     | Beginner   |
| 4        | Sleigh Sabotage       | Mount Crumpit        | Expert     |
| 5        | Chimney Block         | Mayors Mansion       | Expert     |

<br>

***Difficulty Level:*** Easy

<br>

*Query*

```sql
SELECT prank_name, location
FROM grinch_pranks
WHERE difficulty = 'Advanced' OR difficulty = 'Expert'
ORDER BY location DESC, prank_name DESC
```

| prank_name            | location             |
|-----------------------|----------------------|
| Christmas Tree Topple | Whoville Town Square |
| Sleigh Sabotage       | Mount Crumpit        |
| Chimney Block         | Mayors Mansion       |

---

## Day 18:
A travel agency is promoting activities for a "Summer Christmas" party. They want to identify the top 2 activities based on the average rating. Write a query to rank the activities by average rating.

**Table name:** activities

| activity_id | activity_name   |
|-------------|-----------------|
| 1           | Surfing Lessons |
| 2           | Jet Skiing      |
| 3           | Sunset Yoga     |

<br>

**Table name:** activity_ratings

| rating_id | activity_id | rating |
|-----------|-------------|--------|
| 1         | 1           | 4.7    |
| 2         | 1           | 4.8    |
| 3         | 1           | 4.9    |
| 4         | 2           | 4.6    |
| 5         | 2           | 4.7    |
| 6         | 2           | 4.8    |
| 7         | 2           | 4.9    |
| 8         | 3           | 4.8    |
| 9         | 3           | 4.7    |
| 10        | 3           | 4.9    |
| 11        | 3           | 4.8    |
| 12        | 3           | 4.9    |

<br>

***Difficulty Level:*** Hard

<br>

*Query*

```sql
SELECT 
    a.activity_name,
    AVG(r.rating) AS average_rating
FROM activities a
JOIN  activity_ratings r ON a.activity_id = r.activity_id
GROUP BY activity_name
ORDER BY average_rating DESC
LIMIT 2
```

| activity_name   | average_rating |
|-----------------|----------------|
| Sunset Yoga     | 4.82           |
| Surfing Lessons | 4.8            |

---


## Day 19:
Scientists are studying the diets of polar bears. Write a query to find the maximum amount of food (in kilograms) consumed by each polar bear in a single meal December 2024. Include the bear_name and biggest_meal_kg, and sort the results in descending order of largest meal consumed.

**Table name:** polar_bears

| bear_id | bear_name | age |
|---------|-----------|-----|
| 1       | Snowball  | 10  |
| 2       | Frosty    | 7   |
| 3       | Iceberg   | 15  |

<br>

**Table name:** meal_log

| log_id | bear_id | food_type | food_weight_kg | date       |
|--------|---------|-----------|----------------|------------|
| 1      | 1       | Seal      | 30             | 2024-12-01 |
| 2      | 2       | Fish      | 15             | 2024-12-02 |
| 3      | 1       | Fish      | 10             | 2024-12-03 |
| 4      | 3       | Seal      | 25             | 2024-12-04 |
| 5      | 2       | Seal      | 20             | 2024-12-05 |
| 6      | 3       | Fish      | 18             | 2024-12-06 |

<br>

***Difficulty Level:*** Medium

<br>

*Query*

```sql
SELECT 
    p.bear_name,
    MAX(m.food_weight_kg) AS biggest_meal_kg
FROM polar_bears p
JOIN meal_log m ON p.bear_id = m.bear_id
WHERE m.date BETWEEN '2024-12-01' AND '2024-12-31'
GROUP BY 1
ORDER BY 2 DESC
```

| bear_name | biggest_meal_kg |
|-----------|-----------------|
| Snowball  | 30              |
| Iceberg   | 25              |
| Frosty    | 20              |

---

## Day 20:
We are looking for cheap gifts at the market. Which vendors are selling items priced below $10? List the unique (i.e. remove duplicates) vendor names.


**Table name:** vendors

| vendor_id | vendor_name    | market_location |
|-----------|----------------|-----------------|
| 1         | Cozy Crafts    | Downtown Square |
| 2         | Sweet Treats   | Central Park    |
| 3         | Winter Warmers | Downtown Square |

<br>

**Table name:** item_prices

| item_id | vendor_id | item_name          | price_usd |
|---------|-----------|--------------------|-----------|
| 1       | 1         | Knitted Scarf      | 25        |
| 2       | 2         | Hot Chocolate      | 5         |
| 3       | 2         | Gingerbread Cookie | 3.5       |
| 4       | 3         | Wool Hat           | 18        |
| 5       | 3         | Santa Pin          | 2         |

<br>

***Difficulty Level:*** Easy

<br>

*Query*

```sql
SELECT DISTINCT(v.vendor_name)
FROM vendors v
JOIN item_prices i ON v.vendor_id = i.vendor_id
WHERE i.price_usd < 10
```

| vendor_name    |
|----------------|
| Sweet Treats   |
| Winter Warmers |

---

## Day 21:
Santa needs to optimize his sleigh for Christmas deliveries. Write a query to calculate the total weight of gifts for each recipient type (good or naughty) and determine what percentage of the total weight is allocated to each type. Include the recipient_type, total_weight, and weight_percentage in the result.

**Table name:** gifts

| gift_id | gift_name     | recipient_type | weight_kg |
|---------|---------------|----------------|-----------|
| 1       | Toy Train     | good           | 2.5       |
| 2       | Lumps of Coal | naughty        | 1.5       |
| 3       | Teddy Bear    | good           | 1.2       |
| 4       | Chocolate Bar | good           | 0.3       |
| 5       | Board Game    | naughty        | 1.8       |

<br>

***Difficulty Level:*** Hard

<br>

*Query*

```sql
SELECT
    recipient_type,
    SUM(weight_kg) AS total_weight,
    SUM(weight_kg)*100 / SUM(weight_kg) OVER() AS weight_percentage 
FROM gifts
GROUP BY recipient_type
```

<details>
<summary>
Using CTE
</summary>

```sql
WITH overall_total_weight AS(
    SELECT
        SUM(weight_kg) as tw
    FROM gifts
)

SELECT
    recipient_type,
    SUM(weight_kg) AS total_weight,
    ROUND(SUM(weight_kg)*100 / tw,2) AS weight_percentage 
FROM gifts, overall_total_weight
GROUP BY recipient_type

```
</details>

<details>
<summary>
Using Subquery
</summary>

```sql
SELECT
    recipient_type,
    SUM(weight_kg) AS total_weight,
    ROUND(
        SUM(weight_kg)*100 / (SELECT SUM(weight_kg) FROM gifts),2
        ) AS weight_percentage 
FROM gifts
GROUP BY recipient_type
```
</details>

| recipient_type | total_weight | weight_percentage |
|----------------|--------------|-------------------|
| good           | 4            | 100               |
| naughty        | 3.3          | 82.5              |

---

## Day 22:
We are hosting a gift party and need to ensure every guest receives a gift. Using the guests and guest_gifts tables, write a query to identify the guest(s) who have not been assigned a gift (i.e. they are not listed in the guest_gifts table).

**Table name:** guests

| guest_id | guest_name    |
|----------|---------------|
| 1        | Cindy Lou     |
| 2        | The Grinch    |
| 3        | Max the Dog   |
| 4        | Mayor May Who |

<br>

**Table name:** guest_gifts

| gift_id | guest_id | gift_name   |
|---------|----------|-------------|
| 1       | 1        | Toy Train   |
| 2       | 1        | Plush Bear  |
| 3       | 2        | Bag of Coal |
| 4       | 2        | Sleigh Bell |
| 5       | 3        | Dog Treats  |

<br>

***Difficulty Level:*** Medium

<br>

*Query*

```sql
SELECT g.guest_name
FROM guests g
LEFT JOIN guest_gifts gg ON g.guest_id = gg.guest_id
WHERE gg.guest_id IS NULL
```

| guest_name    |
|---------------|
| Mayor May Who |

---

## Day 23:
The Grinch tracked his weight every day in December to analyze how it changed daily. Write a query to return the weight change (in pounds) for each day, calculated as the difference from the previous day's weight.

**Table name:** grinch_weight_log

| log_id | day_of_month | weight |
|--------|--------------|--------|
| 1      | 1            | 250    |
| 2      | 2            | 248    |
| 3      | 3            | 249    |
| 4      | 4            | 247    |
| 5      | 5            | 246    |
| 6      | 6            | 248    |

<br>

***Difficulty Level:*** Medium

<br>

*Query*

```sql
SELECT
    day_of_month,
    weight AS current_weight,
    weight - LAG(weight) OVER(ORDER BY day_of_month) weight_change
FROM grinch_weight_log
```

<details>
<summary>
Using CTE
</summary>

```sql
WITH wt AS 
(
    SELECT
        day_of_month,
        weight AS current_weight,
        LAG(weight) OVER(ORDER BY day_of_month) prev_weight
    FROM grinch_weight_log
)
SELECT *,
    current_weight - prev_weight AS weight_change
FROM wt
```

| day_of_month | current_weight | weight_change |
|--------------|----------------|---------------|
| 1            | 250            |               |
| 2            | 248            | -2            |
| 3            | 249            | 1             |
| 4            | 247            | -2            |
| 5            | 246            | -1            |
| 6            | 248            | 2             |

---

## Day 24:
Santa is tracking how many presents he delivers each night leading up to Christmas. He wants a running total to see how many gifts have been delivered so far on any given night. Using the deliveries table, calculate the cumulative sum of gifts delivered, ordered by the delivery date.

**Table name:** deliveries

| delivery_date | gifts_delivered |
|---------------|-----------------|
| 2024-12-20    | 120             |
| 2024-12-21    | 150             |
| 2024-12-22    | 200             |
| 2024-12-23    | 300             |
| 2024-12-24    | 500             |

<br>

***Difficulty Level:*** Hard

<br>

*Query*

```sql
SELECT
    delivery_date,
    gifts_delivered,
    SUM(gifts_delivered) OVER(ORDER BY delivery_date) as cumulative_sum
FROM deliveries
```
</details>

| delivery_date | gifts_delivered | cumulative_sum |
|---------------|-----------------|----------------|
| 2024-12-20    | 120             | 120            |
| 2024-12-21    | 150             | 270            |
| 2024-12-22    | 200             | 470            |
| 2024-12-23    | 300             | 770            |
| 2024-12-24    | 500             | 1270           |

---
