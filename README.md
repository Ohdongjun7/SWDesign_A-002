```mermaid
classDiagram
    direction TB

    class User {
        <<Abstract>>
        +String id
        +String password
        +String name
        +login() Boolean
    }

    class Student {
        +registerStudent()
        +viewStudent()
        +applyForSubject()
        +viewGrades()
    }

    class Professor {
        +registerProfessor()
        +viewProfessor()
        +registerSubject()
        +inputSubjectScore()
    }

    class Subject {
        +String subjectId
        +String subjectName
        +int score
        +String grade
        +updateScore(int score)
        +calculateGrade()
    }

    %% 상속 관계
    User <|-- Student
    User <|-- Professor

    %% 연관 관계 및 제약 조건
    %% 학생은 3~5개의 과목을 수강
    %% 과목 하나에는 30~35명의 학생이 존재
    Student "30..35" -- "3..5" Subject : 수강신청

    %% 교수는 1~3개의 과목을 등록/관리
    %% 과목은 교수 1명에 의해서만 관리됨
    Professor "1" -- "1..3" Subject : 관리/등록