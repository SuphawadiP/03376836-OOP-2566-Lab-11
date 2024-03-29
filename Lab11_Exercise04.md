# Lab 11 Exercise 4

## Virtual member inheritance
![alt text](./Pictures/image01.png)

1.สร้าง console application project

```cmd
dotnet new console --name Lab11_Ex04
```

2.เปลี่ยน code ให้เป็นดังต่อไปนี้

```cs
var b = new Base();
var d1 = new Derived_1();
var d2 = new Derived_2();

b.A();
d1.A();
d2.A();

class Base
{
    public virtual void A()
    {
        System.Console.WriteLine("Base.A()");
    }
}
class Derived_1 : Base
{
    public override void A()
    {
        System.Console.WriteLine("Derived_1.A()");
    }
}
class Derived_2 : Derived_1
{
    public override void A()
    {
        System.Console.WriteLine("Derived_2.A()");
    }
}
```

3.Build project โดยการใช้คำสั่ง

```cmd
dotnet build  Lab11_Ex04
```

ถ้ามีที่ผิดพลาดในโปรแกรม ให้แก้ไขให้ถูกต้อง

4.บันทึกผลที่ได้จากการรันคำสั่งในข้อ 3
<img width="795" alt="Screenshot 2024-03-29 135230" src="https://github.com/SuphawadiP/03376836-OOP-2566-Lab-11/assets/144196049/33a8fd92-c2ae-4b92-af18-72101e66470c">

#### สามารถ Build ได้ เพราะ เมทอด virtual ถูกโอเวอร์ไรด์ในคลาสลูกทำให้เราสามารถเรียกใช้เมทอดของคลาสลูกได้โดยใช้ตัวแปรของคลาสแม่
5.Run project โดยการใช้คำสั่ง

```cmd
dotnet run --project Lab11_Ex04
```

6.บันทึกผลที่ได้จากการรันคำสั่งในข้อ 5
<img width="790" alt="Screenshot 2024-03-29 135302" src="https://github.com/SuphawadiP/03376836-OOP-2566-Lab-11/assets/144196049/1b54697f-3f2d-410f-ab15-9e1a0005b4c4">

#### สามารถ Run ได้ เพราะ virtual ซึ่งหมายความว่าคลาสลูกสามารถโอเวอร์ไรด์เมทอด A() ได้ และในที่นี้ Derived_1 และ Derived_2 ได้โอเวอร์ไรด์เมทอด A() นี้ตามลำดับ
7.อธิบายสิ่งที่พบในการทดลอง
#### โปรแกรมจะแสดงผล
#### Base.A()
#### Derived_1.A()
#### Derived_2.A()
