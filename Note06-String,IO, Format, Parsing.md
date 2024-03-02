# JAVA NOTE06: String I/O, Formating, Parsing
## String, String Buffer, StringBuilder
### String
String là những đối tượng bất biến, khi một đối tượng String được tạo, nó không bao giờ có thể được thay đổi.

Bởi vì String là bất biến nên các hàm làm việc với String sẽ tạo ra một giá trị mới, lúc này ta phải tham chiếu (gán lại) đến nó mới thấy được sự thay đổi.
```java

String x = "Java";
x.concat(" Rules!");
System.out.println("x = " + x); // kết quả "x = Java", bởi vì giá trị Java Rules! không được gán cho biến nào hết.

x = x.concat(" Rules!");
System.out.println("x = " + x); // kết quả "x = Java", bởi vì giá trị "Java Rules!" đã được gán cho biến x.
```
Việc tạo nhiều biến trong bộ nhớ heap khi làm việc với String sẽ khiến cho bộ nhớ bị đầy, để làm việc hiểu quạ hơn, Java cung cấp 1 vùng nhớ gọi là String constant pool, khi một chuỗi tồn tại nó sẽ kiểm tra có trong một vùng nhớ đó chưa, nếu có nó sẽ tham chiếu đến biến được tạo trước đó

#### Một số phương thức của lớp String
```java
String x = "Hello String!";

x.charAt();
concat();
equalsIgnoreCase()
length()
replace()
substring();
toLowerCase();
toString();
toUpperCase();
trim();
```
### StringBuffer và StringBuilder
Như đã đề cập ở trước đó, một String khi thay đổi quá nhiều sẽ tạo ra rất nhiều giá trị trong bộ nhớ, StringBuffer và StringBuilder sinh ra để làm việc với các chuỗi hay bị thay đổi.

StringBuilder được ra mắt vào Java 5 có các API hoàn toàn gống với StringBuffer, StringBuilder không an toàn cho thread, các hàm của nó không được đồng bộ hóa. Sun khuyên bạn nên sư dụng String builder thay cho string buffer bất cư khi nào nếu có thể vì nó nhanh hơn
các hàm của StringBuffer đều dược đánh dấu là `synchronized` nên nó an toàn cho luồng

Các method của StringBuffer và StringBuilder đều thay đổi giá trị trong Heap chứ không thêm mới nên chúng ta không cần gán lại giá trị như String.
```java
StringBuilder sb = new StringBuilder("abc");
sb.append("def").reverse().insert(3, "---");
System.out.println( sb ); // output is "fed---cba"
```
#### Một số method quan trọng của StringBuffer và StringBuilder
public synchronized StringBuffer append(String s) 

public StringBuilder delete(int start, int end) 
```java
StringBuilder sb = new StringBuilder("0123456789");
System.out.println(sb.delete(4,6)); // output is "01236789"


public StringBuilder insert(int offset, String s)
StringBuilder sb = new StringBuilder("01234567");
sb.insert(4, "---");
System.out.println( sb ); // output is "0123---4567"


StringBuffer s = new StringBuffer("A man a plan a canal Panama");
sb.reverse();
System.out.println(sb); // output: "amanaP lanac a nalp a nam A"


StringBuffer sb = new StringBuffer("test string");
System.out.println( sb.toString() ); // output is "test string"
```
## 2. Thao Tác Với File Và I/O
Java cung cấp cho chúng ta một số class để thao tác với file:
- File: đại diện cho đường dẫn của file hoặc thư mục.
- FileReader: đối tượng dùng để đọc các ký tự riêng lẻ, thường được bọc bởi các đối tượng khác để tăng hiệu suất đọc file
- BufferedReader: đối tượng dùng để đọc số lượng lớn ký tự sau đó đưa vào bộ nhớ
- FileWriter: dùng để ghi ký tự vào file
- BufferedWriter: dùng để ghi nhiều ký tự vào file
#### Tạo file 
```java
File file = new File("fileWrite1.txt");
//lúc này file chưa được tạo thực tế, để tạo file, sử dụng hàm dưới đây
file.createNewFile();
```
sử dụng FileReader và FileWrite để đọc và ghi file

FileWriter fw = new FileWriter(file);
// tạo ra một file thực sự trong ổ đĩa và một đối tượng FileWrite đọc ký tự vào dile đó.
fw.write("howdy\nfolks\n"); // tiến hành ghi ký tự vào file, lưu ý 
fw.flush();
fw.close();

## 3. Tuần Tự Hóa (Serialization)
**Sự tuần tự hóa không áp dụng cho các static member class**

## 4. Date, Numbers và Currency
Java cung cấp một tợp hợp các class hỗ trợ làm việc với ngày tháng, số và tiền tệ. Date, Calendar, DateFormat, Locate là 4 class được sử dụng nhiều nhất.

Khi làm việc với ngày tháng và con số, ta sẽ sử dụng nhiều lớp, điều quan trọng là kết hợp chúng như thế nào.

![image](https://github.com/1truong9song9hiep8/java-notes/assets/101247928/43de11b7-9555-49ba-a1e3-9fc54989cc2d)





## 4. Format

### Token Hóa
Token hóa là tiến trình lấy phần lớn dữ liệu và chia nó ra thành nhiều phần nhỏ hơn và lưu vào trong các biến, thường thấy nhất là chia chuỗi thành nhiều phần dựa vào dấu phẩy.

Việc token hóa cần 2 thứ, một là mã nguồn, 2 là điều kiện để phân chia, ví dụ dấu , phân chia theo chữ số...

Token hóa với String.split()




### Format với `format()`
Hai phương thức `format()` và `print()` hoạt động giống nhau (người ta đồn rằng `print()` được tạo ra để làm hài lòng những người lập trình C)
