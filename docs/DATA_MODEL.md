# Data Model (Entity Level)

A high-level view of the relational model (PostgreSQL). Field-level detail is intentionally omitted.

```mermaid
erDiagram
    USER ||--o{ COURSE_ENROLLMENT : has
    USER ||--o{ COURSE : teaches
    COURSE ||--o{ COURSE_ENROLLMENT : has
    COURSE ||--o{ COURSE_MODULE : contains
    COURSE ||--o{ LEARNING_RESOURCE : provides
    COURSE ||--o{ ASSIGNMENT : sets
    COURSE ||--o{ QUIZ : offers
    ASSIGNMENT ||--o| RUBRIC : graded_by
    RUBRIC ||--o{ RUBRIC_CRITERION : defines
    ASSIGNMENT ||--o| REFERENCE_SOLUTION : benchmarked_by
    ASSIGNMENT ||--o{ SUBMISSION : receives
    USER ||--o{ SUBMISSION : submits
    SUBMISSION ||--o{ SUBMISSION_FILE : includes
    SUBMISSION ||--o| AI_ASSESSMENT_RESULT : evaluated_as
    AI_ASSESSMENT_RESULT ||--o{ CRITERION_ASSESSMENT : breaks_down
    SUBMISSION ||--o| FACULTY_REVIEW : reviewed_in
    SUBMISSION ||--o| OFFICIAL_GRADE : finalised_as
    QUIZ ||--o{ QUIZ_QUESTION : contains
    QUIZ ||--o{ QUIZ_ATTEMPT : attempted_in
```

| Group | Entities |
| :--- | :--- |
| Identity | User (Student / Faculty / Admin) |
| Learning content | Course, Enrollment, Module, Learning Resource |
| Assessment setup | Assignment, Rubric, Rubric Criterion, Reference Solution, Quiz, Quiz Question |
| Student work | Submission, Submission File, Quiz Attempt |
| Evaluation | AI Assessment Result, Criterion Assessment, Faculty Review |
| Records | Official Grade |
