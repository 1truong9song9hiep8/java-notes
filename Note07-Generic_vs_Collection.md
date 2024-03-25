# Generic và Collection
## 1. `hashCode()` và `equal()`
Mặc định lớp Object là lớp cha của tất cả các lớp trong java, và bản thân lớp Object này chứa một số method mà ta hay gặp như toString(), hasCode() và equal()...

Toán tử `==` sẽ kiểm tra 2 biến có cùng tham chiếu đếm một đối tượng hay không (bằng cách so sánh từng bit).

Phương thức `equal()` sẽ kiểm tra giá trị của 2 biến có bằng nhau hay không.

Nếu không overrrid lại hàm `equal()` các đối tượng sẽ không thành mảng băm. và các đối tượng sẽ không được so sánh bằng nhau


Collections hold only Objects, but primitives can be autoboxed.
❑ Iterate with the enhanced for, or with an Iterator via hasNext() & next().
❑ hasNext() determines if more elements exist; the Iterator does NOT move.
❑ next() returns the next element AND moves the Iterator forward.
❑ To work correctly, a Map's keys must override equals() and hashCode().
❑ Queues use offer() to add an element, poll() to remove the head of the
queue, and peek() to look at the head of a queue.
❑ As of Java 6 TreeSets and TreeMaps have new navigation methods like
floor() and higher().
❑ You can create/extend "backed" sub-copies of TreeSets and TreeMaps.
Sorting and Searching Arrays and Lists (Objective 6.5)
❑ Sorting can be in natural order, or via a Comparable or many Comparators.
❑ Implement Comparable using compareTo(); provides only one sort order.
❑ Create many Comparators to sort a class many ways; implement compare().
❑ To be sorted and searched, a List's elements must be comparable.
❑ To be searched, an array or List must first be sorted.
Utility Classes: Collections and Arrays (Objective 6.5)
❑ Both of these java.util classes provide
 ❑ A sort() method. Sort using a Comparator or sort using natural order.
 ❑ A binarySearch() method. Search a pre-sorted array or List.
Two-Minute Drill 633
634 Chapter 7: Generics and Collections
❑ Arrays.asList() creates a List from an array and links them together.
❑ Collections.reverse() reverses the order of elements in a List.

Collections.reverseOrder() returns a Comparator that sorts in reverse.

2 interface List và Set đều có hàm `toArray()` để tạo mảng từ collection. 


# 2. Collections
Một số công việc mà bạn thường làm với collection: Thêm, xóa, tìm kiếm, truy xuất, duyệt phần tử.

**Odered**: Một collection được gọi là *odered* khi mà các phần tử trong nó được xác định bằng các chỉ mục.

**Sorted**: *sorted* collection là những collection mà thứ tự của các phần tử trong collection đó được sắp xếp theo một hoặc nhiều luật nào đó. Thứ tự của nó không liên quan đến việc một phần tử được thêm vào lúc nào. Việc sắp xếp vị trí của phần tử được dựa vào chính thuộc tính của nó, một số luật thông thường mà ta thấy là sắp xếp theo chữ cái hoặc con số, còn nếu phần tử là một object thì việc so sánh sẽ dựa vào hàm Comparable interface. Ngoài ra chúng ta cũng có thể sắp sếp dựa vào class Comparator, Chúng ta sẽ thảo luận về cách sử dụng cả Bộ so sánh và Bộ so sánh để xác định thứ tự sắp xếp ở phần sau của chương này.


Java cung cấp một bộ các interface, class, và thuật toán để lập trình viên dễ dàng làm việc với collection, được gọi là Collection Framework.
### List Interface
List quan tâm đến index. List cung cấp các method làm việc với index.

Tất cả 3 class implement từ List là ArrayList, Vector, LinkedList đều là các odered collection theo index
#### ArrayList
ArrayList là một odered collection và không sorted.

ArrayList được ưa dùng khi bạn muốn duyệt danh sách của bạn, hoặc truy xuất. Hiệu suất khi thêm hoặc xóa phần tử vào đầu của mảng là khá chậm khi các phần tử còn lại phải thay đổi lại index.


#### Vector
Vector là một collection ra đời khá sớm và nó đã trở nên khá lỗi thời.


Vector về cơ bản giống như ArrayList, nhưng các phương thức Vector được đồng bộ hóa để đảm bảo an toàn cho luồng. Vì vậy hiệu suất sẽ giảm đáng kể so với ArrayList.

