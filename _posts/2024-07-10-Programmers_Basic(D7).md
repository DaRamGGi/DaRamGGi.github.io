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

마지막 숫자와 마지막 전숫자를 담을 int를 만들고 if문으로 마지막 전숫자가 클시 "-"를 하여 구분해서 아닐시에는 "*2"를 하였다

이후 answer배열에는 num_list의 배열의 수 +1을 증가시켜 마지막 num값을 넣을 공간을 만들어 주었고 

for문으로 num_list를 먼저 넣고 이후 num을 마지막에 넣어 주었다.



# 수 조작하기 1

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

다른 사람 풀이

```java
class Solution {
    public int solution(int n, String control) {
        int answer = n;

        for(char ch : control.toCharArray()) {
            switch(ch) {
                case 'w': answer += 1; break;
                case 's': answer -= 1; break;
                case 'd': answer += 10; break;
                case 'a': answer -= 10; break;
                default:break;
            }
        }

        return answer;
    }
}
```

따로 char 배열을 안만들고 이런식으로 하는 법이 있다.



# 수 조작하기 2

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

numlog의 경우 배열의 수중 첫번쨰의 값 0 이 문자를 출력하기 전이라해당 배열을 빼서 answer배열에는 -1 을 주었다.

for문은 첫번째 0부터 시작 하면 계산이 힘들어 져서 1부터 시작하여 뒤에 숫자 i-1에 기존 i-(i-1)을 비교하여 나온 값들을 if문으로 주었고

answer에 들어가는 값들을 i-1로하여 배열값0부터 들어가게 만들었다.

# 수열과 구간 쿼리 3

해당 문제는 20분정도 고민후 어떻게해야할지 감이 안잡혀서 구글링 해서 찾았다.

```java
import java.util.Arrays;

class Solution {
    public int[] solution(int[] arr, int[][] queries) {
        int[] answer = Arrays.copyOf(arr, arr.length);

        for (int[] query : queries) {
            int i = query[0];
            int j = query[1];

            int temp = answer[i];
            answer[i] = answer[j];
            answer[j] = temp;
        }

        return answer;
    }
}
```

Arrays.copyOf 메서드를 사용하여 arr의 배열 사본을 만듬

즉 answer은 arr의 값을 가진다라는 뜻임



for (int[] query : queries)

queries배열 수 만큼 반복하고

i,j는 그안의 값들 이다.



int temp = answer[i]

i와 j의 위치를 바꿀꺼미 우선 i의 값을 temp에 저장

answer[i] = answer[j];

이제 i의 값을 j 로 바꿔줌

answer[j] = temp;

아까 i의 값을 저장해둔 temp를 

j의 값을 temp로 바꿔줌

# 수열과 구간 쿼리 2

해당 문제도 20분 이상 고민 했지만 답이 나오지 않아 다시 구글링을 했다.

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



int minValue = Integer.MAX_VALUE;

해당 함수는 k보다 크면서 가장 작은 값을 저장할 변수

배열의 값을 비교할때 항상 첫번째로 찾은 유요한 값이 minvalue에 저장 된다고 한다.



boolean found = false;

찾은 값이 유요한 값인지 를 확인하는 변수



for (int j = s; j <= e; j++)

s,e내에서 배열 arr의 모든 요소를 순회하기 위해 사용 된다.



if (arr[j] > k && arr[j] < minValue) {

k보다 크면서 minvalue보다 작은 값을 찾는다

mainvalue의 기본값은 max_value이기 때문에 최대 값을 가지고있어서

첫번째 조건만 만족하면 그 아래 코드를 실행해서

minValue = arr[j];

이렇게 j의 값을 넣는다



if (found) {
    answer[i] = minValue;
} else {
    answer[i] = -1;
}

해당 코드는 최종 결과 값들을 answer[i]배열에 넣는 값이다

ture가 나왔을떄는 i에 minvalue값을 넣고

flase가 나오면 -1 의 값을 넣는다









