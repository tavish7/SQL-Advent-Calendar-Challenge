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

## Day 6:
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

## Day 7:
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

## Day 8:
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

## Day 9:
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

## Day 10:
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

## Day 11:
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

## Day 12:
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

## Day 13:
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

## Day 14:
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

## Day 15:
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

## Day 16:
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

## Day 17:
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

## Day 18:
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


## Day 19:
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

## Day 20:
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

## Day 21:
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

## Day 22:
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

## Day 23:
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

## Day 24:
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
