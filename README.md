# SPCN-011
**สร้าง vm and ct on Proxmox cluster**
# create master vm (ubuntu-22.04)
1.เลือก Creat Virtual Machine

2.กรอกรายละเอียดชื่อและตั้งค่าต่างๆ

      -ตัวอักษรชื่อภาษาอังกฤษตัวเอง  3 ตัว - เลข VM ID                                                                              
      -ช่อง Resource Pool เลือก Special_CN
      -ช่อง ISO image เลือก ubuntu-22.04.1-live-server-amd64
      -System ตั้งค่าตามค่า default 
      -Disk ตั้งค่าตามค่า default 
      -CPU ตั้งค่าตามค่า default
      -Memory เลือกค่า 2048
      -Netwoek ตั้งค่าตามค่า default

![image](https://user-images.githubusercontent.com/113360594/208263139-6652dc01-2533-4b71-aa46-89ec232b59b3.png)

3.Install ตามขั้นตอน และจะมีให้กรอกข้อมูล

4.ตั้งค่า SSH เลือก Github ใส่รายละเอียด Username Github Confirm SSH Keys แล้วรอติดตั้ง

![image](https://user-images.githubusercontent.com/113360594/208263627-f3760c63-500a-4b39-993e-4ea7ee5850ab.png)

**Setup timezone**

 -ใช้คำสั่ง เพื่อตั้งค่าเวลา
 
     Sudo timedatectl set-timezone Asia/Bankok
		 
 -ใช้คำสั่ง เพื่อเช็คเวลา
 
     date
		 
**ติดตั้ง QEMU Guest Agent**

 -Shutdown VM ไปแถบ Option ของ VM ตัวนั้น เลือกกด QEMU Guest Agent ปรับเป็น Enable
	
 -ใช้คำสั่ง
	
	 sudo apt install qemu-guest-agent
	 
	 sudo systemctl start qemu-guest-agent
	 
-ใช้คำสั่งนี้เพื่อตรวจสอบสถานะการทำงานของ QEMU Guest Agent
	 
	 sudo systemctl status qemu-guest-agent
	 
![image](https://user-images.githubusercontent.com/113360594/208263935-de4a9a28-7220-4dfa-9af0-c09068ad8c4c.png)

	   
		 


