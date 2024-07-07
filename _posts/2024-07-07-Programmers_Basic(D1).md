---

layout: single

title: "프로그래머스) day 1 기초 코"

categories: coding

tag: [blog, 백준]

toc: true

---

# 대소문자 출력

```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String a = sc.next();
        String x = "";
        
        for(int i = 0; i < a.length(); i++){
            int tmp = (int)a.charAt(i);
            if( (65 <= tmp) && (tmp <= 90)){
                x += (char)(tmp + 32);
            }else if((97 <= tmp) && (tmp <= 122)){
                x +=(char)(tmp - 32);
            }else{
                x += (char)tmp;
            }
        }
        System.out.println(x);
    }
}
```

받은 글자들을 아스키코드 char로 변환후에 소문자일시 대문자 아스키코드로 낮추고

대문자 아스키 코드로 높인디.

# 특수문자 출력하기

```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        String specialChars = "!@#$%^&*(\\'\"<>?:;";
        System.out.println(specialChars);
    }
}
```



