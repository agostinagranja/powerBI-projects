--initial query: create dataframe with data needed

--expenses

CREATE TABLE personalfinances.expenses AS
  SELECT 
    Fecha_y_hora AS date,
    Categor__a AS cathegory,
    Comentario AS concept,
    Cantidad_en_la_divisa_de_la_cuenta AS amount
  FROM `my-finance-344415.personalfinances.expenses_06072022`
  ORDER BY date ASC;

SELECT 
  *
FROM 
  `my-finance-344415.personalfinances.expenses`;

--income

CREATE TABLE personalfinances.incomes AS
  SELECT 
    Fecha_y_hora AS date,
    Categor__a AS cathegory,
    Comentario AS concept,
    Cantidad_en_la_divisa_predeterminada AS amount
  FROM `my-finance-344415.personalfinances.incomes_06072022`
  ORDER BY date ASC;

SELECT 
  *
FROM 
  `my-finance-344415.personalfinances.incomes`;

--data exploration

--expenses

SELECT 
  MIN(date) AS first_date,
  MAX(date) AS last_date
FROM 
  my-finance-344415.personalfinances.expenses;

SELECT 
  DISTINCT (cathegory) AS cathegories
FROM 
  my-finance-344415.personalfinances.expenses;

SELECT 
  DISTINCT (concept) AS concepts,
  LENGTH(concept) AS length
FROM 
  my-finance-344415.personalfinances.expenses
ORDER BY 
  concept;

SELECT 
  MIN(amount) AS min,
  MAX(amount) AS max
FROM 
  my-finance-344415.personalfinances.expenses;

SELECT 
  date,
  cathegory,
  concept,
  amount
FROM 
  my-finance-344415.personalfinances.expenses
ORDER BY  
  amount ASC;

SELECT
  (SELECT 
    COUNT(*) 
  FROM 
    (SELECT 
      DISTINCT * 
    FROM my-finance-344415.personalfinances.expenses)) AS distinct_rows,
  (SELECT 
    COUNT(*)
  FROM 
    my-finance-344415.personalfinances.expenses) AS total_rows;

--income

SELECT 
  MIN(date) AS first_date,
  MAX(date) AS last_date
FROM 
  my-finance-344415.personalfinances.incomes;

SELECT 
  DISTINCT (cathegory) AS cathegories
FROM 
  my-finance-344415.personalfinances.incomes;

SELECT 
  DISTINCT (concept) AS concepts,
  LENGTH(concept) AS length
FROM 
  my-finance-344415.personalfinances.incomes
ORDER BY 
  concept;

SELECT 
  MIN(amount) AS min,
  MAX(amount) AS max
FROM 
  my-finance-344415.personalfinances.incomes;

SELECT 
  date,
  cathegory,
  concept,
  amount
FROM 
  my-finance-344415.personalfinances.incomes
ORDER BY  
  amount ASC;



--data cleaning

--expenses

UPDATE 
    my-finance-344415.personalfinances.expenses
SET 
    cathegory = 'Culture' 
WHERE 
    cathegory = 'Cultural';

UPDATE 
    my-finance-344415.personalfinances.expenses
SET 
    concept = 'Supermarket' 
WHERE 
    concept = 'Supermarket ';

REPLACE TABLE my-finance-344415.personalfinances.expenses AS 
    SELECT
        DISTINCT *
    FROM my-finance-344415.personalfinances.expenses;
    
 --data analysis

--expenses

--expenses per month per category
SELECT
    FORMAT_DATE("%Y-%m",date) AS year_month,
    cathegory,
    SUM (amount) AS subtotal_expenses
FROM
    my-finance-344415.personalfinances.expenses
GROUP BY
    year_month,
    cathegory
ORDER BY
    year_month ASC,
    cathegory ASC;

--expenses per month per concept
SELECT
    FORMAT_DATE("%Y-%m",date) AS year_month,
    concept,
    SUM (amount) AS subtotal_expenses
FROM
    my-finance-344415.personalfinances.expenses
GROUP BY
    year_month,
    concept
ORDER BY
    year_month ASC,
    concept ASC;

--monthly variation %
SELECT 
    year_month,
    ROUND(total,2) AS total,
    ROUND(((total - LAG(total) OVER(ORDER BY year_month ASC))/ LAG(total) OVER(ORDER BY year_month ASC)),2) AS growth_rate

FROM (
    SELECT
        FORMAT_DATE("%Y-%m",date) AS year_month,
        SUM (amount) AS total
    FROM
        my-finance-344415.personalfinances.expenses
    GROUP BY
        year_month
)
ORDER BY 
    year_month ASC;

--monthly variation % (basic)
SELECT 
    year_month,
    cathegory,
    ROUND(total,2) AS total,
    ROUND(((total - LAG(total) OVER(ORDER BY year_month ASC))/ LAG(total) OVER(ORDER BY year_month ASC)),2) AS growth_rate

FROM (
    SELECT
        FORMAT_DATE("%Y-%m",date) AS year_month,
        cathegory,
        SUM (amount) AS total
    FROM
        my-finance-344415.personalfinances.expenses
    WHERE 
        cathegory = 'Basic'
    GROUP BY
        year_month,
        cathegory
)
ORDER BY 
    year_month ASC;

--monthly variation % (optional)
SELECT 
    year_month,
    cathegory,
    ROUND(total,2) AS total,
    ROUND(((total - LAG(total) OVER(ORDER BY year_month ASC))/ LAG(total) OVER(ORDER BY year_month ASC)),2) AS growth_rate

FROM (
    SELECT
        FORMAT_DATE("%Y-%m",date) AS year_month,
        cathegory,
        SUM (amount) AS total
    FROM
        my-finance-344415.personalfinances.expenses
    WHERE 
        cathegory = 'Optional'
    GROUP BY
        year_month,
        cathegory
)
ORDER BY 
    year_month ASC;

--monthly variation % (culture)
SELECT 
    year_month,
    cathegory,
    ROUND(total,2) AS total,
    ROUND(((total - LAG(total) OVER(ORDER BY year_month ASC))/ LAG(total) OVER(ORDER BY year_month ASC)),2) AS growth_rate

FROM (
    SELECT
        FORMAT_DATE("%Y-%m",date) AS year_month,
        cathegory,
        SUM (amount) AS total
    FROM
        my-finance-344415.personalfinances.expenses
    WHERE 
        cathegory = 'Culture'
    GROUP BY
        year_month,
        cathegory
)
ORDER BY 
    year_month ASC;

--monthly variation % (extras)
SELECT 
    year_month,
    cathegory,
    ROUND(total,2) AS total,
    ROUND(((total - LAG(total) OVER(ORDER BY year_month ASC))/ LAG(total) OVER(ORDER BY year_month ASC)),2) AS growth_rate

FROM (
    SELECT
        FORMAT_DATE("%Y-%m",date) AS year_month,
        cathegory,
        SUM (amount) AS total
    FROM
        my-finance-344415.personalfinances.expenses
    WHERE 
        cathegory = 'Extras'
    GROUP BY
        year_month,
        cathegory
)
ORDER BY 
    year_month ASC;

