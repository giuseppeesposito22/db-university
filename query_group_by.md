1. Contare quanti iscritti ci sono stati ogni anno

```sql
SELECT count(`enrolment_date`) as `number_of_members`, year(`enrolment_date`) as `year`
FROM `students`
GROUP BY year(`enrolment_date`)
ORDER BY `year` ASC;
```

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

```sql
SELECT count(`office_address`) as `number_of_teachers`, `office_address`
FROM `teachers`
GROUP BY `office_address`
```

3. Calcolare la media dei voti di ogni appello desame

```sql
SELECT `exam_id`,
avg(`vote`) as `vote_avg`
FROM `exam_student`
group by `exam_id`
```

4. Contare quanti corsi di laurea ci sono per ogni dipartimento

```sql
SELECT `department_id`,
count(*) as `num_of_courses`
FROM `degrees`
group by `department_id`;
```
