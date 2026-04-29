```mermaid

graph LR
    subgraph "학사관리 시스템 (LMS)"
        %% 공통 및 관리 기능
        UC_S_Reg["학생 등록"]
        UC_S_Search["학생 조회"]
        UC_S_Auth["학생 인증"]
        
        UC_P_Reg["교수 등록"]
        UC_P_Search["교수 조회"]
        UC_P_Auth["교수 인증"]

        %% 교수 전용 기능
        UC_C_Reg["과목 등록"]
        UC_Score_In["과목 점수 입력"]
        
        %% 학생 전용 기능
        UC_Enroll["수강 신청"]
        UC_Grade_View["학점 조회"]
        
        %% 공통 기능
        UC_C_Search["과목 조회"]
    end

    %% 액터 설정
    Student((학생))
    Professor((교수))

    %% 학생 연결 관계
    Student --> UC_S_Reg
    Student --> UC_S_Search
    Student --> UC_S_Auth
    Student --> UC_Enroll
    Student --> UC_Grade_View
    Student --> UC_C_Search

    %% 교수 연결 관계
    Professor --> UC_P_Reg
    Professor --> UC_P_Search
    Professor --> UC_P_Auth
    Professor --> UC_C_Reg
    Professor --> UC_Score_In
    Professor --> UC_C_Search

    %% 포함(Include) 관계 설정 (인증 후 이용 가능 조건)
    UC_C_Reg -.->|include| UC_P_Auth
    UC_Score_In -.->|include| UC_P_Auth
    UC_Enroll -.->|include| UC_S_Auth
    UC_Grade_View -.->|include| UC_S_Auth