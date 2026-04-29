```mermaid
useCaseDiagram
    actor "학생 (Student)" as S
    actor "교수 (Professor)" as P

    package "학사관리 시스템" {
        usecase "학생 등록" as UC_S_REG
        usecase "학생 조회" as UC_S_VIEW
        usecase "학생 인증" as UC_S_AUTH
        
        usecase "교수 등록" as UC_P_REG
        usecase "교수 조회" as UC_P_VIEW
        usecase "교수 인증" as UC_P_AUTH

        usecase "과목 등록" as UC_SUB_REG
        usecase "과목 점수 입력" as UC_SCORE_IN
        usecase "수강 신청" as UC_ENROLL
        usecase "학점 조회" as UC_GRADE_VIEW
        usecase "과목 조회" as UC_SUB_VIEW
    }

    %% 학생의 활동
    S --> UC_S_REG
    S --> UC_S_VIEW
    S --> UC_S_AUTH
    S --> UC_ENROLL
    S --> UC_GRADE_VIEW
    S --> UC_SUB_VIEW

    %% 교수의 활동
    P --> UC_P_REG
    P --> UC_P_VIEW
    P --> UC_P_AUTH
    P --> UC_SUB_REG
    P --> UC_SCORE_IN
    P --> UC_SUB_VIEW

    %% 관계 정의 (Include)
    UC_ENROLL ..> UC_S_AUTH : <<include>>
    UC_GRADE_VIEW ..> UC_S_AUTH : <<include>>
    
    UC_SUB_REG ..> UC_P_AUTH : <<include>>
    UC_SCORE_IN ..> UC_P_AUTH : <<include>>