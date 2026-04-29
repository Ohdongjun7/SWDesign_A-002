```mermaid
graph LR
    %% 행위자(Actors) 정의
    S(["학생 (Student)"])
    P(["교수 (Professor)"])

    subgraph Academic_Management_System ["학사관리 시스템 (Academic Management System)"]
        %% 유스케이스(Use Cases) 정의
        UC_S_REG(["학생 등록"])
        UC_S_VIEW(["학생 조회"])
        UC_S_AUTH(["학생 인증"])
        
        UC_P_REG(["교수 등록"])
        UC_P_VIEW(["교수 조회"])
        UC_P_AUTH(["교수 인증"])

        UC_SUB_REG(["과목 등록"])
        UC_SCORE_IN(["과목 점수 입력"])
        UC_ENROLL(["수강 신청"])
        UC_GRADE_VIEW(["학점 조회"])
        UC_SUB_VIEW(["과목 조회"])

        %% 포함(Include) 관계 설정
        UC_ENROLL -. "<<include>>" .-> UC_S_AUTH
        UC_GRADE_VIEW -. "<<include>>" .-> UC_S_AUTH
        
        UC_SUB_REG -. "<<include>>" .-> UC_P_AUTH
        UC_SCORE_IN -. "<<include>>" .-> UC_P_AUTH
    end

    %% 학생 연결
    S --- UC_S_REG
    S --- UC_S_VIEW
    S --- UC_S_AUTH
    S --- UC_ENROLL
    S --- UC_GRADE_VIEW
    S --- UC_SUB_VIEW

    %% 교수 연결
    P --- UC_P_REG
    P --- UC_P_VIEW
    P --- UC_P_AUTH
    P --- UC_SUB_REG
    P --- UC_SCORE_IN
    P --- UC_SUB_VIEW