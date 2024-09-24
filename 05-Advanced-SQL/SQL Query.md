### The File to storage the SQL Queries of the Advanced SQL Assignment

### Datasets


##### Problem Set 1

```
SELECT S.NAME_OF_SCHOOL, S.COMMUNITY_AREA_NAME, S.AVERAGE_STUDENT_ATTENDANCE
FROM chicago_public_schools S LEFT JOIN chicago_socioeconomic_data C
ON C.HARDSHIP_INDEX = 98
```

##### problem Set 2

```
SELECT CR.CASE_NUMBER, CR.PRIMARY_TYPE, C.COMMUNITY_AREA_NAME
FROM chicago_crime CR LEFT JOIN chicago_socioeconomic_data C
ON CR.COMMUNITY_AREA_NUMBER = C.COMMUNITY_AREA_NUMBER
WHERE CR.LOCATION_DESCRIPTION LIKE '%SCHOOL%'
```

#### Exercise 2
##### Problem Set
```
#Creating the view:

CREATE VIEW SCHOLLVIEW (School_Name, Safety_Rating, Family_Rating, Environment_Rating, Instruction_Rating, Leaders_Rating, Teachers_Rating)
AS SELECT NAME_OF_SCHOOL, Safety_Icon, Family_Involvement_Icon, Environment_Icon, Instruction_Icon, Leaders_Icon, Teachers_Icon
FROM chicago_public_schools
```

```
#Select only the school name and the leaders rating from the view:

SELECT School_Name, Leaders_Rating
FROM SCHOLLVIEW
```

#### Exercise 3

##### Problem Set 1

```
DELIMITER $$
CREATE PROCEDURE UPDATE_LEADERS_SCORE (in_School_ID int, in_Leader_Score int)
BEGIN

END
DELIMITER ;

```

##### Problem Set 2

```
DELIMITER $$
CREATE PROCEDURE UPDATE_LEADERS_SCORE (in_School_ID int, in_Leader_Score int)
BEGIN
UPDATE chicago_public_schools
SET Leaders_Score = in_Leader_score
WHERE School_ID = in_School_ID
END
DELIMITER ;

```

##### Problem Set 3

```
DELIMITER $$
CREATE PROCEDURE `UPDATE_LEADERS_SCORE`(IN in_School_ID int,IN in_Leader_Score int)
BEGIN
UPDATE chicago_public_schools
SET Leaders_Score = in_Leader_score
WHERE School_ID = in_School_ID;

IF in_Leader_Score > 0 AND in_Leader_Score < 20
THEN UPDATE chicago_public_schools
SET Leaders_Icon = 'Very_Weak'
WHERE School_ID = in_School_ID;

ELSEIF in_Leader_Score < 40
THEN UPDATE chicago_public_schools
SET Leaders_Icon = 'Weak'
WHERE School_ID = in_School_ID;

ELSEIF in_Leader_Score < 60
THEN UPDATE chicago_public_schools
SET Leaders_Icon = 'Average'
WHERE School_ID = in_School_ID;

ELSEIF in_Leader_Score < 80
THEN UPDATE chicago_public_schools
SET Leaders_Icon = 'Strong'
WHERE School_ID = in_School_ID;

ELSEIF in_Leader_Score < 100
THEN UPDATE chicago_public_schools
SET Leaders_Icon = 'Very_Strong'
WHERE School_ID = in_School_ID;

END IF;


END $$

```


##### Problem Set 4

```
CALL UPDATE_LEADERS_SCORE(610316, 50)

```


#### Exercise 4

##### Problem Set 1

```
DELIMITER $$
CREATE PROCEDURE `UPDATE_LEADERS_SCORE`(IN in_School_ID int,IN in_Leader_Score int)
BEGIN
UPDATE chicago_public_schools
SET Leaders_Score = in_Leader_score
WHERE School_ID = in_School_ID;

IF in_Leader_Score > 0 AND in_Leader_Score < 20
THEN UPDATE chicago_public_schools
SET Leaders_Icon = 'Very_Weak'
WHERE School_ID = in_School_ID;

ELSEIF in_Leader_Score < 40
THEN UPDATE chicago_public_schools
SET Leaders_Icon = 'Weak'
WHERE School_ID = in_School_ID;

ELSEIF in_Leader_Score < 60
THEN UPDATE chicago_public_schools
SET Leaders_Icon = 'Average'
WHERE School_ID = in_School_ID;

ELSEIF in_Leader_Score < 80
THEN UPDATE chicago_public_schools
SET Leaders_Icon = 'Strong'
WHERE School_ID = in_School_ID;

ELSEIF in_Leader_Score < 100
THEN UPDATE chicago_public_schools
SET Leaders_Icon = 'Very_Strong'
WHERE School_ID = in_School_ID;

ELSE
ROLLBACK;

END IF;

END $$

```
##### Problem Set 2

```
DELIMITER $$
CREATE PROCEDURE `UPDATE_LEADERS_SCORE`(IN in_School_ID int,IN in_Leader_Score int)
BEGIN
UPDATE chicago_public_schools
SET Leaders_Score = in_Leader_score
WHERE School_ID = in_School_ID;

IF in_Leader_Score > 0 AND in_Leader_Score < 20
THEN UPDATE chicago_public_schools
SET Leaders_Icon = 'Very_Weak'
WHERE School_ID = in_School_ID;

ELSEIF in_Leader_Score < 40
THEN UPDATE chicago_public_schools
SET Leaders_Icon = 'Weak'
WHERE School_ID = in_School_ID;

ELSEIF in_Leader_Score < 60
THEN UPDATE chicago_public_schools
SET Leaders_Icon = 'Average'
WHERE School_ID = in_School_ID;

ELSEIF in_Leader_Score < 80
THEN UPDATE chicago_public_schools
SET Leaders_Icon = 'Strong'
WHERE School_ID = in_School_ID;

ELSEIF in_Leader_Score < 100
THEN UPDATE chicago_public_schools
SET Leaders_Icon = 'Very_Strong'
WHERE School_ID = in_School_ID;

ELSE
ROLLBACK;

END IF;
COMMIT;

END $$

```
##### Problem Set 1

```

```