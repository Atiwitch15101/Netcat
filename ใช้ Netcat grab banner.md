# Netcat grab banner

## การใช้ Netcat grab banner

> Netcat(nc) คือเครื่องมือสารพัดประโยชน์  สามารถทำงานได้หลากหลายมาก ตั้งแต่การทดสอบ connect เข้าไปเหมือนกับ telnet ไปจนถึงการทำเป็น backdoor หรือติดต่อกลับ C&C ก็สามารถทำได้เช่นกัน

### ใช้งาน nc ให้เหมือน telnet

> เราสามารถใช้คำสั่งได้เป็น

```
nc <server_IP> <port>
```
> เช่น หากเราใช้ nmap scan เจอ web server port 80 แล้วต้องการติดต่อ web server แบบ manual จะใช้คำสั่งเป็น

```
nc target.com 80
```

> จากนั้นทำการส่งคำสั่ง  HTTP ไปเป็น

```
GET / HTTP/1.1
Host: google.co.th
```

> เราจะได้ HTTP Response กลับมา

### ตัวอย่างการใช้งาน

![Screenshot 2024-05-29 140909](https://github.com/Atiwitch15101/Netcat/assets/159407312/fe7d71ec-8d9e-450b-ab87-f631de7fff02)

> [!NOTE]
> หลังจากเชื่อมต่อเสร็จสิ้น จะมีข้อมูล banner แสดงออกมาที่หน้าจอ ช่วยในการรู้ข้อมูลพื้นฐานของเซิร์ฟเวอร์ที่เรากำลังเชื่อมต่อไปยังได้อย่างรวดเร็ว
