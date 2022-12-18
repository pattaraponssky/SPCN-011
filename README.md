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
 
 ![image](https://user-images.githubusercontent.com/113360594/208264111-ad3ff428-b9c2-4853-8ab4-61e7ec70123c.png)

	
 -ใช้คำสั่ง
	
	 sudo apt install qemu-guest-agent
	 
	 sudo systemctl start qemu-guest-agent
	 
-ใช้คำสั่งนี้เพื่อตรวจสอบสถานะการทำงานของ QEMU Guest Agent
	 
	 sudo systemctl status qemu-guest-agent
	 
![image](https://user-images.githubusercontent.com/113360594/208263935-de4a9a28-7220-4dfa-9af0-c09068ad8c4c.png)

-หน้า Summary จะมีเลข IPs เพิ่มมาหลังจากทำการเปิดใช้ QEMU Guest Agent

![image](https://user-images.githubusercontent.com/113360594/208264127-97fb44ab-de80-421d-a654-d1d24c31ec7e.png)

-ปิดเครื่อง และกด More เลือก Convert to template

![image](https://user-images.githubusercontent.com/113360594/208298518-494d111a-424d-42ba-8ded-edf1b87136d5.png)

-clone from template สร้าง vm ใหม่จำนวน 2 vm

![image](https://user-images.githubusercontent.com/113360594/208298593-e4d2d4bd-6755-4cff-92ac-a24dc027758e.png)

-กดเลือกเครื่อง clone แล้วเปลี่ยน IP โดยใช้คำสั่ง

	sudo -i
	rm /var/lib/dbus/machine-id
	nano /etc/machine-id 
	ln -s /etc/machine-id /var/lib/dbus/machine-id

-Restart os

-เครื่อง Clone 1

![image](https://user-images.githubusercontent.com/113360594/208298824-158954d2-38b6-4c56-b9af-fda5c3d4b21f.png)

![image](https://user-images.githubusercontent.com/113360594/208298833-2e0cb680-a120-4362-85bb-fe4c0e4fc82c.png)

-เครื่อง Clone 2

![image](https://user-images.githubusercontent.com/113360594/208298852-d715f63f-49a5-4b5d-a21d-ed8ab51a2e8b.png)

![image](https://user-images.githubusercontent.com/113360594/208298861-bec90a79-24e5-4a10-a5e5-157785babcae.png)

#create vm from other os
 
 -สร้าง Create VM ตั้งค่าต่างๆตามที่กำหนด โดยจะใช้ระบบปฏิบัติการ kali-linux-2022-3-live-amd64
 -ตั้งชื่อ VM ตัวอักษรชื่อภาษาอังกฤษตัวเองอย่างน้อย 3 ตัว-otherOS-เลข VM ID
 
 ![image](https://user-images.githubusercontent.com/113360594/208298965-b6ee4c1e-cb1a-47dd-854c-89f4c20cef2b.png)

#create create container template

-กดเลือกปุ่ม Create CT

-Create LXC Container หน้า General ใส่รายละเอียดข้อมูล แล้ว next เลือกค่า default

![image](https://user-images.githubusercontent.com/113360594/208299016-97870427-8024-4a74-bd13-3131c758a901.png)

-Create LXC Container หน้า Network เลือก IPv4 เป็น DHCP และ IPv6 เป็น SLAAC

![image](https://user-images.githubusercontent.com/113360594/208299138-f6b15345-e22c-4eb9-b6cf-aaeb7cd558ad.png)

-หน้า Summary

![image](https://user-images.githubusercontent.com/113360594/208299164-9a38968e-caa0-40bc-909f-2a7e7e29a1cd.png)


-หน้า console

![image](https://user-images.githubusercontent.com/113360594/208299195-2bc7fae7-e6f9-45e3-a1bf-5dfe42416cfc.png)









	   
		 


