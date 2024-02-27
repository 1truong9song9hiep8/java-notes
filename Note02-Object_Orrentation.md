## Tính đóng gói (Encapsulation)
Tính đóng gói trong Java thể hiện ở việc thiết lập các access modifier nhằm dấu những thứ không cần thiết, từ đó giúp người lập trình viên dấu những thông tin quan trọng và riêng tư trong ứng dụng.

private/public/protected method trong java cũng được xem là một thể hiện của tính đóng gói trong java, package cũng được xem là tính đóng gói trong java

Lợi ích từ getter và setter? nó là việc bạn có thể tùy chỉnh sử lý khi get và set giá trị cho biến.
## Iheritence, Is-A, Has-A
Mọi class mà chúng ta tạo ra đều kế thừa từ 1 class tên là `Object`, và có thể sử dụng một số method từ class này như: `equal()`, `hashCode()`, `toString()`...
Tính kế thừa trong Java được thể hiện bằng việc 1 class có thể extend 1 class và có thể implement nhiều interface.
Mối quan hệ Is-A và Has-A
Mối quan hệ Is-A chính là mối quan hệ kế thừa, khi một class A extends từ B, ta nói A-B là mối quan hệ Is-a (hay cha-con), hay A là một kiểu của B, mối quan hệ IS-A được thể hiện thông qua keyword extends và implements

Has-A
Nếu một class A có một properties là instance của class B, khi đó mối quan hệ A-B chính là quan hệ Has-a, từ đây các method trong B có thể được gọi từ A thông qua instance của B.

IS-a/ has-a hay escapsulation chỉ là phần cực kì nhỏ và cơ bản trong thiết kế,trong thực tế, mọi thứ phức tạp và to lớn hơn rất nhiều, và để hỗ trợ việc đó thì các mẫu thiết kế được ra đời nhằm hỗ trợ việc thiết kế ứng dụng java một cách hiệu quả..

## Tính trừu tượng (Polymorphism)
Tính đa hình được thể hiện qua kế thừa và override lại các phương thức của lớp cha.

Biến tham chiếu là những biến có kiểu là parent hoặc interface

Static variable vs method
Biến và hàm static được tạo khi class chứa nó được load vào JVM trước bất cứ instance nào được tạo, Biến và hàm static được dùng để lưu trữ dữ liệu mà có thể chia sẽ giữa các instance, nó không phụ thuộc vào instance của class
một static method không thể truy cập vào một biến nonstatic

## Static
### Biến và hàm static
Một số đặc điểm của hàm static:
- Biến static được các instance chia sẻ.
- Có thể gọi trực tiếp mà không cần khởi tạo instance của class.
- Hàm static chỉ có thể truy cập vào các static member, và không có quyền truy cập vào các non-static member.
- Hàm static không thể được ghi đè

## coupling vs cohesion
coupling(sự khớp nối) và cohesion(tính liên kết) để chỉ mức độ liên kết, mức độ phụ thuộc lẫn nhau giữa các đối tượng trong OOP. Một ứng dụng được thiết kế OOP tốt là một ứng dụng mà sự khớp nối được tránh đồng thời tính liên kết dược tăng cường.

### Tính khớp nối 
Một class A chỉ biết những thứ mầ class B thể hiện qua interface thì đó la một kết nối lỏng lẻo (một thiết kế tốt), ví dụ:
```java
  class DoTaxes {
        float rate;

        float doColorado() {
            SalesTaxRates str = new SalesTaxRates();
            rate = str.salesRate; // ouch
            // this should be a method call:
            // rate = str.getSalesRate("CO");
            // do stuff with rate
        }
    }
```
