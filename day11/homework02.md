```java
package day11.quiz;

public class Test01 {

	public static void main(String[] args) {
		
		FunctionFactory myFac = new FunctionFactory();
		
		String s = myFac.strGugudan(5);
		
		System.out.println(s);
		
		System.out.println(myFac.strGugudan(4));
		
		
		int[] b = {10, 2, 4, 6, 2, 100, 15};
		System.out.println(myFac.getMax(b));
		
		
		System.out.println(myFac.getMax(new int[] {10, 2, 4, 6, 2, 100, 15}));
		
		System.out.println(myFac.getRandomPokemon());

	}

}
```
