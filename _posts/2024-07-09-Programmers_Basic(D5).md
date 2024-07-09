---

layout: single

title: "프로그래머스) day 5 기초 코딩"

categories: coding

tag: [blog, 프로그래머스]

toc: true

---

# 코드 처리하기

```java
class Solution {
    public String solution(String code) {
        char[] arr = code.toCharArray();
        int mode = 0;
        String answer = "";
        for(int i = 0; i < code.length(); i++){
            if(arr[i] == '1'){
                int cheng = mode - 1 == 0 ? 0 : 1;
                mode = cheng;
            }
            else if(i % 2 != 0 && mode == 1){
                answer += arr[i];
            }
            else if(i % 2 == 0 && mode == 0){
                
                answer += arr[i];
            }
                
            
        }
        if(answer.isEmpty()){
            answer = "EMPTY";
            return answer;
        }
        else
            return answer;
    }
}
```

