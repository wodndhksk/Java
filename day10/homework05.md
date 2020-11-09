```java
package day09.homework;

//중-3: "김", "이", "박", "최", "한" 등의 대한민국 성씨를 저장할 배열을 만들고, 성씨들을 저장하세요.
//"피카츄", "라이츄", "파이리", "꼬부기", "버터풀", "야도란", "피죤투" 를 저장할 배열을 만들고 이름들을 저장하세요.
//1) 총 10개의 성+이름 조합을 출력하세요. ( Math.random()을 사용하며, 중복 조합을 허용합니다)
//2) 조합가능한 모든 이름을 출력하세요.



public class Test05 {

	public static void main(String[] args) {
		
		String lastName[] = {"김", "이", "박", "최", "한"}; 
		
		String firstName[] = {"피카츄", "라이츄", "파이리", "꼬부기", "버터풀", "야도란", "피죤투"};
		
		int l, f;
		
		// 1)
		for(int i=0; i< 10; i++) {
		l = (int) Math.floor(Math.random()*4+1);
		f = (int) Math.floor(Math.random()*6+1);
		
		System.out.println(lastName[l] +" "+ firstName[f]);
		
		}
		
		
		
		
		// 2)
		for(int i = 0; i < lastName.length; i++) {
			
			for(int j = 0; j< firstName.length; j++)	{
				
				System.out.println(lastName[i] +firstName[j]);
				
			}
				
		
		}
		
		
		
		
		
		
		

	}

}
```
