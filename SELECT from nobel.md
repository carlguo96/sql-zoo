
## SELECT from nobel

### 1. Change the query shown so that it displays Nobel prizes for 1950.
 ```SQL
 SELECT yr, subject, winner FROM nobel
  WHERE yr = 1950
 ```
### 2. Show who won the 1962 prize for Literature.
 ```SQL
 SELECT winner FROM nobel
  WHERE yr = 1962 AND subject = 'Literature'
 ```

### 3. Show the year and subject that won 'Albert Einstein' his prize.
 ```SQL
  SELECT yr, subject FROM nobel
   WHERE winner = 'Albert Einstein'
 ```
### 4. Give the name of the 'Peace' winners since the year 2000, including 2000.
 ```SQL
   SELECT winner FROM nobel
    WHERE yr >= 2000 AND subject = 'Peace'
 ```
### 5. Show all details (yr, subject, winner) of the Literature prize winners for 1980 to 1989 inclusive.
 ```SQL
  SELECT yr, subject, winner FROM nobel
   WHERE yr >= 1980 AND yr<=1989 AND subject = 'Literature'
 ```
 
 ```SQL
SELECT yr, subject, winner 
FROM nobel 
WHERE subject = 'Literature' AND yr between 1980 AND 1989
 ```
### 6. Show all details of the presidential winners:
Theodore Roosevelt
Woodrow Wilson
Jimmy Carter
Barack Obama
 ```SQL
 SELECT * FROM nobel
 WHERE winner IN ('Theodore Roosevelt',
                  'Woodrow Wilson', 'Jimmy Carter',
                  'Barack Obama')
 ```
 
 ### 7. Show the winners with first name John
 ```SQL
 SELECT winner FROM nobel
  WHERE winner LIKE 'John%'
 ```
 
 ### 8. Show the Physics winners for 1980 together with the Chemistry winners for 1984.
 ```SQL
 SELECT * FROM nobel
  WHERE (subject = 'Physics' AND yr = 1980) OR (subject = 'Chemistry' AND yr = 1984)
 ```
 
 ### 9. how the winners for 1980 excluding the Chemistry and Medicine
 ```SQL
 SELECT * FROM nobel
  WHERE (subject!='Chemistry' AND subject!='Medicine') AND yr=1980
 ```
 ```SQL
 SELECT *
 FROM nobel 
 WHERE yr = 1980 AND subject NOT IN ('Chemistry', 'Medicine')
 ```
 ### 10. how who won a 'Medicine' prize in an early year (before 1910, not including 1910) together with winners of a 'Literature' prize in a later year (after 2004, including 2004)
 ```SQL
 SELECT * FROM nobel
  WHERE (subject='Medicine' AND yr<1910) OR (subject='Literature' AND yr>=2004)
 ```
  ```SQL
  SELECT * 
  FROM nobel 
  WHERE subject = 'Medicine' AND yr < 1910 
  union 
  SELECT * 
  FROM nobel 
  WHERE subject = 'Literature' AND yr >= 2004 
 ```
 ### 11. Find all details of the prize won by PETER GRÜNBERG
 ```SQL
 SELECT * FROM nobel 
WHERE winner = 'PETER GRÜNBERG' 
 ```
 
 
 ### 12. Find all details of the prize won by EUGENE O'NEILL
Escaping single quotes
You can't put a single quote in a quote string directly. You can use two single quotes within a quoted string.
 ```SQL
 SELECT * FROM nobel 
  WHERE winner = 'EUGENE O''NEILL' 
 ```
 
  ### 13. Change the query shown so that it displays Nobel prizes for 1950.
 ```SQL
 SELECT winner,yr,subject FROM nobel 
  WHERE winner Like 'sir%' 
  ORDER BY 'yr'
 ```
       'yr'是反序
  ### 14. The expression subject IN ('Chemistry','Physics') can be used as a value - it will be 0 or 1.

Show the 1984 winners and subject ordered by subject and winner name; but list Chemistry and Physics last.
 ```SQL
 SELECT winner, subject FROM nobel
  WHERE yr=1984
  ORDER BY subject IN ('Chemistry', 'Physics'), subject, winner
 ```
