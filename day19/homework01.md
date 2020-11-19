```java
package day18.homework;
/*
 * 1. 깊은 복사와 얕은 복사 조사하기 
 */
class Person implements Cloneable {
	
	String name;
	int age;
	Person father;
	Person mother;
	
	Person(String name, int age){
		
	}
	// clone() / copy()
	
	public Person clone() {
		Person p = new Person(name, age);
		p.father = father;
		p.mother = mother;
		return p;
	}
	
}
public class Test04 {
	public static void main(String[] args) {
		// 할아버지 : 홍길동 70세
		// 할머니 : 김피카츄 65세
		
		// 어머니 : 김피츄 35세 
		// 아버지 : 홍또도가스 40세
		
		// 아들 : 홍뚜벅초 10세 
		// 딸 : 홍푸린 5세 
		
		// 동일한 어머니, 아버지를 둔 뚜벅초, 푸린 생성 할 때 
		Person grandfatherPerson = new Person("홍길동", 70);
		Person grandmotherPerson = new Person("김피카츄", 65);
		
		Person fatherPerson = new Person("홍또도가스" , 40);
		fatherPerson.father = grandfatherPerson;
		fatherPerson.mother = grandmotherPerson;
		
		Person motherPerson = new Person("김피츄", 35);
		
		Person son = new Person("홍뚜벅초", 10); 
		son.father = fatherPerson;
		son.mother = motherPerson;
		
		Person daughter = new Person("홍푸린" , 5);
		daughter.father = son.father;
		daughter.mother = son.mother;
		
		
		
		Person dauther = son.clone();
		daughter.name = "홍푸린";
			
		
		
		
		
		
		// 푸린(동생) 객체를 생성할 때 깊은 복사를 해야하는지 얕은 복사를 해야하는지 생각해보고 
		// 푸린 객체는 뚜벅초 객체를 복사하여 구현하세요. (아버지, 어머니가 뚜벅초와 같아야 함)
		
		// 오류 수정 
	}
}






```
