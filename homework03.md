<hr>
1. Scanner를 사용하여 6개의 데이터를 입력 받고, 이들을 nums 배열에 저장

2. 입력 받은 값 중, 20 이상 100 이하인 원소만 출력

3. 입력 받은 값 중, 최댓값과 최솟값을 출력
<pre>
// int max = nums[0];
// int min = nums[0];
// (for문 사용)
// System.out.println("최댓값 : " + max);
// System.out.println("최댓값 : " + min);
</pre>

4. 오름차순(작은->큰)으로 정렬하여 모든 원소를 출력  ==> 버블 정렬 알고리즘 검색해서 ... 


<hr>

'''
package day08.homwork;

import java.util.Scanner;

public class Test03 {

	public static void main(String[] args) {
		
		Scanner sc = new Scanner(System.in);
		
		int nums[] = new int[6];
		
		for(int i = 0; i < nums.length; ++i) { //Scanner를 사용하여 6개의 데이터를 입력 받고, 이들을 nums 배열에 저장s
			
			System.out.print("[" + i + "] 번째 배열 입력 : ");
			nums[i] = sc.nextInt();
			
						
		}
		
		System.out.print("\n입력한 값 중 20 이상 100 이하인 수 : \n");
		
		
		for(int i = 0; i < nums.length; ++i) { //입력 받은 값 중, 20 이상 100 이하인 원소만 출력
			
			if(nums[i] >= 20 && nums[i] <= 100) {
				
				System.out.println(nums[i] + " ");
			}
			
		}
		
		int max = nums[0];
		int min = nums[0];
		
		for(int i = 1; i < nums.length; ++i) { //최댓값 최솟값 비교 
			
			if(max < nums[i]) {
				
				max = nums[i];
			}
			if(min > nums[i]) {
				
				min = nums[i];
			}
			
		}
		System.out.println("최댓값 : " + max + "   최솟값 : " + min);
		
		
		
		
		/////////////////버블 정렬////////////////////
		
		int b;
		
		for(int i = 0; i<nums.length; ++i) {
			for(int j = 0; j< nums.length; ++j) {
				
				if(nums[j] > nums[j+1]) {
					
					b = nums[j];
					nums[j] = nums[j+1];
					nums[j+1] = b;
					
				}				
				
			}
		}
		
		for(int i = 0; i < nums.length; ++i) {
			
			System.out.println(nums[i]); 
			
		}
		
		////////////////////////////////////////////
		
		
		
		
		

	}

}

'''

