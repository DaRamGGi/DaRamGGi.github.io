---

layout: single

title: "프로그래머스) day 2 기초 코딩"

categories: coding

tag: [blog, 프로그래머스]

toc: true

---

# 덧셈식 출력
```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();
        int b = sc.nextInt();

        System.out.println(a + " + " + b + " = " + (a+b));
    }
}
```

# 문자열 붙여서 출력

```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String a = sc.next();
        String b = sc.next();
        System.out.print(a.replaceAll(" ", ""));
        System.out.print(b.replaceAll(" ", ""));
    }
}
```

replaceAll를 사용해 모든 공백 제거

# 문자열 돌리기

```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String a = sc.next();
        
        for(int i = 0; i < a.length(); i++){
            char c = a.charAt(i);
            System.out.println(c);
        }
    }
}
```

# 홀짝 구분하기

```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        if(n % 2 == 0){
            System.out.println(n + " is even");
        }
        else{
            System.out.println( n + " is odd");
        }
    }
}
```

# 문자열 겹쳐쓰기

```java
class Solution {
    public String solution(String my_string, String overwrite_string, int s) {
        char[] arr = my_string.toCharArray();
        char[] arr2 = overwrite_string.toCharArray();
        int z = 0;
        for(int i = 0; i < overwrite_string.length(); i++){
            arr[s] = arr2[z];
            s++;
            z++;
        }
        String answer = new String(arr);
        return answer;
    }
}
```

다른 사람 풀이

```java
class Solution {
    public String solution(String my_string, String overwrite_string, int s) {
        char[] my_chars = my_string.toCharArray();
        char[] overwrite_chars = overwrite_string.toCharArray();
        for (int i=0; i<overwrite_chars.length; i++) {
            my_chars[s + i] = overwrite_chars[i];
        }
        return String.valueOf(my_chars);
    }
}
```

