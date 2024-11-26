# **Mastering Advanced SQL Topics** 🚀  
Welcome back, SQL Champion! 🧙‍♂️ Are you ready to level up your database skills and tackle **Advanced SQL Topics**? Let’s explore *Subqueries*, *Window Functions*, *Functions & Procedures*, *Triggers*, *Indexing*, and *Views* with some fun examples! 🎉  

---

## 1. **Subqueries**: SQL's Secret Agent 🕵️‍♀️  
Subqueries are like having a query within a query—a little spy that gathers info for the main query!  

### Example: Find Top Scorers in a League 🎮  
You have a **Players** table with their scores. Let’s find players who scored above the average!  

### **Step 1**: Create the Players Table  
```sql  
CREATE TABLE players (  
    player_id INT PRIMARY KEY,  
    player_name VARCHAR(50),  
    score INT  
);  

INSERT INTO players (player_id, player_name, score) VALUES  
(1, 'Marouane', 85),  
(2, 'Jamie', 90),  
(3, 'Taylor', 60),  
(4, 'Said', 70);  
```  

### **Step 2**: Use a Subquery to Find Top Scorers  
```sql  
SELECT player_name, score  
FROM players  
WHERE score > (SELECT AVG(score) FROM players);  
```  

**Result:**  
| player_name | score |  
|-------------|-------|  
| Marouane    | 85    |  
| Jamie       | 90    |  

**Explanation:** The subquery (`SELECT AVG(score) FROM players`) calculates the average score, and the main query retrieves players who scored above it. 🏅  

---

## 2. **Window Functions**: SQL's Crystal Ball 🔮  
Window functions let you perform calculations across rows without grouping them. It’s like giving each row a little extra context!  

### Example: Rank Players by Their Scores 🥇  
```sql  
SELECT player_name, score,  
       RANK() OVER (ORDER BY score DESC) AS rank  
FROM players;  
```  

**Result:**  
| player_name | score | rank |  
|-------------|-------|------|  
| Jamie       | 90    | 1    |  
| Marouane    | 85    | 2    |  
| Said        | 70    | 3    |  
| Taylor      | 60    | 4    |  

**Explanation:** The `RANK()` function assigns a rank based on the `ORDER BY` clause. Perfect for leaderboards! 🏆  

---

## 3. **Functions and Procedures**: SQL Automation Magic ✨  
Functions and procedures let you automate repetitive tasks. Think of them as SQL’s reusable spells!  

### Example: Create a Function to Convert Scores to Grades 🧙‍♂️  
```sql  
CREATE FUNCTION get_grade(score INT) RETURNS VARCHAR(2)  
BEGIN  
    RETURN CASE  
        WHEN score >= 90 THEN 'A'  
        WHEN score >= 80 THEN 'B'  
        WHEN score >= 70 THEN 'C'  
        ELSE 'D'  
    END;  
END;  

SELECT player_name, score, get_grade(score) AS grade  
FROM players;  
```  

**Result:**  
| player_name | score | grade |  
|-------------|-------|-------|  
| Jamie       | 90    | A     |  
| Marouane    | 85    | B     |  
| Said        | 70    | C     |  
| Taylor      | 60    | D     |  

---

## 4. **Triggers**: Automate Reactions in Your Database 🛎️  
Triggers are like setting up a trap—SQL reacts automatically when something happens!  

### Example: Log Every Score Update 🔍  
```sql  
CREATE TABLE score_logs (  
    log_id INT AUTO_INCREMENT PRIMARY KEY,  
    player_id INT,  
    old_score INT,  
    new_score INT,  
    log_time TIMESTAMP DEFAULT CURRENT_TIMESTAMP  
);  

CREATE TRIGGER log_score_update  
AFTER UPDATE ON players  
FOR EACH ROW  
BEGIN  
    INSERT INTO score_logs (player_id, old_score, new_score)  
    VALUES (OLD.player_id, OLD.score, NEW.score);  
END;  

-- Update a score to see the trigger in action!  
UPDATE players SET score = 95 WHERE player_id = 2;  
```  

**Result in `score_logs`:**  
| log_id | player_id | old_score | new_score | log_time             |  
|--------|-----------|-----------|-----------|----------------------|  
| 1      | 2         | 90        | 95        | 2024-11-26 12:00:00 |  

---

## 5. **Indexing for Performance**: SQL Speed Boost 🏎️  
Indexing is like creating a fast lane for your queries. It helps retrieve data quickly!  

### Example: Add an Index to Speed Up Queries on `score`  
```sql  
CREATE INDEX idx_score ON players(score);  
```  

**Explanation:** Now, queries that filter or sort by `score` will run much faster. ⚡  

---

## 6. **Views**: Simplify Complex Queries 🪞  
Views are like virtual tables—they simplify complex queries and make them reusable!  

### Example: Create a View for Top Players  
```sql  
CREATE VIEW top_players AS  
SELECT player_name, score  
FROM players  
WHERE score > 80;  

-- Use the view  
SELECT * FROM top_players;  
```  

**Result:**  
| player_name | score |  
|-------------|-------|  
| Jamie       | 95    |  
| Marouane    | 85    |  

---

## 🎉 Conclusion  
Advanced SQL can feel like wizardry, but with practice, you'll master these spells and use them to build faster, smarter, and more interactive databases! 🧙‍♀️  

### Your Mission 🧑‍💻  
Try these queries, tweak the data, and observe how SQL handles these advanced tasks. SQL is a superpower—keep practicing to wield it like a pro! 💪  

Remember: The database is your playground. Go forth and create magic! ✨  
