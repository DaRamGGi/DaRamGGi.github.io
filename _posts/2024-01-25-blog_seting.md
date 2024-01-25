---

layout: single

title:  "깃허브 블로그 셋팅"

---



# minimal-mistakes를 토대로 블로그 기본 설정 하기



대부분의 설정은 [Configuration - Minimal Mistakes (mmistakes.github.io)](https://mmistakes.github.io/minimal-mistakes/docs/configuration/) 여기서 찾아 설정값들을 바꿀수있다.



1. 깃허브 블로그 파일 (예:DaRamGGi.github.io)디텍토리 안에 있는 "_config.yml"에서 기본적인 블로그 설정을 바꿀수있다.
   

2. locale          : "ko-KR"  // 블로그의 언어를 바꿀수있다. (기존 영어에서 한글로)
   
   
   title           : "나만의 블로그" // 타이틀 변경
   

   title_separator      : "|" // "(들어간 게시글 타이틀 ) | (블로그 타이틀)"
   
   
   subtitle         : "small positive action" // 서브  타이틀
   

   name           : "Jae Hwan" //작성자
   
   
   description        : "재환의 블로그 입니다." // 블로그 소개글
   
   
   url            : "https://DaRamGGi.github.io" // 블로그  URL
   
   
3. 로컬로 블로그 확인할때 POWER SELL 에서 CTRL+C 누른후 Y로 종료후 다시 서버를 실행하면 바로 확인가능하다.
   

4. 네비게이션 메뉴 : BREADCRUMBS 를 TURE로 바꿔준다(기본: FALSE)
   

5. 블로그 작성일 표기 :  #Defaults -> values -> show_date :true새로 작성
   

6. 연도표시 : date_format: "%y-%m-%d" 를 새롭게 추가한다.