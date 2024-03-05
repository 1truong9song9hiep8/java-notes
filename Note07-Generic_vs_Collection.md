# Generic vs Collection
Generic là tính năng nổi bật nhất được giới thiệu ở Java 5.

## `hashCode()` và `equal()`
Mặc định lớp Object là lớp cha của tất cả các lớp trong java, và bản thân lớp Object này chứa một số method mà ta hay gặp như toString(), hasCode() và equal()...

toán tử `==` và hàm equal(): toán tử `==` so sánh các bit của đối tượng

# Collections
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

# Sử dụng Collection Framewor
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

Khi thêm/xóa phần tử, list mới sẽ báo lỗi, vì vậy hãy cẩn thận khi sử dụng các hàm 

