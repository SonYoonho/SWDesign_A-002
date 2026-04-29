```mermaid

classDiagram
    direction TB

    class Student {
        -String 학번
        -String 암호
        -String 성명
        +학생등록() boolean
        +학생조회() Student
        +학생인증(암호 String) boolean
        +수강신청(과목id String) boolean
        +학점조회(과목id String) String
    }

    class Professor {
        -String 교수id
        -String 암호
        -String 성명
        +교수등록() boolean
        +교수조회() Professor
        +교수인증(암호 String) boolean
        +과목등록(과목명 String) boolean
        +과목점수입력(과목id String, 학번 String, 과목점수 int) String
    }

    class Course {
        -String 과목id
        -String 학번
        -String 교수id
        -String 과목명
        -int 과목점수
        -String 학점
        +과목조회() Course
        +점수저장_및_학점반환(과목점수 int) String
        -학점계산(과목점수 int) String
    }

    %% 관계 및 다중성 (Multiplicity) 정의
    Professor 1 -- 1..3 Course  등록 및 관리
    Student 30..35 -- 3..5 Course  수강신청