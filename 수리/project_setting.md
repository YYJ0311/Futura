# 다운로드
egov 검색, 다운로드 - 개발환경 - 3.x 다운로드 - 개발자용 64비트 다운로드
jdk 1.7 / 1.8, tomcat 7.0 / 8.5 설치 후 각각 jdk, tomcat 폴더 안에 압축 풀어서 넣어 놓음
    => 프로젝트마다 버전을 바꿔가며 사용하기 위함

# setting
    1. 하드디스크 따로 할당해서 egov 넣고 jdk, tomcat, maven 폴더 생성
    2. jdk와 tomcat에 다운로드 받은 파일 압축해체해서 넣기
    3. maven 폴더에 svn에서 공유받은 settings_nims.xml 파일 넣고 같은 위치에 프로젝트 저장소폴더(nims_repository) 생성
        (svn 연결 : win + r로 실행창 - mstsc(원격 데스크탑 연결) - svn 아이피 입력해서 접속)
    4. settings_nims.xml 파일 열어서 localRepository에 프로젝트 저장소 경로 입력 (D:\maven\nims_repository)
    5. egov 폴더 안에 workspace 폴더 생성하고 그 안에 프로젝트별 workspace 생성(nims_workspace)
    6. egov 실행해서 바로 위에 만든 workspace 불러옴(프로젝트 별로 다르게 불러와야 톰캣을 나눠서 사용 가능)

    7. 이클립스 Window > Preferences > Maven > user settings > xml 경로설정
        setting 파일 설정하면 이클립스가 읽으면서 maven 내 저장소 폴더 자동으로 잡아줌
    8. window - show view - others - svn repositories로 svn 저장소 창 띄우기
        8-1. new repository location - 경로, user, password 입력하고 finish해서 svn 불러오기
    9. svn 폴더(경로 말고 폴더명으로 적힌 것) 오른쪽 클릭 checkout
        => 로컬 workspace에 svn 파일 생성됨
    10. server 탭에서 new > apache > tomcat 버전 선택 > 톰캣 경로 입력 (bin 폴더가 있는 폴더로 선택함) > 프로젝트 add > finish
    11. pom.xml에 오류 생긴 dependency jar파일을 폴더 안에 새로 넣어주고 project update
        order and export에서 jdk와 tomcat 차례로 폴더 아래 최상단으로 올리기
    12. 프로젝트 properties > Java build path > Libraries 에서 jdk 삭제 후 새로 add
    13. java compiler, project facets에서 자바 버전 확인
    14. java build path에서 web app libraries 추가하기(update project하면 사라지기 때문에 새로 추가해야 함)
    15. egov_cms에서 톰캣 더블클릭해서 modules에서 path "/" 로 수정
        이유) server.xml 파일에서 context path와 같게 맞춤
    16. 톰캣 포트번호 안겹치게 수정
        admin : 기본설정 포트, HTTP : 내부 접속용 포트, AJP : apache 서비스와 통신하는 포트
        두개 이상의 서버를 구동할 경우 3개의 포트번호를 모두 바꿔줘야 함
    17. run

    * 만약 jdk 버전이 초기화되면 pom.xml에서 maven-compiler-plugin 항목에 버전 확인하고 수정하기
    * server를 지우고 나면 window - preference - server - runtime environments에서 서버 지우기
    * 폴더 선택할 땐 항상 안에 필요로 하는 파일이 있는 폴더인지 확인하기