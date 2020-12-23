```java

package chat;

import java.awt.BorderLayout;
import java.awt.Color;
import java.awt.Dimension;
import java.awt.GridLayout;
import java.awt.TextArea;
import java.awt.TextField;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.io.PrintWriter;
import java.io.Reader;
import java.io.StringReader;
import java.net.Socket;
import java.net.UnknownHostException;
import java.nio.charset.StandardCharsets;
import java.util.Scanner;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.JTextArea;
import javax.swing.JTextField;



public class Client extends JFrame{ 
	private  TextArea textArea;
	private  TextField textField;
	private  JButton sendButton;
	
	class ClientReadThread extends Thread{ //수시로 받는 스레드
		Socket socket;
		private BufferedReader br;

		ClientReadThread(Socket socket) throws IOException{ 
			this.socket = socket;
			br = new BufferedReader(new InputStreamReader(socket.getInputStream()));
		}
		@Override
		public void run() {

			try {
				
				String input;
				while(true) {
					input = br.readLine(); 
					textArea.append("상대 >>" + input + "\n");;
					System.out.println("Server: " + input);
				}
				
			} catch (IOException e) {
				e.printStackTrace();
			}		
		}
	}

	public void textArea1() {
		textArea = new TextArea();
		textArea.setBackground(Color.LIGHT_GRAY);
		textArea.setEditable(false); // the user cannot change the text of this text component (textArea에 텍스트입력X).
		
		add(textArea, BorderLayout.CENTER);
	}
	
	public void southPanel(Socket socket) throws IOException {
		Socket socket2;
		PrintWriter bw;
		
		socket2 = socket;
		bw = new PrintWriter(new OutputStreamWriter(socket.getOutputStream()), true);		
		JPanel panel = new JPanel();
		panel.setLayout(new GridLayout(0, 2));// 2열
		
		sendButton = new JButton("Send");
		textField = new TextField();
		
		sendButton.addActionListener(new ActionListener() { // Send 버튼 누를시 
			
			@Override
			public void actionPerformed(ActionEvent e) {
				String input;
				input = textField.getText();
				textArea.append("클라이언트 : " + input + "\n");
				//textArea.append("실험용 : "+textField.getText());
				//textArea.append("\n");
				textField.setText("");
				bw.println(input);
				bw.flush();
				
			}
		});//ActionListener

		panel.add(textField);
		panel.add(sendButton);
		add(panel, BorderLayout.SOUTH);
		
	}
	
	public void scrollBar() {
		
	}
	
	Client(){
		
		super("Client");
		
		setLocation(400, 200);
		setSize(new Dimension(400, 700));
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		
		textArea1();
		scrollBar();
		
		try {
			
			Socket socket = new Socket("127.0.0.1",50000);	
			ClientReadThread thread = new ClientReadThread(socket);
			thread.start();
			southPanel(socket);
			//			ClientWriteThread thread2 = new ClientWriteThread(socket);
//			thread2.start();
		} catch (Exception e) {
			e.printStackTrace();
		}
		setVisible(true);
	}
	
	public static void main(String[] args) {
			new Client();
		

	}

}

```
