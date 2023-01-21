# SPCN-012
# 1. Hypervisor Technology 
คือ ระบบที่จำลองให้ระบบปฏิบัติการหลายระบบทำงานพร้อมกันบน host เดียวกันได้ ไม่ให้เกิดการทับซ้อน เป็นระบบแบบมัลติคอร์มัลติเธรต หรือ เรียกอีกชื่อว่า VMM สามารถสร้างและลบได้ตามต้องการ เป็นตัวจำลอง Hardware ให้ VM

- Hypervisor Type 1 (Baremetal Architectur) เป็น Hypervisor ที่ทำงานบนฮาร์ดแวร์ เปรียบเสมือนทำให้ตัวเครื่องคอมพิวเตอร์จำลอง OS ได้หลายตัว ใช้งาน Hardware ของเครื่องโดยตรง
- Hypervisor Type 2 (Hosted Architecture) เป็น Hypervisor ที่ทำงานบนฮาร์ดแวร์ เปรียบเสมือนทำให้ตัวเครื่องคอมพิวเตอร์จำลอง OS ได้หลายตัว ใช้งาน Hardware ของเครื่องโดยตรง

ประโยชน์ คือ มีความปลอดภัย สามารถทดสอบซอฟแวร์ได้ ลดความเสี่ยงต่อตัวคอมพิวเตอร์ ลดต้นทุน ใช้พลังงานน้อยลง จะไม่ส่งผลกระทบต่อตัวเครื่อง ช่วยให้ข้อมูลปลอดภัย 

อ้างอิง 
- https://personet.co.th/hypervisor/
- https://arnondora.in.th/what-is-virtual-machine/
    
# 2. Container Technology 
ระบบที่ทำการรวบรวม library หรือ binary ที่จำเป็นในการรันแอปพลิเคชันนั้นไว้แล้ว โดยสามารถนำไปใช้งานได้ทุกระบบปฏิบัติการ ง่ายต่อการโยกย้าย การ boot ระบบที่เร็วกว่า VMM ใช้พื้นที่น้อยกว่า เพราะไม่ต้องสร้างระบบที่รองรับแอปพลิเคชั่นขึ้นมาใหม่ เปรียบเสมือน ตู้ Container ที่เก็บทุกอย่างไว้หมดแล้ว สามารถนำใช้งานได้เลย ติดตั้งอยู่บน Host OS เพื่อให้เรียกใช้งานในระบบอื่นได้
    
อ้างอิง 
- https://blog.cloudhm.co.th/containers-vs-vm/
- https://aws.amazon.com/th/what-is/containerization/
- https://www.blognone.com/node/105928
- https://www.mindphp.com/%E0%B8%84%E0%B8%B9%E0%B9%88%E0%B8%A1%E0%B8%B7%E0%B8%AD/73-%E0%B8%84%E0%B8%B7%E0%B8%AD%E0%B8%AD%E0%B8%B0%E0%B9%84%E0%B8%A3/9187-containers.html
    
# 3. Monolithic MicroService 
- Monolithic คือ ระบบที่ทำงานในสภาพแวดล้อมเดียวกัน ทุกส่วนประกอบทำงานด้วยกัน ใช้ฐานข้อมูลเดียวกัน อยู่ในก้อนเดียวกัน
ประโยชน์ 
1. ง่ายต่อการพัฒนา Application ถูกเขียนในสภาพแวดล้อมเดียวกัน
2. ง่ายต่อการ Deploy เพราะแต่ส่วนถูกมัดรวมกัน การ Deploy จึงง่ายในการนำโค้ด ไปยังตัว web server และตัว database
3. ง่ายต่อการ scale โดยสามารถ clone ออกมาได้

ข้อเสีย
1. การพัฒนานาน
2. IDE ช้า เพราะโค้ดมีขนาดใหญ่
3. แก้ไขส่วนใด อาจส่งผลต่อส่วนอื่น
4. ย้าย framework ยาก
      
- MicroService คือ ระบบที่แยกส่วนประกอบในการทำงานกัน โดยจะแบ่งตามจุดประสงค์ในการทำงาน จะใช้ฐานข้อมูลแยกกันตามจุดประสงค์นั้นๆ แต่ละส่วนทำงานด้วยตัวเอง แต่ละส่วนคุยกันผ่าน API

