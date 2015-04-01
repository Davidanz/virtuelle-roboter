public class main {
	
	private static UDPClnt UdpClnt = new UDPClnt();
	private static String strIP = "141.82.50.192";
	private static int nPort = 50000;
	
	public static void main(String[] args) {
		
		//JointPosition position = new JointPosition(9);
		
		try {
			UdpClnt.InitUdpClnt(strIP);
			UdpClnt.SendData("MOVE PTP 90.0 9    0.4 0.2 0.2 0.8 -3.14 1.57 0.0 -1.57 -3.14", nPort);
			String strRecv = UdpClnt.RecvData();
			UdpClnt.SendData("MOVE PTP 90.0 9    0.4 0.2 0.2 0.0 -3.14 1.57 0.0 -1.57 -3.14", nPort);
			strRecv = UdpClnt.RecvData();
			System.out.println(strRecv);
			//position = UdpClnt.getAsJointPosition(strRecv);
			UdpClnt.EndClnt();	
			//System.out.println(getCurrentJointPosition());
		} catch (Exception e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		

	}
	
	//Akutelle Position holen
	public String getCurrentJointPosition() {
		
		String strRecv = "Aktuelle Postion nicht ermittelt!";
		
		try {
			UdpClnt.InitUdpClnt(strIP);
			UdpClnt.SendData("GET CURRENTJOINTPOSITION", nPort);
			strRecv = UdpClnt.RecvData();
		} catch (Exception e) {
			e.printStackTrace();
		}
		return strRecv;
		
	}

}
