Selezionare tutti gli studenti nati nel 1990 (160)

```sql
SELECT *
FROM `students`
WHERE YEAR(`date_of_birth`) = 1990;
```

Selezionare tutti i corsi che valgono più di 10 crediti (479)

```sql
SELECT *
FROM `courses`
WHERE `cfu` > 10 ;
```

Selezionare tutti gli studenti che hanno più di 30 anni

```sql
SELECT *
FROM `students`
WHERE `date_of_birth` < "1995-06-11";
```

Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di
laurea (286)

```sql

SELECT *
FROM `courses`
WHERE `period` = "I semestre" AND `year` = 1;

```

Selezionare tutti gli appelli desame che avvengono nel pomeriggio (dopo le 14) del
20/06/2020 (21)

```sql

SELECT *
FROM `exams`
WHERE `date` = "2020-06-20" AND hour > "14:00";
```

Selezionare tutti i corsi di laurea magistrale (38)

```sql

SELECT *
FROM degrees
WHERE `name` like "%laurea magistrale%";
```

Da quanti dipartimenti è composta l'università? (12)

```sql
SELECT count(*) as `number_of_departments`
FROM `departments`;
```

Quanti sono gli insegnanti che non hanno un numero di telefono? (50)

```sql
SELECT count(*) as `teachers_without_phone`
FROM `teachers`
WHERE `phone` is NULL;
```
