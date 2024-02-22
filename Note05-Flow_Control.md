# Java Note05: Flow Control
# Câu Lệnh If và Switch
Dấu ngoặc nhọn sau lệnh `if` là tùy chọn, nhưng vẫn khuyến khích đặt nó trong code của ban.
```java
if(x>3)
  print("x>3"); // hợp lệ nhưng không được khuyến khích

if(x>5){
  print("x>5"); // được khuyến khích thêm dấu {}
}
```
nếu không đặt dấu {} thì câu lệnh else sẽ thuộc về lệnh if gần nhất, bất kể bạn có cố gắng bao nhiều dòng nữa.

Tránh đặt câu lệnh if bên trong câu lệnh if hoặc else, điều này gây khó đọc code của bạn hơn.

## Biểu thức so sánh trong câu lệnh if
Biểu thức trong if phải trả về kiểu boolean
niếu có nhiều biểu thức ngang hàng thì nó sẽ tính toán lần lượt từ phải sang trái
Đối với biểu thức có phép | thì Java chỉ tìm biểu thức ngắn hơn để kiểm tra, điều này khá quan trọng khi bạn phải viết test để cover hết các tường hợp

cho đoạn code sau:
```java
boolean boo = false;
if (boo = true) { }
```
Kết quả là gì? kết quả vẫn chạy được và boo lúc này được gán bằng true nên biểu thức trong if sẽ được chạy.

### Câu Lệnh Switch
`switch` được sử dụng khi bạn muốn thay thế nhiều câu lệnh `if-else`.

Biểu thức trong `switch` chỉ cho phép `char, byte, short, int`, `enum` trong Java 6 và String trong Java 7. Ngay cả `long` `float`, `double` cũng không được chấp nhận.

Giá trị trong `case` phải cùng kiểu dữ liệu, và phải được khai báo là constant
```java
final int a = 1;
final int b;
b = 2;
int c = 4;
int x = 0;
switch (x) {
 case a: // ok
 case b: // compiler error
 case c: // compiler error
```
Khi giá trị trong case lớn hơn trong swithc thì sao, ví dụ case 128 cho byte, lúc này sẽ báo lỗi vì Java sẽ tự động ép sang kiểu int

Giá trị trong case không được trùng nhau.

Câu lệnh break trong switch-case
Luồng thực thi của switch-case là các case sẽ được đánh giá từ trên xuống và nếu 1 case match thì mọi case dưới sẽ luôn match, chúng ta gọi đó là fall-through, để đảm bảo nó chỉ mattch với 1 case bạn phải đặt break sau mỗi casse

default là option nó được sử dụng khi không có case nào hợp

default không cần phải đặt cuôis của câu lệnh switch




