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

## Vòng lặp
### Vòng lặp while và `do-while`
Vòng lặp while được dùng khi chúng ta không cần biết chính xác số lần lặp lại. Cú pháp của vòng lặp `while`.
```java
int x = 2;
while(x == 2) {
 System.out.println(x);
 ++x;
}
```
code trong do sẽ được thực hiện sau đó nó sẽ kiểm tra điều kiện while để quyết định có lặp lại hay không.
```java
do {
 System.out.println("Inside loop");
} while(false); // với câu lệnh do-while thì sau while phải có dấu ";"
```
### Vòng lặp `for`
Vòng lặp for về sau được gọi là vòng lặp for cơ bản, bởi vì sau java 6 thì một vòng lặp for khác gọi là vòng lặp for tăng cường chuyên được dùng để duyệt mảng và colleciton.

luồng đi của vòng lặp: khởi tạo biến > kiểm tra biến > thực thi mã > tăng hoặc giảm biến đếm.

Vòng lặp for gồm 3 phần: phần khởi tạo biến đếm, phần điều kiện kết thúc và phần thay đổi giá trị biến đếm. Mỗi phần cách nhau bởi dấu ";".
```java
for (/*Initialization*/ ; /*Condition*/ ; /* Iteration */) {
 /* loop body */
}
for (int i = 0; i<10; i++) {
 System.out.println("i is " + i);
}
```
Phần khai báo biến đếm: bạn có thể khởi tạo nhiều biến, cách nhau bởi dấu phẩy
```java
for (int x = 10, y = 3; y > 3; y++) { }
```
biến khởi tạo trong vòng lặp for có thể có bất kỳ kiểu dữ liệu nào mà Java hỗ trợ. 

Phạm vi của biến chỉ nằm trong câu lệnh `for`

- Phần kiểm tra điều kiện:
  - Biểu thức trong for phải trả về boolean
  - Biểu thức có thể phức tạp : `for (int x = 0; ((((x < 10) && (y-- > 2)) | x == 3)); x++) { }`
  - Biến trong biểu thức không cần thiết phải khai báo trong phần khởi tạo của vòng lặp
    ```java
    int y = 0;
    for (int x = 0;y > 5; x ++){ }
    ```

Phần lặp biến: 
- phần lặp sẽ chạy sau phần thân của vòng lặp `for`.
- `break`, `return` `System.exist()` được dùng để dừng vòng lặp theo mong muốn.
- phần lặp biến la tùy chọn, bạn thậm chí đặt một câu lệnh khác cũng không xảy ra lỗi gì
```java
int b = 3;
for (int a = 1; b != 1; System.out.println("iterate")) {
 b = b - a;
}
```

Lưu ý cả 3 phần đều là tùy chọn, mọi thứ đều không có lỗi khi không khai báo.
```java
for( ; ; ) {
 System.out.println("Inside an endless loop");
}
```
vòng lặp trên sẽ là vòng lặp vô hạn "x=+1" sẽ là vô hạn bởi phép này sẽ là phép gán cho 1 chứ không phải +=

## Vòng lặp tăng cường
Vòng lặp for tăng cường được giới thiệu vào trong Java 6 , vòng lặp tăng cường gồm 2 phần: phần khởi tạo và list.
biến phải được khai báo trong phần khởi tạo, không được khởi tạo bên ngoài
list có thể dc khai báo trong : for (int x: new int[]{1, 2, 3, 4, 5});

### Gán nhãn câu lệnh (Labeled statement)
Gán nhãn câu lệnh cho phép đặt tên cho một câu lệnh hoặc một luồng điều khiển, giúp thao tác với luồng điều khiển thông qua nhãn gán.

Labeled statement trong Java thường được dùng cho các luồng điều khiển `while` hoặc `for`. (tuy nhiên chúng không được khuyến khích sử dụng vì nó có thể làm cho mã trở nên khó hiểu và khó bảo trì.)
```java
// labeled statement trong while
loop:
while (true) {
    // Thực hiện các công việc trong vòng lặp

    if (someCondition) {
        break loop; // Thoát khỏi vòng lặp khi someCondition được thỏa mãn
    }
}

// labeld statement trong for
outerLoop:
for (int i = 0; i < 5; i++) {
    innerLoop:
    for (int j = 0; j < 3; j++) {
        if (i == 2 && j == 1) {
            break outerLoop; // Nhảy khỏi vòng lặp for bên ngoài
        }
        System.out.println("i: " + i + ", j: " + j);
    }
}

```
### Xử lý Exception
Ngoại lệ là một sự kiện sảy ra làm thay đổi luồng đi bình thường của chương trình, ví dụ chia một số cho 0, hoặc truy xuất đến một phần tử rỗng...

Khi một ngoại lệ xảy ra, ta nói nó được `ném` ra, và lúc này Java sẽ tự động khởi tạo một đối tượng Exception, để bắt được đối tượng này, chúng ta phải sử dụng try-catch
### Bắt và xử lý Exception với `try-catch`
Khối finally được dùng sau khối catch và nó sẽ luôn chạy bất kể có ngoại lệ xảy ra hay không. Ngay cả khi khối try có return thì khối finally vẫn chạy trước khi return.

Khối finally là tùy chọn, và khối catch cũng là tùy chọn


