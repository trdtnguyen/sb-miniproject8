# sb-miniproject8
Spark Optimization - Mini Project

## Data model

### Questions:
root
 |-- question_id: long (nullable = true)
 |-- tags: array (nullable = true)
 |    |-- element: string (containsNull = true)
 |-- creation_date: timestamp (nullable = true)
 |-- title: string (nullable = true)
 |-- accepted_answer_id: long (nullable = true)
 |-- comments: long (nullable = true)
 |-- user_id: long (nullable = true)
 |-- views: long (nullable = true)
 
 ### Answers
root
 |-- question_id: long (nullable = true)
 |-- answer_id: long (nullable = true)
 |-- creation_date: timestamp (nullable = true)
 |-- comments: long (nullable = true)
 |-- user_id: long (nullable = true)
 |-- score: long (nullable = true) 
