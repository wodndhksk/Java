## 문제
```
https://programmers.co.kr/learn/courses/30/lessons/77484#
```
```java

import java.util.*;
public class Pgs42576 {


    class Solution {
        public int[] solution(int[] lottos, int[] win_nums) {

            int count = 0;
            int sameIndex = 0;

            // 0 갯수 파악
            for(int i=0; i<lottos.length; i++){
                if(lottos[i] == 0){
                    count +=1;

                }
            }

            // Arrays.sort(lottos);
            // Arrays.sort(win_nums);

            for(int i =0; i<lottos.length; i++){
                for(int j = 0; j < win_nums.length; j++){
                    if(lottos[i] == win_nums[j]){
                        sameIndex += 1;
                    }
                }
            }
            // 등수는 맞춘 갯수를 7로 빼면 된다.
            // maxNum 은 0 이 다 맞을 경우 minNum 은 0이 다 틀릴경우이다.
            int maxNum = count + sameIndex;
            int minNum = sameIndex;

            if(count == 0 && sameIndex == 0){ // 둘다 = 0 인 조건문을 가장 먼저 두지 않을시 아래 조건문에 포함되어 버림(둘중 하나만 0인 조건에)
                int[] answer = {6, 6};
                return answer;
            }
            else if(sameIndex == 0){
                int[] answer = {7-maxNum, 7-1};
                return answer;
            }
            else if(count == 0){
                int[] answer = {7-maxNum, 7-minNum};
                return answer;
            }
            else{
                int[] answer = {7-maxNum, 7-minNum};
                return answer;
            }

        }
    }
    public static void main(String[] args) {


    }
}
```
