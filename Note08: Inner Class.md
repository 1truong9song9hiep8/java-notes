# Inner Class

## Regular Inner Class

## Method-Local Inner Class
Inner class (lớp lồng) là một lớp được khai báo bên trong một class khác.
```java
public class OuterClass {
    private int outerField;

    // ...

    public class InnerClass {
        private int innerField;

        public void innerMethod() {
            // Access outer class members
            outerField = 10;
            // ...
        }
    }
}
```
Một inner class được đặt ngang hàng với các method trong outer class, tuy nhiên bạn vẫn có thể đặt một class bên trong một hàm, tuy nhiên đoạn code đó sẽ vô dụng và trình biên dịch sẽ không biết đến.

## Anonymous Inner Class

## Static Nested Class
Một static nested class là một static class nằm bên trong 1 class khác.
```java
class BigOuter {
 static class Nested { }
}
```
Một số đặc điểm của static nested class:
- nó có thể được truy cập mà không cần phải khởi tạo instance của outer class, cú pháp truy cập `outerClass.StaticInnnerClass.method()`
- nó có quyền truy cập đến các static member, và không có quyền truy cấp đến các non-static member của outer class,

# consum
## 1. Inner Classes
Chúng ta có thể khai báo một class bên trong một class khác, các class đó được gọi là các inner class.

Một inner class "thông thường" được khai báo bên trong class và bên ngoài bất cứ method hoặc khối mã nào.

Một inner class cũng được xem là một class member của outer class, vì vậy nó có thể được đánh dấu bởi access modifier cũng như `final` hoặc `abstract`. Xin nhắc lại lần nữa là `final` và `abstract` không thể đi cùng nhau.

Một thể hiện của lớp bên trong chia sẻ mối quan hệ đặc biệt với một thể hiện của lớp kèm theo. Mối quan hệ này cho phép lớp bên trong truy cập vào tất cả các thành viên của lớp bên ngoài, bao gồm cả những thành viên được đánh dấu là riêng tư.

Để khởi tạo một inner class, bạn phải khởi tạo outer class trước.
```java
MyOuter mo = new MyOuter();
MyOuter.MyInner inner = mo.new MyInner();
```
Từ khóa `this` bên trong inner class để chỉ tham chiếu đến instance của inner class đó. Nếu muốn trỏ đến outer class thì ta phải Khai báo tên của outer class trước this, ví dụ: `var outer = OuterClass.this;`

## Method-Local Inner Classes
Một class cũng có thể được khai báo bên trong một method của một class khác, khi đó class đó gọi là **Method-local inner class**.

Để sử dụng method-local inner class bạn phải khởi tạo chúng bên trong method, và đoạn code khởi tạo phải nằm sau đoạn code khai báo method-local inner class.
```java
public class OuterClass {
    public void outerMethod() {
        InnerClass inner = new InnerClass(); // LỖI: khởi tạo nằm trước khai báo
        class InnerClass {
            public void innerMethod() {
            }
        }
        InnerClass inner = new InnerClass(); // khởi tạo phải nằm sau khai báo
        inner.innerMethod();
    }
}
```
Các method-local inner class có thể truy cập và sử dụng các biến cục bộ (local variables) của phương thức nơi nó được khai báo, VỚI MỘT ĐIỀU KIỆN là biến đó phải là final hoặc giá trị của nó không bị gán lại.

## Anonymous Inner Classes
❑ Anonymous inner classes have no name, and their type must be either a
subclass of the named type or an implementer of the named interface.
❑ An anonymous inner class is always created as part of a statement; don't
forget to close the statement after the class definition with a curly brace. This
is a rare case in Java, a curly brace followed by a semicolon.
❑ Because of polymorphism, the only methods you can call on an anonymous
inner class reference are those defined in the reference variable class (or
interface), even though the anonymous class is really a subclass or implementer of the reference variable type.
❑ An anonymous inner class can extend one subclass or implement one
interface. Unlike non-anonymous classes (inner or otherwise), an anonymous
inner class cannot do both. In other words, it cannot both extend a class and
implement an interface, nor can it implement more than one interface.
❑ An argument-defined inner class is declared, defined, and automatically
instantiated as part of a method invocation. The key to remember is that the
class is being defined within a method argument, so the syntax will end the
class definition with a curly brace, followed by a closing parenthesis to end
the method call, followed by a semicolon to end the statement: });
Static Nested Classes
❑ Static nested classes are inner classes marked with the static modifier.
❑ A static nested class is not an inner class, it's a top-level nested class.
❑ Because the nested class is static, it does not share any special relationship
with an instance of the outer class. In fact, you don't need an instance of the
outer class to instantiate a static nested class.
❑ Instantiating a static nested class requires using both the outer and nested
class names as follows:
BigOuter.Nested n = new BigOuter.Nested();
❑ A static nested class cannot access non-static members of the outer class,
since it does not have an implicit reference to any outer instance (in other
words, the nested class instance does not get an outer this reference)
