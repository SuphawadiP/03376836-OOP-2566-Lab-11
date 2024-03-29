# Lab 11 Exercise 6

## Masking virtual member inheritance by keyword `new`

1.สร้าง console application project

```cmd
dotnet new console --name Lab11_Ex06
```

2.เปลี่ยน code ให้เป็นดังต่อไปนี้

```cs
Derived_2 d2 = new Derived_2();
Base b = (Base) d2;
Derived_1 d1 = (Derived_1) d2;


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
    public new void A()
    {
        System.Console.WriteLine("Derived_2.A()");
    }
}
```

3.Build project โดยการใช้คำสั่ง

```cmd
dotnet build  Lab11_Ex06
```

ถ้ามีที่ผิดพลาดในโปรแกรม ให้แก้ไขให้ถูกต้อง

4.บันทึกผลที่ได้จากการรันคำสั่งในข้อ 3
<img width="796" alt="Screenshot 2024-03-29 142053" src="https://github.com/SuphawadiP/03376836-OOP-2566-Lab-11/assets/144196049/ebd4f7d3-f8ef-4932-a709-d002e6789955">

#### สามารถ Build ได้ เพราะ ใช้ new เพื่อบอกว่าเมทอดใหม่นี้ไม่ได้เป็นการโอเวอร์ไรด์ (override) เมทอดในคลาสซ้อนทับก่อนหน้านี้ แต่เป็นการสร้างเมทอดใหม่ที่มีชื่อเดียวกันและคล้ายกับการสืบทอด
5.Run project โดยการใช้คำสั่ง

```cmd
dotnet run --project Lab11_Ex06
```

6.บันทึกผลที่ได้จากการรันคำสั่งในข้อ 5
<img width="796" alt="Screenshot 2024-03-29 142113" src="https://github.com/SuphawadiP/03376836-OOP-2566-Lab-11/assets/144196049/e8a50787-fe9f-4994-a15a-66aeab5374e4">

#### สามารถ Run ได้ เพราะ คลาส Derived_2 มีการสร้างเมทอด A() ที่ใหม่โดยใช้ new เพื่อมาสก์เมทอดที่มีชื่อเดียวกันในฐานและซ้อนทับซ้อนๆ ทำให้เมทอดใหม่นี้ไม่ได้ทำการโอเวอร์ไรด์
7.อธิบายสิ่งที่พบในการทดลอง
#### โปรแกรมจะแสดงผล
#### Derived_1.A()
#### Derived_1.A()
#### Derived_2.A()
