# sb-miniproject8
Spark Optimization - Mini Project

## Data model

### Questions:
```
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
 
 +-----------+---------+--------------------+--------+-------+-----+
|question_id|answer_id|       creation_date|comments|user_id|score|
+-----------+---------+--------------------+--------+-------+-----+
|     226592|   226595|2015-12-29 17:46:...|       3|  82798|    2|
|     388057|   388062|2018-02-22 12:52:...|       8|    520|   21|
|     293286|   293305|2016-11-17 15:35:...|       0|  47472|    2|
|     442499|   442503|2018-11-22 00:34:...|       0| 137289|    0|
|     293009|   293031|2016-11-16 07:36:...|       0|  83721|    0|
|     395532|   395537|2018-03-25 00:51:...|       0|   1325|    0|
|     329826|   329843|2017-04-29 10:42:...|       4|    520|    1|
|     294710|   295061|2016-11-26 19:29:...|       2| 114696|    2|
|     291910|   291917|2016-11-10 04:56:...|       0| 114696|    2|
|     372382|   372394|2017-12-03 20:17:...|       0| 172328|    0|
|     178387|   178394|2015-04-25 12:31:...|       6|  62726|    0|
|     393947|   393948|2018-03-17 17:22:...|       0| 165299|    9|
|     432001|   432696|2018-10-05 03:47:...|       1| 102218|    0|
|     322740|   322746|2017-03-31 13:10:...|       0|    392|    0|
|     397003|   397008|2018-04-01 06:31:...|       1| 189394|    6|
|     223572|   223628|2015-12-11 23:40:...|       0|  94772|   -1|
|     220328|   220331|2015-11-24 09:57:...|       3|  92883|    1|
|     176400|   176491|2015-04-16 08:13:...|       0|  40330|    0|
|     265167|   265179|2016-06-28 06:58:...|       0|  46790|    0|
|     309103|   309105|2017-02-01 11:00:...|       2|  89597|    2|
+-----------+---------+--------------------+--------+-------+-----+
 ```
 ### Answers
```
root
 |-- question_id: long (nullable = true)
 |-- answer_id: long (nullable = true)
 |-- creation_date: timestamp (nullable = true)
 |-- comments: long (nullable = true)
 |-- user_id: long (nullable = true)
 |-- score: long (nullable = true) 
 
 +-----------+--------------------+--------------------+--------------------+------------------+--------+-------+-----+
|question_id|                tags|       creation_date|               title|accepted_answer_id|comments|user_id|views|
+-----------+--------------------+--------------------+--------------------+------------------+--------+-------+-----+
|     382738|[optics, waves, f...|2018-01-28 01:22:...|What is the pseud...|            382772|       0|  76347|   32|
|     370717|[field-theory, de...|2017-11-25 03:09:...|What is the defin...|              null|       1|  75085|   82|
|     339944|[general-relativi...|2017-06-17 15:32:...|Could gravitation...|              null|      13| 116137|  333|
|     233852|[homework-and-exe...|2016-02-04 15:19:...|When does travell...|              null|       9|  95831|  185|
|     294165|[quantum-mechanic...|2016-11-22 05:39:...|Time-dependent qu...|              null|       1| 118807|   56|
|     173819|[homework-and-exe...|2015-04-02 10:56:...|Finding Magnetic ...|              null|       5|  76767| 3709|
|     265198|    [thermodynamics]|2016-06-28 09:56:...|Physical meaning ...|              null|       2|  65035| 1211|
|     175015|[quantum-mechanic...|2015-04-08 20:24:...|Understanding a m...|              null|       1|  76155|  326|
|     413973|[quantum-mechanic...|2018-06-27 08:29:...|Incorporate spino...|              null|       3| 167682|   81|
|     303670|[quantum-field-th...|2017-01-08 00:05:...|A Wilson line pro...|              null|       0| 101968|  184|
|     317368|[general-relativi...|2017-03-08 13:53:...|Shouldn't Torsion...|              null|       0|  20427|  305|
|     369982|[quantum-mechanic...|2017-11-20 21:11:...|Incompressible in...|              null|       4| 124864|   83|
|     239745|[quantum-mechanic...|2016-02-25 02:51:...|Is this correct? ...|            239773|       2|  89821|   78|
|     412294|[quantum-mechanic...|2018-06-17 19:46:...|Is electron/photo...|              null|       0|    605|   61|
|     437521|[thermodynamics, ...|2018-10-29 01:49:...|Distance Dependen...|              null|       2| 211152|   19|
|     289701|[quantum-field-th...|2016-10-29 22:56:...|Generalize QFT wi...|              null|       4|  31922|   49|
|     239505|[definition, stab...|2016-02-24 04:51:...|conditions for so...|              null|       3| 102021|  121|
|     300744|[electromagnetism...|2016-12-24 12:14:...|Maxwell equations...|            300749|       0| 112190|  171|
|     217315|[nuclear-physics,...|2015-11-08 03:13:...|Is the direction ...|              null|       1|  60150| 1749|
|     334778|[cosmology, cosmo...|2017-05-22 08:58:...|Why are fluctatio...|            334791|       3| 109312|  110|
+-----------+--------------------+--------------------+--------------------+------------------+--------+-------+-----+
```

Query Plan
