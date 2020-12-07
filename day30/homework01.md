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
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.ObjectInputStream;
import java.io.ObjectOutputStream;
import java.text.SimpleDateFormat;

import javax.swing.JButton;
import javax.swing.JFileChooser;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JOptionPane;
import javax.swing.JPanel;
import javax.swing.JTextArea;
import javax.swing.JTextField;
import javax.swing.filechooser.FileNameExtensionFilter;
import javax.swing.plaf.FileChooserUI;



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

	
	public MyButton(String menuName, int price) {	
		
		this.menuName = menuName;
		this.price = price;
		
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
	JButton saveButton, openButton, deleteButton;
	
	JTextArea textArea;
	JTextArea textArea1;
	Listener listener = new Listener();
	int total = 0;
	
	long nano = System.currentTimeMillis();
//	JFileChooser chooser;
	

	
	
	
	class Listener implements ActionListener{

		@Override
		public void actionPerformed(ActionEvent e) {
			
		if(e.getSource() == button1) { //button.getName()인 "아메리카노" 가 눌렸으면
			textArea.append(myButton1.getMenuName()+ " 가격 : "); //textArea 	에 메뉴이름 호출 
			textArea.append(Integer.toString(myButton1.getPrice())+"\t"+new SimpleDateFormat("HH:mm:ss").format(nano)+ "\n"); //textArea 에 메뉴의 가격 호출 
			total += myButton1.getPrice();								// 총 결제액 계산 
			textArea1.setText("총 결제액 : " +Integer.toString(total));	// 총 결제액 호출 
			
			System.out.println("저장됨!");
		}
		else if(e.getSource() == button2) { //button.getName()인 "카페라떼" 가 눌렸으면
			textArea.append(myButton2.getMenuName()+ " 가격 : ");
			textArea.append(Integer.toString(myButton2.getPrice())+ "\t"+new SimpleDateFormat("HH:mm:ss").format(nano)+"\n");
			total += myButton2.getPrice();
			textArea1.setText("총 결제액 : " +Integer.toString(total));
			System.out.println("저장됨!");
		}
		else if(e.getSource() == button3) { //button.getName()인 "카푸치노" 가 눌렸으면
			textArea.append(myButton3.getMenuName()+ " 가격 : ");  
			textArea.append(Integer.toString(myButton3.getPrice())+ "\t"+new SimpleDateFormat("HH:mm:ss").format(nano)+"\n");
			total += myButton3.getPrice();
			textArea1.setText("총 결제액 : " +Integer.toString(total));
			System.out.println("저장됨!");
		}
		else if(e.getSource() == button4) { //button.getName()인 "바닐라 라떼" 가 눌렸으면
			textArea.append(myButton4.getMenuName()+ " 가격 : ");
			textArea.append(Integer.toString(myButton4.getPrice())+"\t"+new SimpleDateFormat("HH:mm:ss").format(nano)+ "\n");
			total += myButton4.getPrice();
			textArea1.setText("총 결제액 : " +Integer.toString(total));
			System.out.println("저장됨!");
		}
		else if(e.getSource() == button5) { //button.getName()인 "카라멜 마끼야또" 가 눌렸으면
			textArea.append(myButton5.getMenuName()+ " 가격 : ");
			textArea.append(Integer.toString(myButton5.getPrice())+"\t"+new SimpleDateFormat("HH:mm:ss").format(nano)+ "\n");
			total += myButton5.getPrice();
			textArea1.setText("총 결제액 : " +Integer.toString(total));
			System.out.println("저장됨!");
		}
	
			
		
		
		}
		
	}
	
	
	
	public void panelWest() { //좌측 Panel
		JPanel panelWest = new JPanel();
		
		panelWest.setBackground(Color.blue);
//		JTextField textField = new JTextField();
		
		// 버튼 이름 담기
		this.button1 = new Button("아메리카노");
		this.button2 = new Button("카페라떼");
		this.button3 = new Button("카푸치노");
		this.button4 = new Button("바닐라 라떼");
		this.button5 = new Button("카라멜 마끼야또");
		
		// MyButton 클래스 생성자에 버튼이름 (label)과  가격 담기 
		myButton1 = new MyButton(button1.getLabel(), 4000); 
		myButton2 = new MyButton(button2.getLabel(), 4500);
		myButton3 = new MyButton(button3.getLabel(), 4500);
		myButton4 = new MyButton(button4.getLabel(), 5000);
		myButton5 = new MyButton(button5.getLabel(), 6000);
		// 이벤트 버튼객체 등록 
		button1.addActionListener(listener);
		button2.addActionListener(listener);
		button3.addActionListener(listener);
		button4.addActionListener(listener);
		button5.addActionListener(listener);
		
		
		
		panelWest.setLayout(new GridLayout(5,1,10,10)); //GridLayout(행, 열, 간격, 간격)
		panelWest.add(button1);
		panelWest.add(button2);
		panelWest.add(button3);
		panelWest.add(button4);
		panelWest.add(button5);
		
		
		
		add(panelWest, BorderLayout.WEST);
		
	}
	
	public void panelNorth() {  // 맨위 panel 메서드 
		JPanel panelNorth = new JPanel();
		
		
		//panelNorth.setBackground(Color.GREEN);
		panelNorth.setLayout(new GridLayout(1,3,10,10)); //GridLayout(행, 열, 간격, 간격)
		
		JPanel panelNorthCenter = new JPanel();
		JPanel panelEmpty = new JPanel(); // panelNortCenter의 왼쪽 공백용 
		JPanel panelEmpty2 = new JPanel(); // panelNortCenter의 오른쪽 공백용 
		panelNorthCenter.setBackground(Color.darkGray);
		panelNorthCenter.setLayout(new GridLayout(1,3,10,10));
		panelNorthCenter.setPreferredSize(new Dimension(100, 50));
		
		
		saveButton();
		openButton();
		deleteButton();
		
		
		panelNorthCenter.add(saveButton);
		panelNorthCenter.add(openButton);
		panelNorthCenter.add(deleteButton);
		
		panelNorth.add(panelEmpty);
		panelNorth.add(panelNorthCenter);
		panelNorth.add(panelEmpty2);
		add(panelNorth, BorderLayout.NORTH);
		
	}
	
	public void textAreaCenter() {  //중앙 JTextArea 메서드 
		
	    textArea = new JTextArea(7,1); //
		textArea.setBackground(Color.LIGHT_GRAY);
		textArea.setAlignmentX(CENTER_ALIGNMENT);
		Label label = new Label();
		label.setAlignment((int) CENTER_ALIGNMENT);
	
//		button1.addActionListener(new ActionListener() { // button1 누를시 
//			
//			@Override
//			public void actionPerformed(ActionEvent e) {
//				textArea.append(button1.getName()+"\n");  // button1 누를 textArea 에 text 추가 
//				System.out.println("아메리카노 저장함 ");
//				
//			}
//		});
	
		add(textArea, BorderLayout.CENTER);
		
	}
	
	public void textAreaSouth() { // 하단부 textArea 메서드 
		
		textArea1 = new JTextArea(1,1); 
		

		add(textArea1, BorderLayout.SOUTH);
		
	}
	
	public void saveButton() { //저장하기 버튼 
		saveButton = new JButton("저장하기");
		saveButton.addActionListener(new ActionListener() {
			
			@Override
			public void actionPerformed(ActionEvent e) {
				try (FileOutputStream fOut = new FileOutputStream("menulist.txt");
						ObjectOutputStream oOut = new ObjectOutputStream(fOut);){
					oOut.writeObject(textArea);
					
				} catch (Exception e1) {
					//e1.printStackTrace();
				} 
				
			}
		});
	}
	public void openButton() {
		openButton = new JButton("불러오기");
		openButton.addActionListener(new ActionListener() {
		JFileChooser chooser = new JFileChooser();
		
			@Override
			public void actionPerformed(ActionEvent e) {
				
				
				
				int ret = chooser.showOpenDialog(null);
//				FileNameExtensionFilter filter = new FileNameExtensionFilter("txt"); //*.txt파일만 보이게 설정 
//				chooser.setFileFilter(filter); 
				if(ret != JFileChooser.APPROVE_OPTION) {
					JOptionPane.showMessageDialog(null, "파일을 선택하지 않았습니다.","경고",JOptionPane.WARNING_MESSAGE);
					
				}
				
				String filePath = chooser.getSelectedFile().getPath(); //파일 경로를 알아온다.
				System.out.println(filePath);
				
				
			}
		});
	}
	public void deleteButton() {
		deleteButton = new JButton("삭제하기");
		deleteButton.addActionListener(new ActionListener() {
			
			@Override
			public void actionPerformed(ActionEvent arg0) {
				
				textArea.setText(null);
				textArea1.setText(null);
				total = 0;
				
			}
		});
	}

	public Homework1() {

		super("커피 자판기 ");  //JFrame 이름 
		
		setSize(new Dimension(1200,800)); // 1200 X 800 크기 
		setLocation(400,200);
		
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); // 창 닫으면 빌드 종료
		panelWest();
		panelNorth();
		textAreaCenter();
		textAreaSouth();
		
		setVisible(true);
	}
	
	
	
	
	
	public static void main(String[] args) {
		
		new Homework1();

	}

}

```
