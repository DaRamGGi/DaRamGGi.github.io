---

layout: single

title: "프로그래머스) day 3 기초 코딩"

categories: coding

tag: [blog, 프로그래머스]

toc: true

---

# 문자열 섞기

```java
class Solution {
    public String solution(String str1, String str2) {
        int x = str1.length() + str2.length();
        System.out.println(x);
        char[] arr = new char[x];
        int y = 0;

        for(int i = 0; i < x; i++){
            arr[i] = str1.charAt(y);
            i++;
            arr[i] = str2.charAt(y);
            y++;
        }
        String answer = new String(arr);
        return answer;
    }
}
```

# 더 크게 합치기

```java
class Solution {
    public int solution(int a, int b) {
        int answer = 0;
        String e = String.valueOf(a);
        String r = String.valueOf(b);
        String c = (e+r);
        int q = Integer.parseInt(c);
        String d = (r+e);
        int w = Integer.parseInt(d);
        if(q < w){
            answer = w;
        }else
            answer = q;
        
        return answer;
    }
}
```

다른 사람 풀이

```java
class Solution {
    public int solution(int a, int b) {
        return Math.max(Integer.parseInt(a + "" + b), Integer.parseInt(b + "" + a));
    }
}
```

JAVA는  "" 이 포함되어 있을경우 String type으로 입력된다.

# 두 수의 연산값 비교하기

```java
class Solution {
    public int solution(int a, int b) {
        
        String c = (a + "" + b);
        int d = (2 * a * b);
        
        return Math.max(Integer.parseInt(c) , d);
    }
}
```

