# NOTE01: Declaration and Access Control
Trong phần Declaration and Access Control, chúng ta sẽ tìm hiểu về cách đặt tên trong Java và các từ khóa để kiểm soát quyền truy cập như public, protected, private,..

## 1. Identifier
Java có một số quy tắc (bắt buộc) trong việc đặt tên (áp dụng cho mọi thứ bất kể cả tên biến, tên hàm, tên lớp...).
- Tên phải được bắt đầu bằng một ký tự hoặc `$` hoặc `_`, và không được bắt đầu bằng số.
- Tên không được trùng với tên của các keyword, ví dụ: `int`, `const`, `class`,...
- Java phân biệt chữ hoa và chữ thường, ABC sẽ khác aBC.
```java
// Các tên hợp lệ
int _a;
int $c;
int ______2_w;
int _$;
int this_is_a_very_detailed_name_for_an_identifier;

// Các tên không hợp lệ
int :b;
int -d;
int e#;
int .f;
int 7g;
```
Một số quy ước(không bắt buộc) về đặt tên mà Sun đưa ra và được mọi lập trình viên tuân theo:
- Tên lớp (Classes) nên là danh từ và chữ cái đầu viết hoa, ví dụ: Dog, Account, PrintWriter.
- Tên giao diện (Interfaces) nên là tính từ và chữ cái đầu viết hoa, ví dụ: Runnable, Serializable.
- Tên phương thức (Methods) nên là động từ, chữ cái đầu viết thường và từ thứ hai viết hoa, ví dụ: getBalance, doCalculation, setCustomerName().
- Tên biến (Variables) nên tuân theo quy tắc giống như tên phương thức, thường là các tính từ, ví dụ: numberOfStudents, maximumValue, customerName.
- Tên hằng số (Constants) nên viết hoa và các từ cách nhau bằng dấu gạch dưới (underscore), ví dụ: MAXIMUM_VALUE, PI, DEFAULT_TIMEOUT.

JavaBeans cũng cung cấp 1 chuẩn về đặt tên mà chúng ta sẽ gặp rất nhiều.
- đối với biến boolean thì các hàm getter setter sẽ bắt đầu bằng is.

Một file có thể có nhiều class nhưng chỉ có 1 class được khai báo là public, tên file phải trùng với tên public class đó.

Nếu một file mà không có một public class thì tên file không cần thiết phải trùng với tên của class.

lệnh package phải dc khai báo trước import > class

### Access Modifier
Java có 4 mức độ truy cập, nhưng chỉ cung cấp 3 quyền truy cập, quyền truy cập thứ 4 là quyền truy cập mặc định hoặc quyền truy cập gói.
Sun khuyến khích bạn đặt tên gói ngược lại với tên miền, ví dụ abc.com -> com.abc..


khi một class không khai báo access modifier thì class đó có quyền truy cập là default, và những class trong cùng package mới có thể thấy được, những class khác package sẽ không thể thấy được class đó

một class cũng có thể được khai báo: final, abstract, or strictfp, 

khi một class được khai báo là `final` thì các class khác sẽ không thể kế thừa từ nó, vì tính không kế  thừa nên nó khôngđược đánh giá cao bởi nó vi phạm đặc tính của OOP.


Một abstract class được sinh ra chỉ để cho class khác kế thừa nó(ngược lại với final class), một abstract class không thể được khởi tạo. liên quan đến tính trừu tượng trong java, tính trừu tượng làm đơn giản hóa các đối tượng, dấu những hoạt động không cần thiết và chỉ hiển thị những thứ cần thiết. 

một method là abstract thì class đó phải là abstract

### interface
mọi biến trong interace đều là public static final, ngay cả khi bạn không khai báo access modifier cho nó.
```java
public interface Bounceable {
 void bounce(); // No modifiers
 void setBounceFactor(int bf); // No modifiers
}

//khong hop le
final void bounce(); // final and abstract can never be used
 // together, and abstract is implied
static void bounce(); // interfaces define instance methods
private void bounce(); // interface methods are always public
protected void bounce(); // (same as above)
```

method trong inteface không được là static

