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

