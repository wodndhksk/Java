```java
package chat.Sign;

import java.awt.Dimension;
import java.awt.GridLayout;
import java.awt.TextField;

import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;

public class Signin extends JFrame{
	private TextField idtextField, pswtextField, nametextField, emailTextField;
	private JLabel label;
	private JPanel panel = new JPanel();
	
	


	
	public void idTextField() {
		label = new JLabel("ID");
		label.setBounds(69, 113, 69, 20);
		panel.add(label);
		
		
		idtextField = new TextField();
		idtextField.setColumns(10);
		idtextField.setBounds(159, 106, 186, 35);
		panel.add(idtextField);
		add(panel);
	}
	public void passwordTextField() {
		label = new JLabel("password");
		label.setBounds(69, 163, 69, 20);
		panel.add(label);
		
		pswtextField = new TextField();
		pswtextField.setColumns(10);
		pswtextField.setBounds(159, 156, 186, 35);
		panel.add(pswtextField);
		add(panel);
	}
	public void nameTextField() {
		label = new JLabel("name");
		label.setBounds(69, 210, 69, 20);
		panel.add(label);
		
		nametextField = new TextField();
		nametextField.setColumns(10);
		nametextField.setBounds(159, 203, 186, 35);
		panel.add(nametextField);
		add(panel);
	}
	public void emailTextField() {
		label = new JLabel("email");
		label.setBounds(69, 257, 69, 20);
		panel.add(label);
		
		emailTextField = new TextField();
		emailTextField.setColumns(10);
		emailTextField.setBounds(159, 250, 186, 35);
		panel.add(nametextField);
		add(panel);
	}

	Signin(){
		super("로그인");
		setLocation(400, 200);
		setSize(new Dimension(500, 400));
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		
		//panel.setLayout(new GridLayout(2, 0));
		idTextField();
		passwordTextField();
		nameTextField();
		emailTextField();
		
		setVisible(true);
	}
	
	public static void main(String[] args) {
		new Signin();
		
	}
	
}
```
