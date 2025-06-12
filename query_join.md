1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

```sql
SELECT `students`.*
FROM `students`
INNER JOIN `degrees`
ON students.degree_id = degrees.id
WHERE degrees.name = "Corso di Laurea in Economia";
```

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di
   Neuroscienze

```sql
SELECT `degrees`.*
FROM `departments`
INNER JOIN `degrees`
ON `departments`.`id` = `degrees`.`department_id`
WHERE `departments`.`name` = "Dipartimento di Neuroscienze" AND `degrees`.`level` = "magistrale";
```

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

```sql
SELECT `courses`.*
FROM `courses`
INNER JOIN `course_teacher`
ON `courses`.`id` = `course_teacher`.`course_id`
INNER JOIN `teachers`
ON `teachers`.`id` = `course_teacher`.`teacher_id`
WHERE `teachers`.`id` = 44;
```

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
   sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
   nome

```sql
SELECT *
FROM `students`
INNER JOIN `degrees`
ON `students`.`degree_id` = `degrees`.`id`
INNER JOIN `departments`
ON `degrees`.`department_id` = `departments`.`id`
ORDER BY `students`.`surname` ASC, `students`.`name` ASC
```

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

```sql
SELECT *
FROM `degrees`
INNER JOIN `courses`
ON `degrees`.`id` = `courses`.`degree_id`
INNER JOIN `course_teacher`
ON `courses`.`id` = `course_teacher`.`course_id`
INNER JOIN `teachers`
ON `course_teacher`.`teacher_id` = `teachers`.`id`
ORDER BY `degrees`.`id`;
```

6. Selezionare tutti i docenti che insegnano nel Dipartimento di
   Matematica (54)

```sql
SELECT `teachers`.*
FROM `teachers`
INNER JOIN `course_teacher`
ON `teachers`.`id` = `course_teacher`.`teacher_id`
INNER JOIN `courses`
ON `courses`.`id` = `course_teacher`.`course_id`
INNER JOIN 	`degrees`
ON `courses`.`degree_id` = `degrees`.`id`
INNER JOIN `departments`
ON `degrees`.`department_id` = `departments`.`id`
WHERE `departments`.`id` = 5;
```

7. BONIJS: Selezionare per ogni studente il numero di tentativi sostenuti
   per ogni esame, stampando anche il voto massimo. Successivamente,
   filtrare i tentativi con voto minimo 18.

   ```sql
   SELECT
   `students`.`id`,
   `students`.`name`,
   `students`.`surname`,
   COUNT(`exam_student`.`student_id`) as `attempts`,
   MAX(`exam_student`.`vote`) as `max_vote`
   FROM `students`
   INNER JOIN `exam_student`
   ON `students`.`id` = `exam_student`.`student_id`
   INNER JOIN	`exams`
   ON `exam_student`.`exam_id` = `exams`.`id`
   GROUP BY `students`.`id`
   ORDER BY `students`.`id`;
   ```

```sql
   SELECT
   `students`.`id`,
   `students`.`name`,
   `students`.`surname`,
   COUNT(`exam_student`.`student_id`) as `attempts`
   FROM `students`
   INNER JOIN `exam_student`
   ON `students`.`id` = `exam_student`.`student_id`
   INNER JOIN	`exams`
   ON `exam_student`.`exam_id` = `exams`.`id`
   WHERE `exam_student`.`vote` >= 18
   GROUP BY `students`.`id`
   ORDER BY `students`.`id`;
```