Bạn có thể sử dụng ArrayList để thay cho Vector trong hầu hết các trường hợp, còn vấn đề về luồng, collection framework cũng cung cấp cho chúng ta một số method để làm việc với luồng.


*LinkedList* Linkedlist là một odered collection theo index, LinkedList sử dụng danh sách liên kết (Doubly Linked List) để lưu trữ các phần tử. Danh sách liên kết tức là một phần tử không lưu index mà sẽ lưu 3 giá trị gồm tham chiếu của phần tử trước nó, tham chiếu đến phần tử sau nó, và giá trị của nó.

hoặc xếp hàng. Hãy nhớ rằng LinkedList có thể lặp lại chậm hơn ArrayList,
nhưng đó là một lựa chọn tốt khi bạn cần chèn và xóa nhanh. Kể từ Java 5,
Lớp LinkedList đã được cải tiến để triển khai giao diện java.util.Queue. BẰNG
như vậy, giờ đây nó hỗ trợ các phương thức xếp hàng phổ biến: look(), poll() và Offer()

## Set Interface
Set quan tâm đến tính duy nhất, các phần tử trong set không được phép trùng lặp

**HashSet:** 
HashSet là một Tập hợp không được sắp xếp, không có thứ tự. Nó sử dụng mã băm
của đối tượng được chèn vào, do đó việc triển khai hashCode() của bạn càng hiệu quả hơn
hiệu suất truy cập tốt hơn bạn sẽ nhận được. Sử dụng lớp này khi bạn muốn có một bộ sưu tập không có sự trùng lặp và bạn không quan tâm đến thứ tự khi lặp lại nó.


**LinkedHashSet:** LinkedHashSet là một phiên bản odered của HashSet, các phần tử trong LinkedHashSet sử dụng danh sách liên kết để lưu trữ các phần tử, vì vậy bạn có thể duyêt qua các phần tử theo thứ tự khi được thêm vào.

### TreeSet


## Map Interface
Map quan tâm đến số nhận dạng duy nhất. Bạn ánh xạ một khóa duy nhất (ID) tới một giá trị cụ thể, trong đó cả khóa và giá trị đều là đối tượng. Có thể bạn khá quen thuộc với Maps vì nhiều ngôn ngữ hỗ trợ cấu trúc dữ liệu sử dụng cặp khóa/giá trị hoặc tên/giá trị. Việc triển khai Bản đồ cho phép bạn thực hiện những việc như tìm kiếm giá trị dựa trên khóa, yêu cầu tập hợp chỉ các giá trị hoặc yêu cầu tập hợp chỉ các khóa. Giống như Bộ, Bản đồ dựa vào phương thức bằng() để xác định xem hai khóa giống nhau hay khác nhau.

