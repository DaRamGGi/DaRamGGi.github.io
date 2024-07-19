---

layout: single

title: "프로그래머스 day8 기초 문제"

categories: coding

tag: [blog, 프로그래머스]

toc: true

---

# 수열과 구간 쿼리 4

```java
class Solution {
    public int[] solution(int[] arr, int[][] queries) {
        int[] answer = {};
        for(int[] query : queries){
            int s = query[0];
            int e = query[1];
            int k = query[2];

            for(int i = s; i <= e; i++){
                if(i % k == 0){
                    arr[i] += 1;
                }
            }
        }
        answer = arr;
        return answer;
    }
}
```

