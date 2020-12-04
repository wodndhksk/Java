```java
package day29.homework;

import java.awt.BorderLayout;
import java.awt.Button;
import java.awt.Color;
import java.awt.Desktop.Action;
import java.awt.Dimension;
import java.awt.GridLayout;
import java.awt.Label;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;
import javax.swing.JTextArea;
import javax.swing.JTextField;

/*
 *  저장하기 누르면 현재선택한 메뉴만 텍스트 파일로 담기기 (저장) 
 *  현재 시간 넣기 
 *  총 결제액 넣기 
 *  불러오기 : JfileChooser  or File.listFiles()
 *  삭제하기 : 선택한 메뉴, 총 결제액 삭제 
 *  오른쪽 하단에 현재 시간 흐름 표시
 *  
 * 
 */

class MyButton extends JButton {
	
	
	private String menuName;
	private int price;	
//	JButton btn1;
//	JTextArea text;
	//Listener listener = new Listener();
	
	public MyButton(String menuName, int price) {
		
		
		this.menuName = menuName;
		this.price = price;
		
//		this.btn1 = new JButton(this.menuName);
//		this.text = new JTextArea(Integer.toString(this.price));
		
	}
	public String getMenuName() {
		return menuName;
	}

	public void setMenuName(String menuName) {
		this.menuName = menuName;
	}

	public int getPrice() {
		return price;
	}

	public void setPrice(int price) {
		this.price = price;
	}
}



public class Homework1 extends JFrame {
	
	MyButton myButton1, myButton2, myButton3, myButton4, myButton5;
	Button button1, button2, button3, button4, button5;
//	Listener listener = new Listener();
//	JTextArea textArea = new JTextArea(10,1);
	//JTextField text1, text2, text3, text4, text5;
	
	
	
//	class Listener implements ActionListener{
//
//		@Override
//		public void actionPerformed(ActionEvent e) {
//			
//		if(e.equals(button1.getName())) { //button.getName()인 "아메리카노" 가 눌렸으면
//			textArea.setText(myButton1.getMenuName());
//			textArea.setText(Integer.toString(myButton1.getPrice()));
//			System.out.println("저장됨!");
//		}
//			
//		
//		
//		}
//		
//	}
	
	public void panelWest() {
		JPanel panelWest = new JPanel();
		
		panelWest.setBackground(Color.blue);
//		JTextField textField = new JTextField();
		
		// 버튼 이름 담기
		this.button1 = new Button("아메리카노");
		this.button2 = new Button("카페라떼");
		this.button3 = new Button("카푸치노");
		this.button4 = new Button("바닐라 라떼");
		this.button5 = new Button("카라멜 마끼야또");
		
		// MyButton 클래스 생성자에 메뉴이름과 가격 담기 
		myButton1 = new MyButton(button1.getName(), 4000);
		myButton2 = new MyButton(button2.getName(), 4500);
		myButton3 = new MyButton(button3.getName(), 4500);
		myButton4 = new MyButton(button4.getName(), 5000);
		myButton5 = new MyButton(button5.getName(), 6000);
		// 이벤트 버튼객체 등록 
//		button1.addActionListener(listener);
//		button2.addActionListener(listener);
//		button3.addActionListener(listener);
//		button4.addActionListener(listener);
//		button5.addActionListener(listener);
		
		
		
		panelWest.setLayout(new GridLayout(5,1,10,10)); //GridLayout(행, 열, 간격, 간격)
		panelWest.add(button1);
		panelWest.add(button2);
		panelWest.add(button3);
		panelWest.add(button4);
		panelWest.add(button5);
		
		
		
		add(panelWest, BorderLayout.WEST);
		
	}
	
	public void panelNorth() {  // 좌측 panel 메서드 
		JPanel panelNorth = new JPanel();
		panelNorth.setBackground(Color.GREEN);
		panelNorth.setLayout(new GridLayout(1,3,10,10)); //GridLayout(행, 열, 간격, 간격)
		panelNorth.add(new JButton("저장하기"));
		panelNorth.add(new JButton("불러오기"));
		panelNorth.add(new JButton("결제하기"));
		
		add(panelNorth, BorderLayout.NORTH);
		
	}
	
	public void panelCenter() {  //중앙 panel 메서드 
		JTextArea textArea = new JTextArea(10,1);
		textArea.setAlignmentX(CENTER_ALIGNMENT);
		Label label = new Label();
		label.setAlignment((int) CENTER_ALIGNMENT);
//		JTextArea textArea = new JTextArea(10,1);
		JPanel panelCenter = new JPanel();
		panelCenter.setBackground(Color.lightGray);
		panelCenter.setLayout(new GridLayout(10,1,10,10)); //GridLayout(행, 열, 간격, 간격)
		
		button1.addActionListener(new ActionListener() {
			
			@Override
			public void actionPerformed(ActionEvent arg0) {
				label.setText(myButton1.getMenuName());
				System.out.println("아메리카노 저장함 ");
				
			}
		});
		
		
//		textArea.getText(myButton1.getMenuName());
//		textArea.getText(Integer.toString(myButton1.getPrice()));
//		
//		textArea.setText(myButton2.getMenuName());
//		textArea.setText(Integer.toString(myButton2.getPrice()));
//		
//		textArea.setText(myButton3.getMenuName());
//		textArea.setText(Integer.toString(myButton3.getPrice()));
//		
//		textArea.setText(myButton4.getMenuName());
//		textArea.setText(Integer.toString(myButton4.getPrice()));
//		
//		textArea.setText(myButton5.getMenuName());
//		textArea.setText(Integer.toString(myButton5.getPrice()));
		
		
		add(panelCenter, BorderLayout.CENTER);
		
	}
	
	public void panelSouth() { // 하단부 panel 메서드 
		
	}
	

	public Homework1() {

		super("커피 자판기 ");  //JFrame 이름 
		
		setSize(new Dimension(1200,800)); // 1200 X 800 크기 
		setLocation(400,200);
		
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); // 창 닫으면 빌드 종료
		panelWest();
		panelNorth();
		panelCenter();
		
		setVisible(true);
	}
	
	
	
	public static void main(String[] args) {
		
		new Homework1();

	}

}

```
