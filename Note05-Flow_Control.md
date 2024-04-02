# Java Note05: Flow Control
## 1. Câu Lệnh If và Switch
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



Biểu thức hợp pháp duy nhất trong câu lệnh if là biểu thức boolean, nói cách khác là biểu thức phân giải thành biến boolean hoặc biến Boolean.
❑ Chú ý các phép gán boolean (=) có thể bị nhầm lẫn với boolean
kiểm tra đẳng thức (==):
  boolean x = sai;
if (x = true) { } // một phép gán, vì vậy x sẽ luôn đúng!
❑ Dấu ngoặc nhọn là tùy chọn cho các khối if chỉ có một câu lệnh điều kiện. Nhưng hãy cẩn thận với những vết lõm gây hiểu lầm.
❑ Các câu lệnh switch chỉ có thể đánh giá theo các kiểu dữ liệu enum hoặc byte, short, int và char. Bạn không thể nói,
  dài s = 30;
  (các) công tắc { }
❑ Hằng số kiểu chữ phải là biến bằng chữ hoặc biến cuối cùng hoặc một biểu thức hằng, bao gồm cả enum. Bạn không thể có trường hợp bao gồm biến không phải cuối cùng hoặc một phạm vi giá trị.
❑ Nếu điều kiện trong câu lệnh switch khớp với một hằng số case, việc thực thi sẽ chạy qua tất cả mã trong switch theo sau câu lệnh case khớp cho đến khi gặp câu lệnh break hoặc phần cuối của câu lệnh switch. Nói cách khác, trường hợp khớp chỉ là điểm vào trong khối trường hợp, nhưng trừ khi có câu lệnh break, trường hợp khớp sẽ là
không phải là mã trường hợp duy nhất chạy.
❑ Từ khóa mặc định nên được sử dụng trong câu lệnh switch nếu bạn muốn chạy một số mã khi không có giá trị trường hợp nào khớp với giá trị điều kiện.
❑ Khối mặc định có thể được đặt ở bất kỳ đâu trong khối chuyển đổi, vì vậy nếu không có trường hợp nào khớp, khối mặc định sẽ được nhập và nếu mặc định không chứa dấu ngắt thì mã sẽ tiếp tục thực thi (chuyển tiếp) cho đến hết của switch hoặc cho đến khi gặp câu lệnh break.




## 2. Vòng lặp
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



Một câu lệnh for cơ bản có ba phần: khai báo và/hoặc khởi tạo, đánh giá boolean và biểu thức lặp.
❑ Nếu một biến được tăng hoặc đánh giá trong vòng lặp for cơ bản, thì biến đó phải được khai báo trước vòng lặp hoặc trong phần khai báo vòng lặp for.
❑ Một biến được khai báo (không chỉ được khởi tạo) trong phần khai báo vòng lặp for cơ bản không thể được truy cập bên ngoài vòng lặp for (nói cách khác, mã bên dưới vòng lặp for sẽ không thể sử dụng biến đó).
❑ Bạn có thể khởi tạo nhiều biến cùng loại trong phần đầu tiên của khai báo vòng lặp for cơ bản; mỗi lần khởi tạo phải được phân tách bằng dấu phẩy.
❑ Một câu lệnh for nâng cao (mới kể từ Java 6), có hai phần, phần khai báo và biểu thức. Nó chỉ được sử dụng để lặp qua các mảng hoặc bộ sưu tập.
❑ Với for nâng cao, biểu thức là mảng hoặc tập hợp mà bạn muốn lặp qua đó.
❑ Với for nâng cao, khai báo là biến khối, có kiểu tương thích với các phần tử của mảng hoặc tập hợp và biến đó chứa giá trị của phần tử cho lần lặp đã cho.
❑ Bạn không thể sử dụng một số (cấu trúc ngôn ngữ kiểu C cũ) hoặc bất kỳ thứ gì không đánh giá thành giá trị boolean làm điều kiện cho câu lệnh if hoặc cấu trúc vòng lặp. Ví dụ: bạn không thể nói if(x), trừ khi x là biến boolean.
❑ Vòng lặp do sẽ vào phần thân vòng lặp ít nhất một lần, ngay cả khi điều kiện kiểm tra không được đáp ứng


