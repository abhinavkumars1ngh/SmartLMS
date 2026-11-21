# Assessment & Faculty Review Workflow

```mermaid
sequenceDiagram
    actor F as Faculty
    actor S as Student
    participant L as LMS Backend
    participant A as AI Engine
    participant D as Database

    F->>L: Create assignment, upload question file and confidential answer key
    L->>A: Index answer key (private workflow B)
    S->>L: Download question file
    S->>L: Submit solution
    L->>D: Status SUBMITTED
    L->>A: Evaluate submission
    Note over L,D: Status EVALUATING
    A->>A: Semantic similarity and rubric criteria with evidence
    A-->>L: Proposed score and citations
    L->>D: Status EVALUATED
    F->>L: Open review queue, inspect AI proposal
    F->>L: Adjust marks, add feedback, publish
    L->>D: Official grade recorded, status PUBLISHED
    S->>L: View published grade and feedback
```

## Status Lifecycle

`SUBMITTED` → `EVALUATING` → `EVALUATED` → `PUBLISHED`

## Key Guarantees

- Students never see the AI's raw proposal or the reference solution.
- An official grade exists **only** after explicit faculty publication.
- Evaluation recognises equivalent solutions, such as recursion versus iteration or vectorised versus looped code.
- Every rubric criterion in the AI proposal carries supporting evidence from the submission.
