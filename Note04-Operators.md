# JAVA NOTE04: OPERATORS
Java cung cấp một bộ các toán tử để làm việc với biến bao gồm: Toán tử gán (), toán tử số học, toán tử quan hệ, toán tử logic, toán tử điều kiện
## 1. Toán tử gán
Trong Java thực tế có tận 11 kiểu toán tử gán nhưng chỉ có 4 loại thường được sử dụng (+=, -=, *=, và /=), và thứ tự ưu tiên của các toán tử cũng là một điều đáng lưu ý:
```java

```
## 2. Toán tử quan hệ (Relational operators)
Có tổng cộng 6 toán tử quan hệ (`<`, `<=`, `>`, `>=`, `==`, `!=`), kết quả của biểu thức sử dụng toán tử quan hệ luôn trả về kiểu dữ liệu `boolean`.

Các toán tử (`<`, `<=`, `>`, `>=`) có thể dùng để so sánh số nguyên, số có dấu chấm phẩy động, và ngay cả ký tự.

Các toán tử (`==`, `!=`) được dùng để so sánh: các số, các ký tự, các biến kiểu boolean, các biến tham chiếu.
```java
boolean result;
// Có thể sử dụng toán tử == với kiểu dữ liệu nguyên thủy khác nhau
result = 5.0 == 5L; // Hợp lệ, kết quả là true
result = false == true; // Hợp lệ, kết quả là false
```
Các toán tử (`==`, `!=`) khi được dùng để so sánh với các biến tham chiếu thì sẽ có ý nghĩa là nó sẽ kiểm tra xem 2 biến này có cùng tham chiếu đến một đối tượng hay không, bởi vì biến == là so sánh bit, nên nó sẽ so sánh kỹ càng hơn.
```java
JButton a = new JButton("Exit");
 JButton b = new JButton("Exit");
 JButton c = a;
 System.out.println("Is reference a == b? " + (a == b)); //Is reference a == b? false
 System.out.println("Is reference a == c? " + (a == c)); //Is reference a == c? true
```
Các toán tử (`==`, `!=`) cũng được sử dụng để so sánh enum.
```java
enum Color {RED, BLUE};
Color c1 = Color.RED;
Color c2 = Color.RED;

boolean result01 = c1 == c2; //true
boolean result02 = c1.equals(c2); //true
```
#### So sánh bằng hàm `instanceOf()`
Trong Java, toán tử instanceof được sử dụng để kiểm tra xem một đối tượng có thuộc vào một lớp cụ thể hay không, hoặc có thuộc vào một lớp con của lớp cụ thể đó hay không.

Khi một class implement một interface thì toán tử instanceof cũng trả về true. điều này cũng đúng đối với một sublass với một interface của superclass.

instanceof cũng có thể dùng với null, và tất nhiên kết quả luôn là false

Việc cố gắng sử dụng `instanceof` cho hai đối tượng thuộc class khác nhau sẽ dẫn đến lỗi biên dịch.
![image](https://github.com/1truong9song9hiep8/java-notes/assets/101247928/e02bc00a-19ce-4f1c-ae98-01d24ccca884)

## Toán tử số học
Toán tử số học bao gồm: cộng(+), trừ(-), nhân(*), chia lấy phần nguyên(/), chia lấy phần dư(%).

Các toán tử `*`, `/` có mức độ ưu tiên cao hơn `+` và `-`

Toán tử `+` cũng có thể sử dụng để nối chuỗip

