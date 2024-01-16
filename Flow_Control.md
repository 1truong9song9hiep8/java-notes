# Flow Control
## Câu lệnh If/ If-else
Một số khuyến nghị
- Hãy luôn đặt dấu {} sau if bất kể nó chỉ có 1 dòng, vì dễ dàng đọc.
- đối với biểu thức trong if, nếu có nhiều logic với các toán tử && || thì khi biêt thức trước && sai thì sẽ không cần xem lại các biểu thức sau nữa.
- if chỉ chấp nhận kiểu boolean, tức 0 và 1 cũng không được chấp nhận trong java
- bạn cũng có thể gán giá trị boolean cho biến trong if, ví dụ : boolean a = false, if (a=true) lúc này a sẽ được gán trước sau đó mới thực hiện kiểm tra trong biểu thức.

## switch Statement
swich được dùng để thay thế cho if-else
```java
switch (expression) {
 case constant1: code block
 case constant2: code block
 default: code block
}
```
giá trị trong câu lệnh switch phải là char, byte, short, int hoặc enum trong Java 6, và double, long, float là không được chấp nhận
lưu ý 2: một biến byte = 1 không thể so sánh với giá trị 128 bởi vì nó out range
2 case trùng nhau cũng không được phép
trường hợp không có break thì nếu một case đúng với điều kiện, các case sau sẽ được thực hiện mà không cần kiếm tra điều kiện
case default luôn đáp ứng được điều kiện, case default có thể đặt ở bất cứ nơi nào không nhất thiết phải là cuối. vì vậy case default sẽ thường đặt ở cuối. lưu ý khi đặt case default mà không có beak thì mọi case dưới default đều sẽ được thực thi. nó gọi là fall-throught sự rơi


## Loop