Một câu lệnh break không được gắn nhãn sẽ khiến vòng lặp hiện tại của cấu trúc vòng lặp trong cùng dừng lại và dòng mã theo sau vòng lặp sẽ chạy.
❑ Câu lệnh continue không được gắn nhãn sẽ khiến: quá trình lặp hiện tại của vòng lặp trong cùng dừng lại, điều kiện của vòng lặp đó được kiểm tra và nếu điều kiện được đáp ứng, vòng lặp sẽ chạy lại.
❑ Nếu câu lệnh break hoặc câu lệnh continue được gắn nhãn, nó sẽ gây ra hành động tương tự xảy ra trên vòng lặp được gắn nhãn chứ không phải vòng lặp trong cùng.

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
Xử lý ngoại lệ để đảm bảo chương trình vẫn chạy mà không bị dừng lại khi ngoại lệ xảy ra
```java
// chương trình sẽ bị dừng lại ngay lần lặp đầu tiên bởi 1 ngoại lệ xảy ra mà không được bắt
for (int x = 0; x <10; x++){
                int y = x/0;
                System.out.println(y);
        }

// xử lý ngoại lệ với try-catch giúp chúng ta tiếp tục vòng lặp mà không bị gián đoạn
for (int x = 0; x <10; x++){
            try{
                int y = x/0;
                System.out.println(y);
            } catch (Exception e){
                System.out.println(e);
            }

        }
```

Khi một ngoại lệ xảy ra, ta nói nó được `ném` ra, và lúc này Java sẽ tự động khởi tạo một đối tượng Exception, để bắt được đối tượng này, chúng ta phải sử dụng try-catch
### Bắt và xử lý Exception với `try-catch`
Khối finally được dùng sau khối catch và nó sẽ luôn chạy bất kể có ngoại lệ xảy ra hay không. Ngay cả khi khối try có return thì khối finally vẫn chạy trước khi return.

một khối try phải đi cùng với một khối catch hoặc finally, try không thể đi một mình. các khối phải liền mạnh, không được phép thêm bất kì code nào ngoài 3 khối

một khối try có thể kết hợp được với nhiều khối catch, nhưng chỉ có duy nhất 1 khối finally
một đoạn code hợp lệ là đoạn code bao gồm cả 3 phần try-catch-finally
```java
try {
 // do stuff
} catch (SomeException ex) {
 // do exception handling
} finally {
 // clean up
}
```
Sự lan truyền của ngoại lệ
Điều gì sảy ra khi một khối `try` xảy ra ngoại lệ mà không có khối `catch`? Về cơ bản, khi ngoại lệ không được bắt ở hàm xảy ra ngoại lệ, nó vẫn có thể được bắt ở hàm gọi hàm đó, hoặc hàm gọi hàm đó nữa. nó gọi là sự lan truyền ngoại lệ. và khi một ngoại lệ không được bắt và xử lý thì nó sẽ khiến chương trình của bạn dừng lại.

### Định nghĩa Exception
Trong Java các ngoại lệ đều có một class đại diện cho nó, khi ngoại lệ xảy ra thì một instance của class đó sẽ được khởi tạo.

