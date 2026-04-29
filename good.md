```mermaid
classDiagram
    class Student {
        - studentId:String
        - password:String
        - name:String
        + 학생등록():void
        + 학생조회():Student
        + 학생인증(studentId:String, password:String):boolean
        + 수강신청(subjectId:String):void
        + 학점조회(subjectId:String):String
    }

    class Professor {
        - professorId:String
        - password:String
        - name:String
        + 교수등록():void
        + 교수조회():Professor
        + 교수인증(professorId:String, password:String):boolean
        + 과목등록(subjectName:String):void
        + 과목점수입력(studentId:String, subjectId:String, score:int):String
    }

    class Subject {
        - subjectId:String
        - studentId:String
        - professorId:String
        - subjectName:String
        - score:int
        - grade:String
        + 과목조회():Subject
        - 학점자동계산(score:int):String
    }

    %% 관계 및 다중도 설정
    %% 학생은 3~5개의 과목을 수강, 과목은 30~35명의 학생을 수용
    Student "30..35" -- "3..5" Subject : 수강신청/학점조회
    
    %% 교수는 1~3개의 과목을 관리, 과목은 1명의 교수에 의해 관리됨
    Professor "1" -- "1..3" Subject : 과목등록/점수입력