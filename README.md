# SPCN-012
# 1. Hypervisor Technology 
VMM ระบบที่ทำให้คอมพิวเตอร์หลายเครื่องใช้งานฮาร์ดแวร์ตัวเดียวกันได้ ใช้ประโยชน์ได้สูงสุด จำลองระบบปัฏิบัติการ แบบมัลติคอร์มัลติเธรด และ Ram จำนวนมาก เหมาะสำหรับเมนเฟรมมากกว่า windown OS เพราะ Hypervisor จัดการหลายระบบได้เหมือนกับ Host มี 2 ประเภท
      
- Hypervisor Type 1 (Baremetal Architectur) ทำงานโดยตรงกับฮาร์ดแวร์ของเซิร์ฟเวอร์ ตัวอย่างได้แก่ VMware ESXi
- Hypervisor Type 2 (Hosted Architecture) ทำหน้าที่เป็นซอฟต์แวร์ เป็นเครื่องเสมือน ต้องการใช้ฮาร์ดแวร์ต้องผ่านระบบปฏิบัติการก่อน จะจำลองเสมือนได้มีประสิทธิภาพสูงสุด ตัวอย่างได้แก่ VMware Server

ประโยชน์ คือ มีความปลอดภัย สามารถทดสอบซอฟแวร์ได้ ลดความเสี่ยงต่อตัวคอมพิวเตอร์ ลดต้นทุน ใช้พลังงานน้อยลง จะไม่ส่งผลกระทบต่อตัวเครื่อง ช่วยให้ข้อมูลปลอดภัย 

อ้างอิง https://personet.co.th/hypervisor/
    
# 2. Container Technology 
เปรียบเสมือนตู้ Containers ที่อยู่บนเรือที่สามารถยกเข้า/ออกได้ สิ่งที่ Infrastructure ต้องเตรียมสำหรับรองรับ Container คือ 

- Infrastructure : โครงสร้างพื้นฐาน
- Host Operation System : เป็น OS ที่ติดตั้งบน server เป็น Windows หรือ Linux  
- Container Runtime : เป็น Command Line สำหรับ Brand
- Binary/Library : ชุดข้อมูล
- Application : Software ให้ user ใช้งาน

จะติดตั้งอยู่บน Host OS ใช้ OS ร่วมกันได้ ทำให้มีขนาดไม่ใหญ่ ประหยัด Resource แก้ปัญหาใน OS เดียวได้ ไว้จำลองการรันโปรแกรมจากหลายช่องทาง ไม่จำเป็นต้องมี Operating System image สามารถ deploy Application ไป OS และ Hardware อื่นได้ มีประสิทธิภาพการทำงานที่ดี เวลาบูตน้อย
    
อ้างอิง https://blog.cloudhm.co.th/containers-vs-vm/
    
# 3. Monolithic MicroService 
- Monolithic คือ สถาปัตยกรรมที่นิยมใช้กัน ส่วนต่างๆถูกเขียนที่สภาพแวดล้อมเดียวกัน ฐานข้อมูลเดียวกัน เช่น การทำเว็บ 

ประโยชน์ 
1. ง่ายต่อการพัฒนา Application ถูกเขียนในสภาพแวดล้อมเดียวกัน
2. ง่ายต่อการ Deploy เพราะแต่ส่วนถูกมัดรวมกัน การ Deploy จึงง่ายในการนำโค้ด ไปยังตัว web server และตัว database
3. ง่ายต่อการ scale โดยสามารถ clone ออกมาได้

ข้อเสีย
1. การพัฒนานาน
2. IDE ช้า เพราะโค้ดมีขนาดใหญ่
3. แก้ไขส่วนใด อาจส่งผลต่อส่วนอื่น
4. ย้าย framework ยาก
      
- MicroService คือ สถาปัตนกรรมที่วางโครงสร้างเป็นชุดๆในลักษณะ loosely coupled หรือมีความ Independence โดยจะทำหน้าที่แยกส่วนต่างๆ ออกมาเป็นคอลเล็กชั่น ทำให้แต่ละส่วนทำงานในส่วนของตัวเองได้ ไม่ยึดติดมากนัก

ประโยชน์
1. แก้ไขปัญหาการทับซ้อยของ Application
2. อิสระต่อการเลือก service
3. Deploy เป็นอิสระ ไม่ต้องรอ service อื่น
      
อ้างอิง https://www.softnix.co.th/2018/07/13/%E0%B8%82%E0%B9%89%E0%B8%AD%E0%B9%81%E0%B8%95%E0%B8%81%E0%B8%95%E0%B9%88%E0%B8%B2%E0%B8%87%E0%B8%A3%E0%B8%B0%E0%B8%AB%E0%B8%A7%E0%B9%88%E0%B8%B2%E0%B8%87-microservices-%E0%B9%81%E0%B8%A5%E0%B8%B0-mono/
     
