package UDPClnt;

import java.net.*; 
import java.util.StringTokenizer;

public class UDPClnt {
	
	DatagramSocket clientSocket;
	InetAddress IPAddress;
	byte[] sendData;
	byte[] receiveData;
	DatagramPacket sendPacket;
	DatagramPacket receivePacket;
	
	/// Create new Client Socket
	/** @param strIP IP-Address from Server
	 */
	public void InitUdpClnt(String strIP) throws Exception
	{
		// create new UDP socket
		clientSocket = new DatagramSocket();
		// define address for UDP-Socket
		IPAddress = InetAddress.getByName(strIP);	
		// allocate memory for sending and receiving data
		sendData = new byte[256];
		receiveData = new byte[256];
	}
	
	/// Close Client Socket
	public void EndClnt() throws Exception
	{
		clientSocket.close();
	}
	
	/// Send Data to Server
	/** @param strData Data to Send as String
	 *  @param Network Port
	 */
	public void SendData(String strData, int nPort) throws Exception
	{
		sendData = strData.getBytes();
		// create Packet for sending Bytestream, IP-Adress and port
		sendPacket = new DatagramPacket(sendData, sendData.length, IPAddress, nPort);
		// send packet
		clientSocket.send(sendPacket);
	}
	
	/// Receive Data from Server
	/** @return Data from Server as String
	 */
	public String RecvData() throws Exception
	{ 
		int nIndex = -1;
		// create packet for receiving
		receivePacket = new DatagramPacket(receiveData, receiveData.length);
		// receive packet from server
		clientSocket.receive(receivePacket);
		// convert received data to string
		String modifiedSentence = new String(receivePacket.getData());
		nIndex = modifiedSentence.indexOf("\0");
		if(nIndex != -1)
		{
			modifiedSentence = modifiedSentence.substring(0, nIndex);
		}
		return modifiedSentence;		
	}
	
}