HashMap HashMap cung cấp cho bạn một Bản đồ không được sắp xếp, không có thứ tự. Khi bạn
cần một Bản đồ và bạn không quan tâm đến thứ tự (khi bạn lặp qua nó), thì
HashMap là con đường để đi; các bản đồ khác bổ sung thêm một chút chi phí. Ở đâu
các khóa nằm trong Bản đồ dựa trên mã băm của khóa, do đó, giống như HashSet, việc triển khai hashCode() của bạn càng hiệu quả thì bạn sẽ nhận được hiệu suất truy cập càng tốt.
HashMap cho phép một khóa null và nhiều giá trị null trong một bộ sưu tập.
Giao diện bản đồ (Mục tiêu kỳ thi 6.1) 563
Khi sử dụng HashSet hoặc LinkedHashSet, các đối tượng bạn thêm vào chúng
phải ghi đè hashCode(). Nếu họ không ghi đè hashCode(), thì Object.
Phương thức hashCode() sẽ cho phép nhiều đối tượng mà bạn có thể coi là "có ý nghĩa
bằng" để được thêm vào bộ "không cho phép trùng lặp" của bạn.
Hashtable Giống như Vector, Hashtable đã tồn tại từ thời Java thời tiền sử.
Để giải trí, đừng quên lưu ý sự không nhất quán khi đặt tên: HashMap so với Hashtable.
Viết hoa của t ở đâu? Ồ, bạn sẽ không cần phải đánh vần nó. Dù sao,
giống như Vector là một bản sao được đồng bộ hóa của ArrayList đẹp hơn, hiện đại hơn,
Hashtable là bản sao được đồng bộ hóa của HashMap. Hãy nhớ rằng bạn không
đồng bộ hóa một lớp, vì vậy khi chúng ta nói rằng Vector và Hashtable được đồng bộ hóa, chúng ta
chỉ có nghĩa là các phương thức chính của lớp được đồng bộ hóa. Một sự khác biệt khác,
Tuy nhiên, có phải là mặc dù HashMap cho phép bạn có các giá trị null cũng như một khóa null,
Hashtable không cho phép bạn có bất cứ thứ gì không có giá trị.
LinkedHashMap Giống như đối tác Set của nó, LinkedHashSet, bộ sưu tập LinkedHashMap duy trì thứ tự chèn (hoặc, tùy chọn, thứ tự truy cập). Mặc dù nó
sẽ chậm hơn một chút so với HashMap khi thêm và xóa các phần tử, bạn có thể
mong đợi sự lặp lại nhanh hơn với LinkedHashMap.
TreeMap Bây giờ bạn có thể đoán rằng TreeMap là một Bản đồ được sắp xếp.
Và bạn đã biết rằng theo mặc định, điều này có nghĩa là "được sắp xếp theo thứ tự tự nhiên của
các phần tử." Giống như TreeSet, TreeMap cho phép bạn xác định thứ tự sắp xếp tùy chỉnh (thông qua một
Có thể so sánh hoặc So sánh) khi bạn xây dựng TreeMap, nó chỉ định cách
các phần tử nên được so sánh với nhau khi chúng được sắp xếp. Kể từ
Java 6, TreeMap triển khai NavigableMap.


## Queue Interface
Queue Inteface được sử dụng để lưu trữ các phần tử được xử lý theo thứ tự FIFO (First In First Out). Tức là các phần tử không được đánh dấu bằng index hay key, phần tử nào được thêm vào trước sẽ đứng trước, phần tử nào được thêm vào sau sẽ đứng sau.

Queue hỗ trợ tất cả những method của Collection. 

**PriorityQueue** và **LinkedList** là 2 class implement Queue Interface, PriorityQueue được giới thiệu trong Java 5, **PriorityQueue** cho phép sắp xếp các phần tử theo thứ tự A-Z hoặc 1-9.