Mọi class ngoại lệ trong java đều kế thừa từ 1 class đó là Exception class, dưới đây là cấu trúc của ngoại lệ
![image](https://github.com/1truong9song9hiep8/java-notes/assets/101247928/58335ba4-047c-456b-be5d-0e43e2394fc2)

các Error thường không xuất phát từ chương trình của bạn, phần lớn là về các trục trặc kỹ thuật, và những error xảy ra sẽ không thể được xử lý trong chương trìnhNói chung, ứng dụng của bạn sẽ không thể khôi phục sau Lỗi, do đó bạn không bắt buộc phải xử lý chúng.

khi bạn bắt 1 ngoại lệ cha thì trong khối try xuất hiện ngoại lệ con của nó thì khối catch vẫn có thể bắt được chúng. tuy nhiên điều này không được khuyến khích, chúng tôi khuyến khích bạn bắt nhiều ngoại lệ chi tiết càng tốt. bởi mục tiêu để 

các khói lệnh catch khi có cha-con phải theo thứ tự từ con đến cha nếu không sẽ bị lõi biên dịch.

vậy làm thế nào mà ta biết được một hàm nào đó sẽ nếm ngoại lệ ra để chúng ta bắt chúng? Java quy định các ngoại lệ không phải RuntimeException đều bắt buộc phải khai báo

Khi một hàm của bạn tự ném ra một checkedException thì hàm đó phải được khai báo throws hoặc try catch để bắt

Error cũng có thẻ được ném và bắt lấy, nhưng chúng ta không khuyến khích bởi vì chẳng có cách nào giải quyết ổn thỏa khi một error xảy ra. 
một ngoại lệ được bắt cần được xử lý

một ngoại lệ cũng có thể được ném đi tiếp sau khi bắt được chúng.

khi bạn throw một ngoại lệ trong khối catch thì hàm cũng phải khai báo throws
một overrrider method không thể throws một expceition có phạm vi lớn hơn phương thức mà nó ghi đè

nếu trong khối finally xảy ra ex thì chương trình sẽ không thể bắt được



Một số Exception và Error trong Java
![image](https://github.com/1truong9song9hiep8/java-notes/assets/101247928/a12f94f8-6443-4b1a-81e2-e2eabb76109b)

assertion mechain
Cơ chế khẳng định (assertion mechanism) trong Java là một công cụ mạnh mẽ để kiểm tra các giả định (conditions) trong mã. Nó giúp đảm bảo rằng các giả định đó đúng trong quá trình phát triển và kiểm tra chương trình.
 khi một exception tại dòng x xảy ra thì đoạn code dưới x sẽ không được thực thi nữa

ác ngoại lệ có hai loại: được kiểm tra và không được kiểm tra.
❑ Các ngoại lệ được kiểm tra bao gồm tất cả các kiểu con của Ngoại lệ, ngoại trừ các lớp
mở rộng RuntimeException.
❑ Các trường hợp ngoại lệ được kiểm tra phải tuân theo quy tắc xử lý hoặc khai báo; bất kỳ phương pháp nào
có thể đưa ra một ngoại lệ được kiểm tra (bao gồm các phương thức gọi các phương thức có thể ném ra một ngoại lệ được kiểm tra) phải khai báo ngoại lệ đó
sử dụng các cú ném hoặc xử lý ngoại lệ bằng một lần thử/bắt thích hợp.
❑ Các kiểu con của Error hoặc RuntimeException không được chọn, do đó trình biên dịch
không thực thi quy tắc xử lý hoặc khai báo. Bạn được tự do xử lý chúng, hoặc
khai báo chúng, nhưng trình biên dịch không quan tâm đến cách này hay cách khác.
❑ Nếu bạn sử dụng khối tùy chọn cuối cùng, nó sẽ luôn được gọi, bất kể
liệu một ngoại lệ trong lần thử tương ứng có được ném hay không và bất kể ngoại lệ được ném có bị bắt hay không.
❑ Ngoại lệ duy nhất đối với quy tắc cuối cùng sẽ luôn được gọi là quy tắc cuối cùng sẽ không được gọi nếu JVM tắt. Điều đó có thể xảy ra nếu mã
từ các lệnh gọi khối thử hoặc bắt System.exit().
❑ Chỉ vì lệnh gọi cuối cùng không có nghĩa là nó sẽ hoàn thành. Mã trong
khối cuối cùng có thể tự đưa ra một ngoại lệ hoặc đưa ra System.exit().
❑ Các ngoại lệ chưa được nắm bắt sẽ truyền trở lại ngăn xếp cuộc gọi, bắt đầu từ
phương thức mà ngoại lệ được ném ra và kết thúc bằng ngoại lệ đầu tiên
phương thức có khả năng nắm bắt tương ứng cho loại ngoại lệ đó hoặc JVM
tắt máy (điều này xảy ra nếu ngoại lệ xảy ra với main() và main() là
"làm giảm" ngoại lệ bằng cách khai báo nó).
❑ Bạn có thể tạo ngoại lệ của riêng mình, thông thường bằng cách mở rộng Ngoại lệ hoặc
một trong những kiểu con của nó. Khi đó, ngoại lệ của bạn sẽ được coi là ngoại lệ được kiểm tra và trình biên dịch sẽ thực thi quy tắc xử lý hoặc khai báo cho ngoại lệ đó.
❑ Tất cả các khối bắt phải được sắp xếp từ cụ thể nhất đến chung nhất.
Nếu bạn có mệnh đề bắt cho cả IOException và Exception, bạn phải
đặt phần bắt cho IOException đầu tiên trong mã của bạn. Nếu không, IOException sẽ bị bắt bởi Catch(Exception e), bởi vì đối số Catch
có thể bắt ngoại lệ được chỉ định hoặc bất kỳ kiểu con nào của nó! Trình biên dịch sẽ
ngăn bạn xác định các mệnh đề bắt không bao giờ có thể đạt được.
❑ Một số ngoại lệ được tạo bởi các lập trình viên, một số do JVM tạo ra.
​





