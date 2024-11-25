### SQL Joins – Let’s Connect! 🔗  
Sometimes, you need to connect tables to get the full picture (kind of like finding out how your café employees' tips 🍽️ compare to their salaries 💸 knowing that the tip is stored in another table). SQL JOINs are here for that!


Imagine you're managing a **Gaming League** 🎮🏆. You have a table for **Players** and another for the **Games** they’ve joined. Your task is to figure out how they’re connected and answer questions like, *"Which players joined which games?"* or *"Do we have any games with no players?"* SQL JOINs to the rescue!  

---
#### Visualizing Joins with Images

To understand how each type of join works, let’s take a look at some images! Visualizing joins can really help clarify how they behave:

1. **INNER JOIN**  
   - An `INNER JOIN` returns only the rows where there’s a match in both tables.
      <img src="https://blog.codinghorror.com/content/images/uploads/2007/10/6a0120a85dcdae970b012877702708970c-pi.png" alt="INNER JOIN" width="250" height="150" style="display:block; margin-left: 0;"/>

2. **LEFT JOIN**  
   - A `LEFT JOIN` returns all rows from the left table, and the matched rows from the right table. If there’s no match, it returns `NULL` for the right table.
      <img src="https://media.geeksforgeeks.org/wp-content/uploads/20240605161731/Left_Join.png" alt="LEFT JOIN" width="250" height="150" style="display:block; margin-left: 0;"/>

3. **RIGHT JOIN**  
   - A `RIGHT JOIN` returns all rows from the right table, and the matched rows from the left table. If there’s no match, it returns `NULL` for the left table.
      <img src="https://media.geeksforgeeks.org/wp-content/uploads/20220515095048/join.jpg" alt="RIGHT JOIN" width="250" height="150" style="display:block; margin-left: 0;"/>

4. **FULL OUTER JOIN**  
   - A `FULL OUTER JOIN` returns all rows from both tables, with `NULL` where there’s no match.
      <img src="https://media.geeksforgeeks.org/wp-content/uploads/20240605161926/Full_Join.png" alt="FULL OUTER JOIN" width="250" height="150" style="display:block; margin-left: 0;"/>



## Setting up the Tables  
Let’s create two tables for this gaming league:  
1. **Players** table for gamers.  
2. **Games** table for the tournaments they participate in.  

### Step 1: Create and Populate the `games` Table  
```sql
CREATE TABLE games (
    game_id INT PRIMARY KEY,
    game_name VARCHAR(50)
);

INSERT INTO games (game_id, game_name) VALUES
(1, 'League of Legends'),
(2, 'Valorant'),
(3, 'Minecraft'),
(4, 'Fortnite');
```

### Step 2: Create and Populate the `players` Table  
```sql
CREATE TABLE players (
    player_id INT PRIMARY KEY,
    player_name VARCHAR(50),
    game_id INT
);

INSERT INTO players (player_id, player_name, game_id) VALUES
(1, 'Marouane', 1),  -- Marouane is in League of Legends
(2, 'Jamie', 2), -- Jamie is in Valorant
(3, 'Taylor', 4),-- Taylor is in Fortnite
(4, 'Said', NULL); -- Said hasn’t joined any game yet
```

---

## Performing SQL Joins  

### **INNER JOIN**  
An `INNER JOIN` returns players who have actually joined a game. No unplayed games or Offline players here!  

```sql
SELECT players.player_name, games.game_name
FROM players
INNER JOIN games ON players.game_id = games.game_id;
```  

**Result:**  

| player_name | game_name         |  
|-------------|-------------------|  
| Marouane    | League of Legends |  
| Jamie       | Valorant          |  
| Taylor      | Fortnite          |  

---

### **LEFT JOIN**  
A `LEFT JOIN` returns all players, even those who haven’t joined a game yet (like Said!).  

```sql
SELECT players.player_name, games.game_name
FROM players
LEFT JOIN games ON players.game_id = games.game_id;
```  

**Result:**  

| player_name | game_name         |  
|-------------|-------------------|  
| Marouane    | League of Legends |  
| Jamie       | Valorant          |  
| Taylor      | Fortnite          |  
| Said        | NULL              |  

---

### **RIGHT JOIN**  
A `RIGHT JOIN` shows all games, even those with no players. (Empty tournaments, anyone?)  

```sql
SELECT players.player_name, games.game_name
FROM players
RIGHT JOIN games ON players.game_id = games.game_id;
```  

**Result:**  

| player_name | game_name         |  
|-------------|-------------------|  
| Marouane    | League of Legends |  
| Jamie       | Valorant          |  
| Taylor      | Fortnite          |  
| NULL        | Minecraft         |  

---

### **FULL OUTER JOIN**  
A `FULL OUTER JOIN` combines everything: players with games, unplayed games, and players without games.  

```sql
SELECT players.player_name, games.game_name
FROM players
FULL OUTER JOIN games ON players.game_id = games.game_id;
```  

**Result:**  

| player_name | game_name         |  
|-------------|-------------------|  
| Marouane    | League of Legends |  
| Jamie       | Valorant          |  
| Taylor      | Fortnite          |  
| Said        | NULL              |  
| NULL        | Minecraft         |  

---

**Now it’s your turn!** Try tweaking the data to see how different join types behave. Remember, SQL is not just about queries—it’s about solving problems in your own "league"! 🎮

---

### Conclusion – SQL Can Be Fun! 🎉  
You’ve learned the basics of SQL in a fun and interactive way! 🎈 By now, you should be able to create a database, add tables, insert data, filter, update, delete, and even join tables like a pro. You’re well on your way to becoming an SQL wizard! 🧙‍♂️

Remember, SQL is like a superpower—you can do a lot with it, but you need to practice! So keep experimenting, and soon enough, you’ll be flexing those SQL muscles like a champion 💪.

Now go forth and conquer the world of databases, one query at a time! 🚀