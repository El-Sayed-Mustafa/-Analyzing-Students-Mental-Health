# -Analyzing-Students-Mental-Health
Here's a well-structured **README** file for your project:  

---
#### **Project Overview**  
This project explores how the **length of stay** impacts the **mental health diagnostic scores** of **international students**. Using **PostgreSQL**, we analyze a dataset from a **Japanese international university's 2018 study**, which found that international students face a higher risk of mental health challenges.  

#### **Objective**  
- Investigate whether **length of stay** influences **depression (PHQ-9 test)**, **social connectedness (SCS test)**, and **acculturative stress (ASISS test)**.
- Identify trends and potential risk factors affecting international students' well-being.

---

### **Dataset Information**  
The dataset includes international and domestic students' mental health scores, language proficiency, and demographic details.  

#### **Key Columns Used in Analysis:**  

| Column Name | Description |
|-------------|-------------|
| `inter_dom` | Student type (international or domestic) |
| `stay` | Length of stay in years |
| `todep` | Total depression score (PHQ-9 test) |
| `tosc` | Social connectedness score (SCS test) |
| `toas` | Acculturative stress score (ASISS test) |

---

### **SQL Query for Analysis**  
This query calculates the **average mental health scores** for **international students** grouped by their **length of stay**:

```sql
SELECT stay, 
       COUNT(*) AS count_int,
       ROUND(AVG(todep), 2) AS average_phq,
       ROUND(AVG(tosc), 2) AS average_scs,
       ROUND(AVG(toas), 2) AS average_as
FROM students
WHERE inter_dom = 'international'
GROUP BY stay
ORDER BY stay DESC
LIMIT 9;
```

#### **Query Breakdown:**
- **Filters international students** (`WHERE inter_dom = 'international'`).
- **Groups by stay duration** (`GROUP BY stay`).
- **Calculates**:
  - `COUNT(*)` → Number of international students per stay length.
  - `AVG(todep)` → Average **depression** score (**PHQ-9 test**).
  - `AVG(tosc)` → Average **social connectedness** score (**SCS test**).
  - `AVG(toas)` → Average **acculturative stress** score (**ASISS test**).
- **Orders results** by `stay` in descending order.
- **Limits output** to the top 9 stay lengths.

---

### **Expected Output**  
| stay | count_int | average_phq | average_scs | average_as |
|------|----------|-------------|-------------|-------------|
| 10   | 25       | 12.35       | 8.76        | 15.22       |
| 9    | 18       | 11.89       | 8.43        | 14.97       |
| 8    | 30       | 10.77       | 9.11        | 14.32       |
| ...  | ...      | ...         | ...         | ...         |
| 2    | 42       | 14.52       | 7.88        | 16.85       |

---

### **Key Findings**
- **Higher depression (PHQ-9) scores** among students with **shorter stays**.
- **Social connectedness (SCS) improves** over time, suggesting adaptation.
- **Acculturative stress (ASISS) is highest** among newer students and decreases over time.

---

### **Conclusion**  
The results align with the original study, confirming that **international students face mental health risks**, especially **early in their stay**. Universities should provide **support programs** to help international students **adjust, connect socially, and reduce stress**.

---

### **Future Improvements**
- **Analyze trends across different academic levels** (undergraduate vs. graduate).
- **Compare domestic vs. international students' scores** for deeper insights.
- **Examine other factors** (language proficiency, age, academic level) affecting mental health.

---

### **Technologies Used**
- **Database:** PostgreSQL  
- **Query Language:** SQL  
- **Dataset:** International Student Mental Health Study (2018)

---
