# Lab 11 Exercise 7

## Prevent inheritance by keyword `sealed`

1.สร้าง console application project

```cmd
dotnet new console --name Lab11_Ex07
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
    public sealed override void A()
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
dotnet build  Lab11_Ex07
```

ถ้ามีที่ผิดพลาดในโปรแกรม ให้แก้ไขให้ถูกต้อง

4.บันทึกผลที่ได้จากการรันคำสั่งในข้อ 3
#### แก้ไขแล้ว
<img width="795" alt="Screenshot 2024-03-29 143116" src="https://github.com/SuphawadiP/03376836-OOP-2566-Lab-11/assets/144196049/641088d4-3de7-437d-9304-86a3fb9dea34">

#### ไม่สามารถ Build ได้ เพราะ Derived_2.A พยายามจะสืบทอดจาก Derived_1 แต่ถูกปิดกั้นด้วยคำสั่ง sealed แก้โดยลบส่วนการทำงานของclass Derived_2 : Derived_1 ออก
5.Run project โดยการใช้คำสั่ง

```cmd
dotnet run --project Lab11_Ex07
```

6.บันทึกผลที่ได้จากการรันคำสั่งในข้อ 5
#### แก้ไขแล้ว
<img width="792" alt="Screenshot 2024-03-29 143216" src="https://github.com/SuphawadiP/03376836-OOP-2566-Lab-11/assets/144196049/7bcd57c1-adb4-47af-8cf8-43caaa9eaf19">

#### ไม่สามารถ Run ได้ เพราะ Derived_2.A พยายามจะสืบทอดจาก Derived_1 แต่ถูกปิดกั้นด้วยคำสั่ง sealed แก้โดยลบส่วนการทำงานของclass Derived_2 : Derived_1 ออก
7.อธิบายสิ่งที่พบในการทดลอง
#### โปรแกรมจะแสดงผล
#### Derived_1.A()
#### Derived_1.A()
#### Derived_1.A()
