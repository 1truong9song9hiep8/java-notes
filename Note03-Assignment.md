# Java Note03: Phép Gán (Assigment) 121
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
## Quản lý bộ nhớ và tiến trình thu gom rác trong Java
Java có một chương trình thu gom rác gọi là Bargare Collector, nó sẽ tự động chạy ngầm và tự động xóa những dữ liệu không được sử dụng trong bộ nhớ Heap.

Bargare Collector được quản lý bởi JVM. JVM sẽ quyết định khi nào thì Bargare Collector chạy, chúng ta có thể gọi JVM nhưng không chắc rằng JVM có gọi Bargare Collector hay không.

Bargare Collector hoạt động như thế nào? Một chương trình có thể có nhiều thread, mỗi thread có stack riêng, Một đối tượng được xem là đủ điều kiện để được thu gom là đối tượng mà các thread không gọi đến nó nữa. một thread truy cập vào một đối tượng khi tham chiếu của nó ở trong stack

Một số cách để loại bỏ tham chiếu khỏi đối tượng: set nó về null, gán giá trị cho khác, các đối tượng được tạo ra trong phương thức và khi nó kết thúc cũng đủ điều kiện. Tuy nhiên một đối tượng được return thì giá trị của nó sẽ được gán cho biến của phương thức gọi nó nên nó sẽ là ngoại lệ.


Như ta đã biết việc thu gom rác là tự động, nhưng Java cũng cung cấp cho chúng ta một só hàm để cho phép JVM thực hiện thu gom rác đó là sư dụng hàm cg()


