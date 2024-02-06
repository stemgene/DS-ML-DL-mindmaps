# Common Syntax
## select (Resource: CH03/Your First SQL Statement)
### <p><code class="language-sql">SELECT DISTINCT movieID, MAX(rating) as "Max Rating", AVG(rating) as avgRating<br>FROM table_name<br>WHERE role NOT IN ('admin', 'premium')<br>GROUP BY movieID, title<br>ORDER BY movieID ASC, reviewerID Desc<br>LIMIT 1<br>OFFSET 3</code></p>
## update
### <p><code class="language-sql">UPDATE table_name SET 'col1' = 'value1', 'col2' = 'value2'<br> WHERE 'col' = 'value'</code></p>
## insert
### <p><code class="language-sql">INSERT INTO table_name ('col1', 'col2')<br>  VALUES ('value1', 'value2')</code></p>
### `INSERT INTO table_name SET 'col1' = 'value1', 'col2' = 'value2'` 
## delete
### <p><code class="language-sql">DELETE FROM table_name<br>WHERE 'col'='value'</code></p>
### <p><code class="language-sql">DELETE FROM table_name<br>WHERE 'col' BETWEEN 'value1' AND 'value2'</code></p>
# Useful SQL operators
## `AND`, `OR`, `NOT`
## `COUNT`, `MIN`, `MAX`, `AVG` (Resource: CH03/Aggregate Functions)
## `LIKE`: Search with input not exact match
### `LIKE '%a'`: ending with 'a'
### `LIKE '%or%'`: having 'or' in the middle
### `LIKE '_r%'`: having 'r' at the second place. '_' represents a single character
### `LIKE 'a%o'`: beginning with 'a' and ending with 'o'
## `BETWEEN`
## `IS`
### `WHERE rating IS NULL`
## `CAST`: Convert data type (Resource: CH03/Converting Data Types)
### `SELECT CAST ('9.5' AS decimal(10, 2))`
### `SELECT AVG(CAST(rating AS real)) AS average` equals to `SELECT AVG(rating::real) AS average`
## `SUBSTR()`
### `SUBSTR(string, start index, num length)`
### `WHERE LOWER(SUBSTR(city, 1, 1)) in ('a', 'e', 'i', 'o', 'u')`
## `EXTRACT` (Source: CH04/Operators and Functions for Working with Dates)
### `SELECT id_user, EXTRACT(MONTH FROM log_on) AS month_activity`
## Comparison operators (`=, !=, <, <=, >, >=`)
### numerical data: 
### strings: 
#### `WHERE month_name != 'January'`
#### `WHERE month_name > 'July'`

# AGGREGATION and GROUPING (Resource: CH04/Grouping Data)
## COUNT/COUNT(DISTINCT)
### <p><code class="language-sql">SELECT COUNT(*) AS num<br>FROM student<br>GROUP BY class_id;</code></p>
### <p><code class="language-sql">SELECT class_id, gender, COUNT(*) AS num<br>FROM student<br>GROUP BY class_id, gender;</code></p>
## MIN, MAX, AVG, SUM
### <p><code class="language-sql">SELECT MIN(population), MAX(population)<br>FROM city;</code></p>
### <p><code class="language-sql">SELECT country_id, MAX(population)<br>FROM city<br>GROUP BY country_id</code></p>
## HAVING (Resource: CH04/Processing Data Within a Grouping)
### <p><code class="language-sql">SELECT country_id, AVG(rating)<br>FROM city<br>GROUP BY country_id<br>HAVING AVG(rating) > 3.0</code></p>
## GROUP_CONCAT
### <p><code class="language-sql">//products: Basketball, Headphone, T-shirt<br>SELECT GROUP_CONCAT(DISTINCT product) AS products<br>FROM Activities<br>GROUP BY sale_date</code></p>

# Conditions
## IF conditions
### `IF(condition, value_if_true, value_if_false)`
### `SELECT IF(1=1, sleep(3), NULL)` Here the condition is true so it will trigger a delay for 3s
### <p><code class="language-sql">SELECT name<br>FROM content<br>WHERE id=128 AND IF(SUBSTR((SELECT table_name<br>&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;FROM table<br>&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;WHERE table_schema=database()), 1, 1) = 'a', True, False);</code></p>
### <p><code class="language-sql">SELECT IF((SELECT CONCAT_WS(name, id, image, score)<br>&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;FROM content<br>&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;WHERE name = 'user1'), true, false);</code></p>
### <p><code class="language-sql">SELECT *<br>FROM content<br>WHERE id=128 and IF((length((SELECT name<br>&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;FROM content<br>&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;WHERE id = 148))=7), true, false));</code></p>
## CASE WHEN conditions
### `CASE WHEN (condition) THEN result for true ELSE result for false END`
### <p><code class="language-sql">SELECT * <br>FROM content<br>WHERE id=128 AND CASE WHEN (length((SELECT name<br>&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&ensp;FROM content<br>&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&ensp;WHERE id=148))=7)<br>&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&ensp;THEN true<br>&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&ensp;ELSE false ;END</code></p>

# Subquery (Source: CH04/Subquery)
## In FROM block
### <p><code class="language-sql">SELECT AVG(Sub.count_rating) AS avg_count_rating<br>FROM (SELECT COUNT(rating) AS count_rating)<br>&emsp;&emsp;&emsp;&ensp;FROM books<br>&emsp;&emsp;&emsp;&ensp;GROUP BY genre) AS Sub;</code></p>
## In WHERE block:
### <p><code class="language-sql">SELECT col1, col2<br>FROM books<br>WHERE colname_name=(SELECT col1<br>&emsp;&emsp;&emsp;&ensp;&emsp;&emsp;&emsp;&ensp;&emsp;&emsp;&emsp;&ensp;&emsp;FROM table_name2<br>&ensp;&emsp;&emsp;&ensp;&emsp;&emsp;&ensp;&emsp;&emsp;&ensp;&emsp;&emsp;&emsp;&ensp;WHERE col1 = value);</code></p>

# Window Function: Perform calculations on sets of rows (Source: CH04/Window Functions)
## <p><code class="language-sql">--find the ratio of the price of each book to the total cost of that author's books.<br>SELECT price / SUM(price) OVER (PARTITION BY author_id) </code></p>