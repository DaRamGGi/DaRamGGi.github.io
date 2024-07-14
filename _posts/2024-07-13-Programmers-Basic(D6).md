---

layout: single

title: "프로그래머스 day6 기초 문제"

categories: coding

tag: [blog, 백준]

toc: true

---

# 마지막 두 원소

```java
class Solution {
    public int[] solution(int[] num_list) {
        
        int length = num_list.length;

        int last_num = num_list[length - 1];

        int second_last_num = num_list[length-2];

        int num = 0;

        if(last_num > second_last_num){
            num = (last_num - second_last_num);
        }else{
            num = (last_num * 2);
        }

        int[] answer = new int[num_list.length + 1];
        for(int i = 0; i < num_list.length; i++){
            answer[i] = num_list[i];
        }
        answer[answer.length - 1] = num;
        return answer;
    }
}
```

# 수 조작하기1

```java
class Solution {
    public int solution(int n, String control) {
        int answer = 0;
        char[] chararr = control.toCharArray();

        for(int i = 0; i < chararr.length; i++){
            if(chararr[i] == 'w'){
                n += 1;
            }else if(chararr[i] == 's'){
                n += -1;
            }else if(chararr[i] == 'd'){
                n += 10;
            }else if(chararr[i] == 'a'){
                n += -10;
            }
        }
        answer = n;
        return answer;
    }
}
```

# 수 조작하기2

```java
class Solution {
    public String solution(int[] numLog) {
        String answer = "";
        char[] answer1 = new char[numLog.length-1];
        
        
        for(int i = 1; i < numLog.length; i++){
            int difference = (numLog[i] - numLog[i-1]);
            if(difference == 1){
                answer1[i-1] = 'w';
            }else if(difference == -1){
                answer1[i-1] = 's';
            }else if(difference == 10){
                answer1[i-1] = 'd';
            }else if(difference == -10){
                answer1[i-1] = 'a';
            }
        }
        for(int i = 0; i < answer1.length;i++){
            answer += answer1[i];
        }
        return answer;
    }
}
```

# 수열과 구간 쿼리 3

```java
import java.util.Arrays;

public class Solution {
    public static void main(String[] args) {
        int[] arr = {0, 1, 2, 3, 4};
        int[][] queries = {{0, 3}, {1, 2}, {1, 4}};

        int[] answer = solution(arr, queries);

        System.out.println(Arrays.toString(answer));
    }

    public static int[] solution(int[] arr, int[][] queries){
        for(int[] query : queries){
            int i = query[0];
            int j = query[1];

            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
        }
        return arr;
    }
}
```

# 수열과 구간 쿼리2

```java
class Solution {
    public int[] solution(int[] arr, int[][] queries) {
        int[] answer = new int [queries.length];
        for (int i = 0; i < queries.length; i++) {
            int s = queries[i][0];
            int e = queries[i][1];
            int k = queries[i][2];
            int minValue = Integer.MAX_VALUE;
            boolean found = false;
            
            for (int j = s; j <= e; j++) {
                if (arr[j] > k && arr[j] < minValue) {
                    minValue = arr[j];
                    found = true;
                }
            }
            
            if (found) {
                answer[i] = minValue;
            } else {
                answer[i] = -1;
            }
        }
        return answer;
    }
}
```

`