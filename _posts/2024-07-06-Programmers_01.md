---

layout: single

title: "프로그래머스)신규 아이디 추천"

categories: coding

tag: [blog, 프로그래머스]

toc: true

---

# 문제 이해하기

아이디와 유사하면서 규칙에 맞는 아이디를 추천해주는 프로그램 만들기

아이디는 3자 이상 15자 이하

아이디는 알파벳 소문자, 숫자, -, _, . 만 가능

단, .는 처음과 끝에 사용할수 없음+ 연속 사용 불가능

New_id

- 다 소문자
- 소문자, 숫자, - ,_ , . 제외한 모든 무자 제거
- 마침표가 두번 이상 연속되면 하나로 치환
- 마침표가 처음이나 끝에 위차하면 제거
- 빈문자열이라면 a 대입
- 길이가 16자 이상이면 15문자를 제외한 나머지 제거,
- 제거후에 마지막 마침표가 . 이면 .제거
- 길이가 2자 이하라면 마지막 문자를 3이 될때까지 반복

### 정답

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;


public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        
        String new_id = br.readLine();
        
        // 1단계 소문자 변환
        new_id = new_id.toLowerCase();
        //1단계 출력
        System.out.println("변환이 되었을까용 : " + new_id);
        //2단계
        new_id = new_id.replaceAll("[^a-z0-9-_.]", "");
        System.out.println(new_id);  
        //3단계 마침표 여러게 있떄 하나로 변환
        new_id = new_id.replaceAll("\\.+", "\\.");
        System.out.println(new_id);
        //4단계 마침표가 처음에 있을때 제거
        //char로 첫번째 인덱스를 불러오고
        //substring으로 1번 문자열부터 시작하면 0번 문자열인 . 이 사라지게된다.
        char firstChar = new_id.charAt(0);
        if(firstChar == '.'){
            new_id = new_id.substring(1);
        }
        //new_id = new_id.replaceFirst("\\.", "");
        System.out.println(new_id);
        //4단계 마침표가 마지막에 있을때 제거
        new_id = new_id.replaceFirst("\\.$", "");
        System.out.println(new_id);
        //5단계 빈문자열
        if (new_id.isEmpty()) {
            new_id = "a";
        }
        System.out.println(new_id);
        //6단계 15자 이상 쳐네기 substring 0부터 15 전까지만 출력
        if(new_id.length() > 15){
            new_id = new_id.substring(0, 15);
        }
        System.out.println(new_id);
        //7단계 제거 후 마침표가 마지막에 있을때  제거
        new_id = new_id.replaceFirst("\\.$", "");
        System.out.println(new_id);

        //8단계 길이가 2자 이하일떄 마지막 문자 를 3이될때까지 반복
        char lastChar = new_id.charAt(new_id.length() - 1);
        if(new_id.length() < 3){
            while(new_id.length() < 3){
                new_id = new_id + lastChar;
            }
        }
     
        
        System.out.println(new_id);

        
    }
}

```

### 해당 문제를 풀며 배워간점

정규식, substring, replace