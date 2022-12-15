# SPCN-012
1. Hypervisor Technology คือ VMM ระบบที่ทำให้คอมพิวเตอร์หลายเครื่องใช้งานฮาร์ดแวร์ตัวเดียวกันได้ แบบมัลติคอร์มัลติเธรด และ Ram จำนวนมาก มี 2 ประเภท
      - Hypervisor Type 1 (Baremetal Architectur) ทำงานโดยตรงกับฮาร์ดแวร์ของเซิร์ฟเวอร์
      - Hypervisor Type 2 (Hosted Architecture) ทำหน้าที่เป็นซอฟต์แวร์ เป็นเครื่องเสมือน ต้องการใช้ฮาร์ดแวร์ต้องผ่านระบบปฏิบัติการก่อน จะจำลองเสมือนได้มีประสิทธิภาพสุด
    อ้างอิง https://personet.co.th/hypervisor/
    
2. Container Technology จะติดตั้งอยู่บน Host OS ใช้ OS ร่วมกันได้ ทำให้มีขนาดไม่ใหญ่ ประหยัด Resource แก้ปัญหาใน OS เดียวได้ ไว้จำลองการรันโปรแกรมจากหลายช่องทาง ไม่จำเป็นต้องมี Operating System image สามารถ deploy Application ไป OS และ Hardware อื่นได้ มีประสิทธิภาพการทำงานที่ดี เวลาบูตน้อย
    อ้างอิง https://blog.cloudhm.co.th/containers-vs-vm/
    
3. Monolithic MicroService 
      - Monolithic คือ สถาปัตยกรรมที่นิยมใช้กัน ส่วนต่างๆถูกเขียนที่สภาพแวดล้อมเดียวกัน ฐานข้อมูลเดียวกัน เช่น การทำเว็บ 
      - MicroService คือ สถาปัตนกรรมที่วางโครงสร้างเป็นชุดๆในลักษณะ loosely coupled หรือมีความ Independence โดยจะทำหน้าที่แยกส่วนต่างๆ ออกมาเป็นคอลเล็กชั่น ทำให้แต่ละส่วนทำงานในส่วนของตัวเองได้ ไม่ยึดติดมากนัก
     อ้างอิง https://www.softnix.co.th/2018/07/13/%E0%B8%82%E0%B9%89%E0%B8%AD%E0%B9%81%E0%B8%95%E0%B8%81%E0%B8%95%E0%B9%88%E0%B8%B2%E0%B8%87%E0%B8%A3%E0%B8%B0%E0%B8%AB%E0%B8%A7%E0%B9%88%E0%B8%B2%E0%B8%87-microservices-%E0%B9%81%E0%B8%A5%E0%B8%B0-mono/
     
4. Proxmox แพลตฟอร์มในการจัดการเซิร์ฟเวอร์โอเพ่นซอร์สที่สมบูรณ์สำหรับการจำลองเสมือน รองรับ REST API ผู้ดูแลจัดการทั้งหมดได้ด้วยอินเตอร์เฟซผู้ใช้แบบกราฟิก RAM สูงสุด 12TB และ CPU ตรรกะ 768 ตัวต่อโฮสต์
     อ้างอิง https://www.quickserv.co.th/knowledge-base/technology/VMware-vSphere-%e0%b8%81%e0%b8%b1%e0%b8%9a-Proxmox-%e0%b8%aa%e0%b8%b3%e0%b8%ab%e0%b8%a3%e0%b8%b1%e0%b8%9a%e0%b8%98%e0%b8%b8%e0%b8%a3%e0%b8%81%e0%b8%b4%e0%b8%88-%e0%b9%83%e0%b8%8a%e0%b9%89%e0%b9%81%e0%b8%9a%e0%b8%9a%e0%b9%84%e0%b8%ab%e0%b8%99%e0%b8%94%e0%b8%b5%e0%b8%97%e0%b8%b5%e0%b9%88%e0%b8%aa%e0%b8%b8%e0%b8%94/
5. Ceph เป็นระบบ distributed storage ทำงานบน cluster ของ computer node มี 3 node
    1. monitor ดูแลระบบ cluster
    2. OSD อ่าน/เขียน ตามคำสั่ง
    3. MDS ดูแลสถานะของ file hierarchy
     อ้างอิง https://www.throughwave.co.th/2017/04/10/%E0%B9%81%E0%B8%99%E0%B8%B0%E0%B8%99%E0%B8%B3-ceph-storage-distributed-storage-%E0%B8%A3%E0%B8%B9%E0%B8%9B%E0%B9%81%E0%B8%9A%E0%B8%9A%E0%B9%83%E0%B8%AB%E0%B8%A1%E0%B9%88%E0%B8%97%E0%B8%B5%E0%B9%88/
6. NFS เป็น Protocol ที่ช่วยให้ computer แชร์ข้อมูลผ่าน network ได้ โครงสร้างเป็น Server และ Client ทำให้ computer ใน network เดียวกันเข้าถึงข้อมูลได้ โดยฝั่ง server สามารถตั้งค่าได้ว่า ไฟล์ไหนสามารถแชร์หากันได้ ฝั่ง client ต้อง mount ไฟล์ผ่าน network โดยใช้คำสั่ง mount
      อ้างอิง https://blog.cloudhm.co.th/nfs-vs-smb/
                      
