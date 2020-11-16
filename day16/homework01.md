```java
package day16.homework;
/*
 * < Sniper VS Tank >
 * - 저격수, 탱크 두 캐릭터 중 아무거나 랜덤하게 2개 생성
 *   (탱크 vs 탱크, 저 vs 탱, 저 vs 저)
 * - 두 객체가 서로 죽을 때까지 서로 공격을 반복
 * - 첫번째, 혹은 두번째 플레이어가 이겼는지 마지막 승자 출력! 
 *  e.g. 플레이어1(탱크)의 승리!
 */
class Unit { // 부모 클래스
	String name;
	int hp, att; // 체력, 공격력
	boolean alive; // true:아직 살아있음 (선택사항)
	
	public Unit() {}
	
	public Unit(String name) {
		this.name = name;
	}
	
	public Unit(String name, int hp, int att) {
		this.name = name;
		this.hp = hp;
		this.att = att;
		this.alive = true;
	}
	
	public void attack(Unit enemy) {
		
	}
}


class Sniper extends Unit { // 자식 클래스
	
	Sniper(){};
	// 객체 생성되면, 자동으로 name은 "저격수", hp는 400, att는 100
	
	public Sniper(String name, int hp, int att) {
		super("저격수 ", 400, 100);
		this.alive = true;
		
		
	}
		
		 
	 
	
	// attack 오버라이드 
	// 1. 10% 확률로 헤드샷 (상대 즉사)
	// 2. 나머지 확률로 평타(일반 공격, 상대 hp를 100만큼 깎는다.)
	@Override
	public void attack(Unit enemy) {
		
		
		enemy =(Unit) (Math.random()<0.1 ? this.alive = false : super.hp -100);
	}
}

class Tank extends Unit {
	Tank(){};
	// 객체 생성되면, 자동으로 name은 "탱크", hp는 4000, att는 50
	public Tank(String name, int hp, int att) {
		super("탱크 ", 4000, 50);
		this.alive = true;
	}
	
	// attack 오버라이드 
	// 1. 30% 확률로 상대의 hp 30% 감소
	// 2. 나머지 확률로 평타(일반 공격, 상대 hp를 50만큼 깎는다.)
	@Override
	public void attack(Unit enemy) {
	
		
		enemy = (Unit)(Math.random()< 0.3 ? this.alive = false  : this.hp -50);
	}
}
public class Quiz02 {
	public static void main(String[] args) {
		// 두 타입의 객체를 랜덤하게 2개 생성
		// 무한 반복문을 사용하여 둘 중 하나가 죽을 때까지 서로를 공격
		// 단, 죽은 객체가 공격하면 안됨
		
		Unit arr[]= new Unit[2];// = {new Sniper(),new Tank()};
		
		for(int i = 0; i < arr.length; i++)
			arr[i] = (Unit)(Math.random()<=0.5 ? new Sniper() : new Tank());
		
		while(true) {
			
			arr[0].attack(arr[1]);
			arr[1].attack(arr[0]);
			
			if(arr[0].hp>=0) {
				arr[0].alive = false;
				System.out.println(arr[0].name + " 사망 !! 남은 체력 : " + arr[0].hp );
				break;
			}
			else if(arr[1].hp >=0) {
				arr[1].alive = false;
				System.out.println(arr[1].name + " 사망 !! 남은 체력 : " + arr[0].hp );
				break;
			}
		}
		
		
		
		
		
		
	}
}


```