# 4. Proxmox 
แพลตฟอร์มในการจัดการเซิร์ฟเวอร์โอเพ่นซอร์สที่สมบูรณ์สำหรับการจำลองเสมือน รองรับ REST API ผู้ดูแลจัดการทั้งหมดได้ด้วยอินเตอร์เฟซผู้ใช้แบบกราฟิก RAM สูงสุด 12TB และ CPU ตรรกะ 768 ตัวต่อโฮสต์ เป็นการกระจาย Linux ที่ใช้ Debian พร้อมเคอร์เนล Ubuntu LTS ที่ได้รับการแก้ไข เพื่อช่วยปรับใช้และจัดการ VM และ Container ได้ เช่น KVM(VM แบบเคอร์เนล) สำหรับ VM และ Linux Containers(LXC) สำหรับ Container เป็นเครื่องมือจำลองระดับ OS เครื่องมือมากมาย การจัดการบนเว็บ จัดการคลัสเตอร์ข้ามโหนดเซิร์ฟเวอร์หลายเครื่องเพื่อความพร้อมใช้งาน และจะจัดการตรวจสอบทุก VM มีคุณสมบัติในการโยกย้ายแบบออนไลน์ ย้ายโดยไม่ต้องหยุดทำงาน มีไฟร์วอลล์ในตัวที่ปรับแต่งได้เพื่อให้กำหนดค่าผ่าน GUI หรือ CLI โดยสามารถตั้งค่ากฎไฟร์วอลล์สำหรับโฮสต์ทั้งหมดภายในคลัสเตอร์หรือกำหนดกฎสำหรับ VM และคอนเทนเนอร์เท่านั้น
    
อ้างอิง https://www.quickserv.co.th/knowledge-base/technology/VMware-vSphere-%e0%b8%81%e0%b8%b1%e0%b8%9a-Proxmox-%e0%b8%aa%e0%b8%b3%e0%b8%ab%e0%b8%a3%e0%b8%b1%e0%b8%9a%e0%b8%98%e0%b8%b8%e0%b8%a3%e0%b8%81%e0%b8%b4%e0%b8%88-%e0%b9%83%e0%b8%8a%e0%b9%89%e0%b9%81%e0%b8%9a%e0%b8%9a%e0%b9%84%e0%b8%ab%e0%b8%99%e0%b8%94%e0%b8%b5%e0%b8%97%e0%b8%b5%e0%b9%88%e0%b8%aa%e0%b8%b8%e0%b8%94/

# 5. Ceph 
เป็นระบบ distributed storage ทำงานบน cluster ของ computer node มี 3 node
    1. monitor ดูแลระบบ cluster
    2. OSD อ่าน/เขียน ตามคำสั่ง
    3. MDS ดูแลสถานะของ file hierarchy
Ceph ทำงานบน cluster ที่แต่ละ Node ทำหน้าต่างกันอย่างชัดเจน ทำให้จัดการได้สะดวก workload ถูกกระจายอย่างเหมาะสม ลดความเสี่ยงจาก System failure และทำให้ scale ได้ง่าย และไม่ต้องการ hardware แบบพิเศษ

มี 3 Interface
1. Ceph Object Storage รองรับ Amazon S3 และ OpenStack Swift protocol สามารถทำงานร่วมกับ application ที่รองรับ protocol เหล่านั้น
2. Ceph Block Storage  รองรับการทำงานในลักษณะที่คล้ายกับ SAN (Storage Area Network)
3. Ceph File System Storage รองรับการทำงานในลักษณะคล้าย NAS คือ ผู้ใช้สามารถสร้าง CephFS ขึ้นมาใน Ceph Storage แล้ว mount ไปใช้งานยังเครื่องปลายทางได้เช่นเดียวกับ NAS ทั่วไปโดยใช้งานผ่าน CephFS Gateway

อ้างอิง https://www.throughwave.co.th/2017/04/10/%E0%B9%81%E0%B8%99%E0%B8%B0%E0%B8%99%E0%B8%B3-ceph-storage-distributed-storage-%E0%B8%A3%E0%B8%B9%E0%B8%9B%E0%B9%81%E0%B8%9A%E0%B8%9A%E0%B9%83%E0%B8%AB%E0%B8%A1%E0%B9%88%E0%B8%97%E0%B8%B5%E0%B9%88/

# 6. NFS 
เป็น Protocol ที่ช่วยให้ computer แชร์ข้อมูลผ่าน network ได้ มีการพัฒนาและนำมาใช้งานใน ปี ค.ศ.1984 โครงสร้างเป็น Server และ Client ทำให้ computer ใน network เดียวกันเข้าถึงข้อมูลได้ โดยฝั่ง server สามารถตั้งค่าได้ว่า ไฟล์ไหนสามารถแชร์หากันได้ ฝั่ง client ต้อง mount ไฟล์ผ่าน network โดยใช้คำสั่ง mount ทำให้มุมมองฝั่งที่ mount ผ่าน Network ด้วย NFS ให้ความรู้สึกว่าใช้ไฟล์จากเครื่องตัวเอง

หลังจากที่มีการแชร์ผ่านทาง Network ไปแล้ว NFS daemons ที่อยู่ทั้งฝั่ง Server และ Client จะทำการ Sync ข้อมูลระหว่าง Device อยู่ตลอดเวลา หากมีการเปลี่ยนแปลง เครื่องที่ mount อยู่ จะเห็นการเปลี่ยนแปลงไปด้วย ทางเทคนิค NFS จะใช้แชร์ไฟล์กันในเฉพาะ Local Network แชร์ผ่าน Internet จะยาก เพราะไม่รองรับการแชร์ผ่าน Routing ที่มีความซับซ้อน หรือการทำ NAT ก็คือ NFS 

อ้างอิง https://blog.cloudhm.co.th/nfs-vs-smb/
                      
