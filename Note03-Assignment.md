# Java Note03: Phép Gán (Assigment)
## Stack và Heap
- Instance variables và objects được lưu trong vùng nhớ heap.
- Local variables được lưu trong vùng nhớ stack.
  ưu ý: Các tên biến local lưu ở trong stack nhưng nó lại tham chiếu đến vùng nhớ ở trong heap. thông thường stack sẽ lưu trữ tên hàm và những tên biến trong nó, còn giá trị nằm trong heap
```java
class Collar {}

class Dog {
    Collar c; // instance variable
    String name; // instance variable

    public static void main(String[] args) {
        Dog d; // local variable: d
        d = new Dog();
        d.go(d);
    }

    void go(Dog dog) { // local variable: dog
        c = new Collar();
        dog.setName("Aiko");
    }

    void setName(String dogName) { // local var: dogName
        name = dogName;
    }
}
```