ประโยชน์
1. แก้ไขปัญหาการทับซ้อนของ Application
2. อิสระต่อการเลือก service
3. Deploy เป็นอิสระ ไม่ต้องรอ service อื่น

ข้อเสีย
1. มีความช้าในการติดต่อของแต่ละส่วนหากัน
2. การ Deploy ต้องมีตัว auto เพราะแต่ละตัวอยู่แยกกัน
      
อ้างอิง 
- https://www.softnix.co.th/2018/07/13/%E0%B8%82%E0%B9%89%E0%B8%AD%E0%B9%81%E0%B8%95%E0%B8%81%E0%B8%95%E0%B9%88%E0%B8%B2%E0%B8%87%E0%B8%A3%E0%B8%B0%E0%B8%AB%E0%B8%A7%E0%B9%88%E0%B8%B2%E0%B8%87-microservices-%E0%B9%81%E0%B8%A5%E0%B8%B0-mono/
- https://blog.skooldio.com/microservices-vs-monolithic/
     
# 4. Proxmox 
ระบบปฏิบัติการสำหรับจัดการ VM แบบ Hyper-V type 1 ผสานรวม KVM Hypervisor และ LXC ใช้การจัดเก็บข้อมูล ฟังก์ชัน บนแพลตฟอร์มเดียว ควบคุมผ่านเว็บอินเตอร์เฟรช ใช้งานง่าย ลดค่าใช้จ่ายที่ไม่จำเป็น เป็นระบบที่คล้ายกับ ESXi ของ VMware
    
อ้างอิง 
- https://www.quickserv.co.th/knowledge-base/technology/VMware-vSphere-%e0%b8%81%e0%b8%b1%e0%b8%9a-Proxmox-%e0%b8%aa%e0%b8%b3%e0%b8%ab%e0%b8%a3%e0%b8%b1%e0%b8%9a%e0%b8%98%e0%b8%b8%e0%b8%a3%e0%b8%81%e0%b8%b4%e0%b8%88-%e0%b9%83%e0%b8%8a%e0%b9%89%e0%b9%81%e0%b8%9a%e0%b8%9a%e0%b9%84%e0%b8%ab%e0%b8%99%e0%b8%94%e0%b8%b5%e0%b8%97%e0%b8%b5%e0%b9%88%e0%b8%aa%e0%b8%b8%e0%b8%94/
- https://www.bestinternet.co.th/single_blog.php?id=96&proxmox%20virtual%20environment%20%E0%B8%AB%E0%B8%A3%E0%B8%B7%E0%B8%AD%20proxmox%20ve%20(pve)%20%E0%B8%84%E0%B8%B7%E0%B8%AD%E0%B8%AD%E0%B8%B0%E0%B9%84%E0%B8%A3
- https://netway.co.th/kb/blog/cloud-managed-services/%E0%B9%83%E0%B8%8A%E0%B9%89%E0%B8%87%E0%B8%B2%E0%B8%99-server-%E0%B9%83%E0%B8%AB%E0%B9%89%E0%B8%84%E0%B8%B8%E0%B9%89%E0%B8%A1%E0%B8%84%E0%B9%88%E0%B8%B2%E0%B8%94%E0%B9%89%E0%B8%A7%E0%B8%A2%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B8%97%E0%B8%B3-virtualization%E2%80%8B
- https://yourconnect.com/proxmox/ve/
- https://www.proen.cloud/en/blogs/proxmox-virtual-environment/
- https://blog.limitrack.com/proxmox-basic/
- https://kirz.com/EN/blog-detail/Proxmox-VE-Hypervisor-%E0%B8%97%E0%B8%A3%E0%B8%87%E0%B8%9E%E0%B8%A5%E0%B8%B1%E0%B8%87%E0%B8%97%E0%B8%B5%E0%B9%88-Cloud-Service-Provider-%E0%B8%95%E0%B9%88%E0%B8%B2%E0%B8%87%E0%B9%80%E0%B8%A5%E0%B8%B7%E0%B8%AD%E0%B8%81%E0%B9%83%E0%B8%8A%E0%B9%89

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
                      