![image](https://github.com/1truong9song9hiep8/java-notes/assets/101247928/d53d4151-b60d-4cec-a056-7874d1862a10)


`Collection` Interface là interface cấp cao nhất của Collection framework, gần như mọi class đều implement interface nay

Những class liên quan đến Map đều **không** implement Collection interface.

![image](https://github.com/1truong9song9hiep8/java-notes/assets/101247928/0a01351b-e420-4e39-8dc1-3e8b0b7b0673)

# 3. Sử dụng Collection Framewor
Mục tiêu:
- Viết code sử dụng Navigableset và NavigableMap.
- Sử dụng `java.util.Comparator` và `java.lang.Comparable` để tùy chỉnh việc sắp xếp phần tử trong list và array.
- Biết được ảnh hưởng của "natural ordering" trong các hàm sorting.

Navigation Methods
Tìm kiếm trong TreeSets và TreeMaps, Java 5 cung cấp 2 interface mới là NavigableSet và `java.util.NavigableMap` 

Backed collection
Trong Java, Backed collection để chỉ những collection được liên kết với một collection khác, 2 collection này cùng chia sẻ chung nguồn dữ liệu, vì vậy bất cứ khi nào 1 trong 2 thay đổi thì cả 2 đều thay đổi.

Một số class trong gói java.util hỗ trợ backed collection bao gồm: **Collections**, **Arrays**, **List**, và **Set**, trong các class này sẽ có một số method sinh ra backed collection từ collection gốc.

Một số lưu ý: bởi vì 1 list tham chiếu đến list gốc, nếu như bạn thay đổi phàn tử trong list gốc mà phạm vi của nó vượt ngoài list mới thì list mới vẫn sẽ không thay đổi


## 4. Generic Type
Có thể bạn đã biết, Java cho phép khai báo các collection mà không cần khai báo kiểu dữ liệu kèm theo.

Một `ArrayList<Animal>` có thể chấp nhận các tham chiếu thuộc loại `Dog`, `Cat` hoặc bất kiểu dữ liệu nào là subtype của `Animal`(các lớp kế thừa hoặc triển khai).

Khi sử dụng genereic collection, không cần thiết phải ép kiểu để lấy các phần tử (loại được khai báo) ra khỏi collection. Với các bộ non-generic collection, ép kiểu là cần thiết.
```java
List<String> gList = new ArrayList<String>();
List list = new ArrayList();
// more code
String s = gList.get(0); // no cast needed
String s = (String)list.get(0); // cast required
```
Một generic collection có thể được truyền vào một method mà nó nhận vào một non-generic collection, nhưng kết quả có thể rất tệ. Trình biên dịch không thể ngăn phương thức chèn sai kiểu vào bộ sưu tập an toàn loại trước đó.

Thông tin về kiểu kiểu dữ liệu Generic không tồn tại lúc run-time, nó chỉ đảm bảo không lỗi trong quá trình biên dịch.

Tính đa hình không được áp dụng cho generic collection. Tuy nhiên mảng thì có thể.
```java
class Parent { }
class Child extends Parent { }
List<Parent> myList = new ArrayList<Child>(); // error
void foo(List<Animal> aList) { } // cannot take a List<Dog>
List<Animal> bar() { } // cannot return a List<Dog>

Parent[] myArray = new Child[3];
Object[] myArray = new JButton[3]; // yes
```
Để thực hiện tính đa hình, phải thực hiện cú pháp sau
```java
void addD(List<Dog> d) {} // can take only <Dog>
void addD(List<? extends Dog>) {} // take a <Dog> or <Beagle>
```
Khi sử dụng cú pháp đại diện `<?>` nó chỉ được gán không được truy cập hay sửa đổi

Quy ước khai báo generic là sử dụng `E` cho collection và `T` cho mọi thứ khác.

Một phương thức của class T phải khai báo kiểu T.
```java
public <T> void makeList(T t) { }
// Ở đây hàm trả về void, nhưng phải khai báo T để sử dụng.
```



```java
// Trước Java 5
ArrayList myList = new ArrayList(); // nó gần như là ArrayList<Object> myList = new ArrayList<>();
List myList = new ArrayList();
```
Các collection đó được gọi là non-generic collection, nó có thể chứa bất cứ thứ gì không phải là kiểu nguyên thủy. Điều này khá là khó chịu bởi chúng ta biết rằng Java rất nghiêm ngặt về kiểu dữ liệu, sẽ là một thảm họa nếu ta tính toán các collection mà nó có thể chứa string.

Generic có thể đảm bảo kiểu dữ liệu mà bạn mong muốn nó sử dụng.

cú pháp generic là đặt kiểu dữ liệu vào trong `<>`
Vấn đề về đa hình sẽ xuất hiện

sự kết hợp giữa generic collection và non-genenric? hẫy tương tượng bạn có một mảng genereic có kiểu integer, làm sao để đưa nó vào mảng không genereic

xem kểu sau


Khai báo generic
E là viết tắt của Element, còn T dùng cho những thứ không phải collection.
Make your own generic class:
Ví dụ bạn muốn tạo một cửa hàng cho thuê đồ và bạn tạo một class như sau:
```java
public class Rental {
 private List rentalPool;
 private int maxNum;
 public Rental(int maxNum, List rentalPool) {
 this.maxNum = maxNum;
 this.rentalPool = rentalPool;
 }
 public Object getRental() {
 // blocks until there's something available
 return rentalPool.get(0);
 }
 public void returnRental(Object o) {
 rentalPool.add(o);
 }
}
```
Tiếp theo bạn muốn cho thuê xe, bạn sẽ viết 1 class kết thừa từ nó.
```java
public class CarRental extends Rental {
    public CarRental(int maxNum, List<Car> rentalPool) {
        super(maxNum, rentalPool);
    }

    public Car getRental() {
        return (Car) super.getRental();
    }

    public void returnRental(Car c) {
        super.returnRental(c);
    }

    public void returnRental(Object o) {
        if (o instanceof Car) {
            super.returnRental(o);
        } else {
            System.out.println("Cannot add a non-Car");
            // probably throw an exception
        }
    }
}
```
vấn đề xảy ra,


Sau Java 5 bạn phải khai báo kiểu khi khai báo list trong Java, vậy các kỹ sư Java đã làm thế nào?




Khi thêm/xóa phần tử, list mới sẽ báo lỗi, vì vậy hãy cẩn thận khi sử dụng các hàm 

