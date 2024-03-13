# SQL basics

## basic query, filtering & ordering rows

```sql
SELECT <DISTINCT> <column> <AS> FROM <table>
    WHERE <conditions>
        [AND, OR, NOT, BETWEEN, IN (), LIKE]
        [IS/IS NOT NULL]
    ORDER BY <column> LIMIT <n>;

COALESCE(x, y, z, ...) -- returns the first non-null
IFNULL(x, y) -- returns y if x is null
```

## aggregate and math functions

```sql
SELECT
    COUNT(<column>)
    SUM(<column>)
    MIN(<column>)
    MAX(<column>)
    AVG(<column>)
    ABS(<column>)
    ROUND(<column>, <decimal>)
    CEIL/FLOOR(<column>)
    POWER(<column>, <n>)
    MOD(<column>, <n>)
    CAST(<column> AS DECIMAL/FLOAT) -- ::DECIMAL, ::FLOAT
    FROM <table> [...];
```

## group by, having

```sql
SELECT <column> FROM <table> GROUP BY <column> HAVING [...];
```

## case statement

```sql
SELECT <column>
    CASE
        WHEN <condition> THEN <result>
        WHEN <condition> THEN <result>
        [...]
        ELSE <result>
    END AS <alias>
FROM <table>;
```

## join

```sql
SELECT * FROM <table1> JOIN <table2> ON <table1.colum> = <table2.column>
```

`INNER` - only the rows with matching values from both tables

`LEFT` - all the rows from the left table and the matching rows from the right table

`RIGHT` - all the rows from the right table and the matching rows from the left table

`FULL OUTER` - all rows when there is a match in either the left or the right table (if there is no match, NULL values are returned for columns from the table without a match)

## date and time

```sql
CURRENT_DATE, CURRENT_TIME, CURRENT_TIMESTAMP, NOW()

EXTRACT(<PART> FROM <datetime>)
DATE_PART('<part>', <datetime>)

DATE_TRUNC('<part>', <datetime>)
<date> + INTERVAL '<datetime>'

TO_DATE(<string>) -- ::DATE
TO_TIMESTAMP(<string>) -- ::TIMESTAMP
TO_CHAR(<datetime>, '<format>')
```

| Format Name | Format | Example |
| - | - | - |
| ISO 8601 Date and Time | 'YYYY-MM-DD HH24:MI:SS' | '2023-08-27 14:30:00' |
| Date and Time with 12-hour Format | 'YYYY-MM-DD HH:MI:SS AM' | '2023-08-27 02:30:00 PM' |
| Long Month Name, Day and Year | 'Month DDth, YYYY' | 'August 27th, 2023' |
| Short Month Name, Day and Year | 'Mon DD, YYYY' | 'Aug 27, 2023' |
| Day, Month, and Year | 'DD Month YYYY' | '27 August 2023' |
| Day of the Month | 'Month' | 'August' |
| Day of the Week | 'Day' | 'Saturday' |
