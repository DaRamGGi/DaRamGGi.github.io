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

# 등차수열의 특정한 항만 더하기

```java
class Solution {
    public int solution(int a, int d, boolean[] included) {
        int answer = 0;
        for(int i = 0; i < included.length; i++){
            if(included[i] == true){
                answer += a;
            }
            a += d;
        }
        return answer;
    }
}
```

# 주사위 게임

```java
class Solution {
    public int solution(int a, int b, int c) {
        int answer = 0;
        if(a == b && b == c){
            answer += (a+b+c) * ((a*a)+(b*b)+(c*c)) * ((a*a*a)+(b*b*b)+(c*c*c));
        }else if(
            (a == b && a != c) ||
            (b == c && a != b) ||
            (c == a && b != c)){
            answer += (a+b+c) * ((a*a)+(b*b)+(c*c));
        }else if(a != b && a != b && c != b){
            answer += (a+b+c);
        }
        return answer;
    }
}
```

# 원소들의 곱과 합

```java
class Solution {
    public int solution(int[] num_list) {
        int answer = 0;
        int answer2 = 0;
        int answer3 = 1;

        for(int i = 0; i < num_list.length; i++){
            answer2 += num_list[i];
            answer3 *= num_list[i];
        }
        answer2 = (answer2 * answer2);
        if(answer2 > answer3){
            answer = 1; 
        }else
        answer = 0;
        return answer;
    }
}
```



# 이어 붙인 수

```java
class Solution {
    public int solution(int[] num_list) {
        int answer = 0;
        String a = "";
        String b = "";
        for(int i = 0; i < num_list.length; i++){
            if(num_list[i] % 2 == 0){
                a += String.valueOf(num_list[i]);
            }else{
                b += String.valueOf(num_list[i]);
            }
        }
        int d = Integer.parseInt(a);
        int q = Integer.parseInt(b);
        answer = (d+q);
        return answer;
    }
}
```

