---

layout: single

title: "프로그래머스) day 4 기초 코딩"

categories: coding

tag: [blog, 프로그래머스]

toc: true

---

# n의 배수

```java
class Solution {
    public int solution(int num, int n) {
        int answer = 0;
        if(num % n == 0){
            answer = 1;
        }else
            answer = 0;
        
        return answer;
    }
}
```

다른 사람 풀이

```java
class Solution {
    public int solution(int num, int n) {
        int answer = num % n == 0 ? 1 : 0;
        return answer;
    }
}
```

if 문을 안쓰고 삼황 연산자 사

```java
condition ? value_if_true : value_if_false
```

condition(조건)이  ture일때 앞에꺼를 출력 flase일떄 뒤에꺼를 출력

# 공배수

```java
class Solution {
    public int solution(int number, int n, int m) {
        int answer = number % n == 0 && number % m == 0 ? 1 : 0;
        return answer;
    }
}
```

삼황연산자 사용해서 한줄로 끝냈다.

# 홀짝에 따라 다른 값 반환하기

```java
class Solution {
    public int solution(int n) {
        int answer = 0;
        if(n % 2 == 1 ){
            for(int i = 1; i <= n; i++){
                if(i % 2 == 1){
                    answer += i;
                }
                
            }
        }else{
            for(int i = 1; i<= n; i++){
                if(i % 2 == 0){
                    answer += i * i;
                }
            }
        }
        return answer;
    }
}
```



# 조건 문자열

```java
class Solution {
    public int solution(String ineq, String eq, int n, int m) {
        int answer = 0;
        boolean result = false;
        if (ineq.equals("<") && eq.equals("=")) {
            result = n <= m;
        } else if (ineq.equals("<") && eq.equals("!")) {
            result = n < m;
        } else if (ineq.equals(">") && eq.equals("=")) {
            result = n >= m;
        } else if (ineq.equals(">") && eq.equals("!")) {
            result = n > m;
        }
        
        if(result == false){
            answer = 0;
        }else
            answer = 1;
        
        return answer;
    }
}
```

# flag에 따라 다른 값 반환하기

```java
class Solution {
    public int solution(int a, int b, boolean flag) {
        int answer = 0;
        int d = (b*-1);
        if(flag){
            answer = a+b;
        }else
            answer = a - b;

        return answer;
    }
}
```

