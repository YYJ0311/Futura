```
채용공고 리스트 조회!
sql 쿼리문에서 사용하는 id = getArtlListMainRecruitType2
getArtlListMainRecruitType2 이 사용된 곳 
	1. home.xml(쿼리문 작성한 곳)
	2. homeDAO.java(인터페이스)
	3. homeDAOImpl.java(AbstractDAO와 homeDAO 모두 상속받은 클래스)
		getArtlListMainRecruitType2을 호출

HomeController = 채용공고를 가져오는 주소를 가진 컨트롤러
/home/ajaxRecruit 주소를 요청받으면
	1. main이라는 HashMap을 새로 만들어서 top_menu_id, bbs_uniq_id, rownumStartNumber, rownumEndNumber 를 key로 하는 데이터를 main에 넣어준다
    2. homeDao의 getArtlListMainRecruit에 main 데이터를 넣어서 새로 만든 list(recruitList)에 넣어준다
    3. list를 다시 JSONObject에 넣어준다
    4. list가 null이 아니라면 새로 만든 JSONObject에 recruitListCnt를 key, list의 크기를 value로 해서 넣어준다
    5. JSONObject 리턴
    => 오브젝트에 list의 크기만 담아서 넘겨줌

위 과정은 보도자료, 공지사항, 채용공고, 입찰공고 리스트 크기 구하는데 모두 사용됨
그리고 index.jsp에서 ajax로 정보를 불러오는데 사용됨

index.jsp에서는 오늘 날짜와 비교해서 접수중 또는 접수마감 상태를 정하고, 
```