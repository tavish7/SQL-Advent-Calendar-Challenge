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
<details>
<summary>
Query
</summary>

```sql
SELECT customer_name, COUNT(DISTINCT activity) AS distinct_activity
FROM rentals
GROUP BY customer_name
HAVING COUNT(DISTINCT activity) > 1
```
 </details>

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

## Day 4:
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
