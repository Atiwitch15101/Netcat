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

## Netcat ส่ง Message

> เราสามารถใช้ netcat ในการรับ-ส่ง Message หากันได้ผ่าน nc ได้ เช่น

### Server: (192.168.1.1)

> ที่ฝั่ง Server รันคำสั่งเป็น

```
nc -lvp <port>
```

> หรือ

```
nc -lvp 10000
```

> นั่นคือเราจะรัน server รอรับ message ที่ port 10000 นั่นเอง

### Client (ฝั่งที่ต้องการส่ง message คำว่า “message” ไปยังปลายทาง)

> ที่ฝั่ง Client รันคำสั่งเป็น

```
nc 192.168.1.1 10000
message
```

> เมื่อเสร็จแล้ว server ปลายทางจะได้รับคำว่า “message” ขึ้นมา

### ตัวอย่างการใช้งาน

> นั้นส่ง message “Testing secplayground” ไปยัง port 10000 ซึ่งภายใน server เป้าหมายจะมี netcat รันคำสั่ง nc -lvp 10000 ค้างไว้อยู่แล้ว หากเราส่ง message สำเร็จ จะพบ flag ที่ /tmp/flag.txt

![Screenshot 2024-05-29 142748](https://github.com/Atiwitch15101/Netcat/assets/159407312/0c683c03-1948-4623-a29d-8a95c1606cfe)

![Screenshot 2024-05-29 143614](https://github.com/Atiwitch15101/Netcat/assets/159407312/43bfde72-4c2d-4e6e-9b88-4e949574efdb)

## Netcat รับ-ส่ง File

> เราสามารถใช้ netcat ในการรับ-ส่ง file ใดๆก็ได้ผ่าน nc เช่น

## Server: (192.168.1.1)

> ที่ฝั่ง Server รันคำสั่งเป็น

```
nc -lvp 10000
```

หรือ

```
nc -lvp 10000 > out.txt
```

> นั่นคือเราจะรัน server รอรับ message ที่ port 10000 นั่นเอง

### Client (ฝั่งที่ต้องการส่ง File ไปยังปลายทาง)

> ที่ฝั่ง Client รันคำสั่งเป็น

```
cat <file> | nc 192.168.1.1 10000
```

> เมื่อเสร็จแล้ว server ปลายทางจะได้รับ <file> มา หรือหากใช้ > ก็จะกลายเป็น save ลงไฟล์ out.txt นั่นเอง




