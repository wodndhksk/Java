```java
package chatting;

import java.awt.BorderLayout;

import java.awt.Color;
import java.awt.Dimension;
import java.awt.GridLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.KeyAdapter;
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.DataInputStream;
import java.io.DataOutputStream;
import java.io.IOException;
import java.net.ServerSocket;
import java.net.Socket;
import java.net.SocketAddress;
import java.util.Scanner;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.JTextArea;
import javax.swing.JTextField;

public class Server {

	ServerSocket serverSocket;
	BufferedReader bufferedReader;
	BufferedWriter bufferedWriter;

	DataInputStream dataInputStream;
	DataOutputStream dataOutputStream;
	Socket socket1;
	Socket socket2;

	public Server() throws IOException {

		ServerSocket serverSocket = new ServerSocket(5000);

		socket1 = serverSocket.accept();
		new s_Read(socket1).start();
		new s_Write(socket1).start();

		socket2 = serverSocket.accept();
		new s_Read(socket2).start();
		new s_Write(socket2).start();

	}

	class s_Read extends Thread {
		Socket socket;

		s_Read(Socket socket) {

			this.socket = socket;

		}

		@Override
		public void run() {
			dataInputStream = null;

			try {
				dataInputStream = new DataInputStream(socket.getInputStream());

				while (true) {
					String massage = dataInputStream.readUTF();
					System.out.println();
					System.out.println("상대방 : " + massage);

					if (massage.equals("exit"))
						break;
				}

			} catch (Exception e) {

				e.printStackTrace();
			} finally {

				try {
					if (dataInputStream != null)
						dataInputStream.close();
				} catch (IOException e) {
					// TODO Auto-generated catch block
					e.printStackTrace();
				}
			} // finally

		}

	} // c1_Thread

	class s_Write extends Thread {
		Socket socket;

		s_Write(Socket socket) {

			this.socket = socket;

		}

		@Override
		public void run() {
			Scanner sc = new Scanner(System.in);
			dataOutputStream = null;

			try {
				dataOutputStream = new DataOutputStream(socket.getOutputStream());

				while (true) {
					System.out.println("my chat : ");
					String massage = sc.nextLine();
					dataOutputStream.writeUTF(massage);

					if (massage.equals("exit"))
						break;
				}
			} catch (Exception e) {

				e.printStackTrace();

			} finally {

				try {
					if (dataOutputStream != null)
						dataOutputStream.close();
				} catch (IOException e) {
					// TODO Auto-generated catch block
					e.printStackTrace();
				}
			}

		}

	}

	public static void main(String[] args) {

		try {
			new Server();

		} catch (IOException e) {

			e.printStackTrace();
		}

	}

}


```