bởi vì method trong interface được mặc định là absstract nên final, strif, native không được phép sử dụng.

interface có thể kế thừa từ 1 interafce hoặc nhiều khác.

### Class Member
trong khi một class chỉ có thể sử dụng 2 trong 4 cấp độ truy cập (public hoặc default) thì các biến và hàm trong class có thể khai báo 4 cấp độ(public-protected-default-private).

có 2 keeir truy cập vào phương thức
1. liêu a có gọi được hàm trong class b hay không
2. liệu a có hàm của class cha B hay không

một class member được khai bao là public thì mọi class hay interface đều có thể truy cập vào nó.

các class member được đánh dấu là private thì nó sẽ không thể truy cập được từ bất kì class nào khác, bất kể chúng có quan hệ cha-con, cùng gói hay khác gói.

trong thực tế, các biến thường được khuyến khích là sử dụng private, việc truy xuất chúng sẽ thông qua các hàm getter và setter. Nó đảm bảo được tính đóng gói của thiết kế chương trình. Và cũng cần biết là một hàm private không thẻ bị ghi đè.

các class member được đánh dấu là protected sẽ được truy cập thông qua kế thừa, cho phép khác package, đồng thời cũng từ các class cùng package, một lưu ý to đùng ở đây là được phép truy cập thông qua kế thừa, còn việc bạn tạo mới 1 instance và gọi nó thì điều đó là không cho phép. bởi lúc này việc này khong còn là kế thừa fnuawx
đối với các class bên ngoài package, cách duy nhát để truy cập vào các protected class member là thông qua kế thừa


khi một subclass khác package kế thừa protected class member từ parentclass, thì các class cùng package với class con đó cũng sẽ không thể thấy được protected class member
các class member được đánh dấu là defaul(level package) chỉ được truy cập trong 1 package, còn protected được truy cập ngoài một package, thông qua kế thừa.


Khi một class member của superclass được đánh dấu là default thì:
- các subclass mà khác package sẽ không thể truy cập vào.

Các local variable có được phép gán access modifier không? Câu trả lời là KHÔNG! và chỉ có `final` mới dc gán cho local variable.

Đươi đây là một tổng hợp lại :
- Các member class trong cùng 1 class: public(có thể thấy) - protected (có thể thấy)
- Khác class nhưng cùng gói: private (không được thấy)
- subclass trong cùng 1 gói: private (không được thấy)
- subclass nhưng khác package: protected(nhìn thấy thông qua kế thừa)
- non-subclass khác gói: chỉ có public có thể thấy.

NonAccess member modifier
Final method: một method là final thì nó sẽ không được ghi đè khi kế thừa. các đối số trong method cũng có thể được dánh dấu là final, và giá trị của nó sẽ không thể thay đổi, nó hoạt động giống như local variable.

abstract method: các method được đánh dấu là static thì không có phần thân hàm. Một abstract class thì có thể không chứa bất kì abstract method nào cả.

bất kì class nào khi kế thừa từ một abstract class cũng sẽ phải override lại hết các abstract method, trừ khi class đó cũng là abstract


một method không thể vừa abtract vừa final hay vừa abtract vừa private được. static method cũng không thể là static được.

một hàm đánh dấu là synchronized thì nó chỉ được 1 luồng sử dụng trong 1 thời điểm, và nó chỉ app dụng với method, các biến không được phép gán 


danh sách đối sô trong method: 

argument: là khi bạn truyền giá trị
paramater: là khi bạn khai báo hàm


hàm tạo là hàm để tạo instance từ class, hàm tạo không khai báo kiểu trả về, có tên trùng với tên class, constructor có thể khai báo các access modifier nhung không được phép khai báo là tĩnh-final hoặc abstract

khai báo biến:
6 kiểu dữ liệu số đều là 8bit va bit đầu tiên sẽ quyết định nó là số âm hay dương

![image](https://github.com/1truong9song9hiep8/java-notes/assets/101247928/b5848035-6c59-49f1-9b0f-00dad2832140)

với các biến referrence; bạn chỉ có thể gán các access modifier và final cho nó + transitient, các keyword còn lại là không được phép.
một hàm static không thể truy cập vào các static class member



