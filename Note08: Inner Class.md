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
