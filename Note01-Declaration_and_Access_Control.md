# NOTE 01: Declaration and Access Control
Trong phần Declaration and Access Control, chúng ta sẽ tìm hiểu về cách đặt tên trong Java và các từ khóa để kiểm soát quyền truy cập như public, protected, private,..

## 1. Identifier
Java có một số quy tắc bắt buộc trong việc đặt tên. Các quy tắc này áp dụng cho mọi thứ bất kể cả tên biến, tên hàm, tên lớp....
- Tên phải được bắt đầu bằng một ký tự hoặc `$` hoặc `_`, và không được bắt đầu bằng số.
- Tên không được trùng với tên của các keyword, ví dụ: `int`, `const`, `class`,...
- Java phân biệt chữ hoa và chữ thường, ABC sẽ khác aBC.
 ```java
 // Các tên hợp lệ
 int _a, $c, ______2_w, _$, this_is_a_very_detailed_name_for_an_identifier;
 
 // Các tên không hợp lệ
 int :b, -d, e#, .f, 7g;
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

## 2. Declaration Rules
Một file chỉ có thể có duy nhất một public class.

Một file mã nguồn chỉ có thể có một lớp public.

Nếu tệp nguồn chứa lớp công khai, tên tệp phải khớp với tên lớp công khai.

Một tập tin chỉ có thể có một câu lệnh gói nhưng được nhập nhiều lần.
Câu lệnh gói (nếu có) phải là dòng đầu tiên (không có chú thích) trong một tập tin nguồn.
Các tờ khai nhập khẩu (nếu có) phải ở sau gói hàng và trước khai báo lớp.

Nếu không có câu lệnh gói, câu lệnh nhập phải là câu lệnh đầu tiên (không ghi chú) trong tệp nguồn.

câu lệnh đóng gói và nhập áp dụng cho tất cả các lớp trong tệp.

Một tập tin có thể có nhiều lớp không công khai.

Các tập tin không có lớp công khai sẽ không có hạn chế về đặt tên.

### 3. Class Access Modifiers
Java có 4 cấp độ truy cập là `public`, `protected`, `default`, `private` nhưng chỉ cung cấp 3 access modifier là `public`, `protected`, `private`.

Các lớp chỉ có thể được gán là `public` hoặc `default`. Các class được gán là `public` sẽ được thấy bởi mọi class ở mọi package. Các class với cấp độ truy cập mặc định thì chỉ được thấy bởi những class trong cùng một package.

Khả năng nhìn thấy của một lớp đề cập đến việc: tạo một instance, kế thừa từ nó, truy cập vào các biến và hàm của lớp đó.

Một class cũng có thể được khai báo: final, abstract, or strictfp.

Một final class không thể được kế thừa, một abstract class không thể được khởi tạo. Một abstract class có thể không có abstract method nào, như nếu một class có một abstract method thì class đó phải là abstract class.

Class kế thừa từ abstract class phải ghi đè toàn bộ abstract method, một abstract method không được là private

Một class không thể vừa là `final` vừa là `abstract`

### Access Modifier
Java có 4 mức độ truy cập, nhưng chỉ cung cấp 3 quyền truy cập, quyền truy cập thứ 4 là quyền truy cập mặc định hoặc quyền truy cập gói.

Sun khuyến khích bạn đặt tên gói ngược lại với tên miền, ví dụ abc.com -> com.abc..

khi một class được khai báo là `final` thì các class khác sẽ không thể kế thừa từ nó, vì tính không kế  thừa nên nó không được đánh giá cao bởi nó vi phạm đặc tính của OOP.


Một abstract class được sinh ra chỉ để cho class khác kế thừa nó(ngược lại với final class), một abstract class không thể được khởi tạo. liên quan đến tính trừu tượng trong java, tính trừu tượng làm đơn giản hóa các đối tượng, dấu những hoạt động không cần thiết và chỉ hiển thị những thứ cần thiết. 

một method là abstract thì class đó phải là abstract

### 4. Interface
### Interface
- Interface định nghĩa những gì mà một class có thể làm
- Interface chỉ có thể được khai báo là `public` hoặc `default`.
- Một Interface hoàn toàn giống với một abstract class và nó được ngầm định là `abstract` dù bạn có khai báo hay không.
❑ An interface can have only abstract methods, no concrete methods allowed.
❑ Interface methods are by default public and abstract—explicit declaration
of these modifiers is optional.

- Các constant có thể được khai báo trong Interface, và chúng luôn được đánh dấu là `public static final` bất kể ta có khai báo rõ ràng hay không.
- Khi một nonabstract class implement một interface thì:
❑ A legal nonabstract implementing class has the following properties:
 ❑ It provides concrete implementations for the interface's methods.
 ❑ It must follow all legal override rules for the methods it implements.
 ❑ It must not declare any new checked exceptions for an
 implementation method.

 ❑ It must not declare any checked exceptions that are broader than
 the exceptions declared in the interface method.
 ❑ It may declare runtime exceptions on any interface method
 implementation regardless of the interface declaration.
 ❑ It must maintain the exact signature (allowing for covariant returns)
 and return type of the methods it implements (but does not have to
 declare the exceptions of the interface).
❑ A class implementing an interface can itself be abstract.
❑ An abstract implementing class does not have to implement the interface methods (but the first concrete subclass must).
- Một class chỉ có thể kế thừa 1 class nhưng lại có thể implement nhiều interface.
- Một Interface không thể kế thừa một class, cũng như không thể implement class hoặc interface khác mà nó có thể kế thừa 1 hoặc nhiều interface.
- Khi làm bài kiểm tra, hãy xác minh rằng các khai báo interface và class là hợp lệ trước khi xác minh logic mã khác.

với các biến referrence; bạn chỉ có thể gán các access modifier và final cho nó + transitient, các keyword còn lại là không được phép.
một hàm static không thể truy cập vào các static class member
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

## 5. Member Access Modifiers
❑ Methods and instance (nonlocal) variables are known as "members."
❑ Members can use all four access levels: public, protected, default, private.
❑ Member access comes in two forms:
 ❑ Code in one class can access a member of another class.
 ❑ A subclass can inherit a member of its superclass.
❑ If a class cannot be accessed, its members cannot be accessed.
❑ Determine class visibility before determining member visibility.
❑ public members can be accessed by all other classes, even in other packages.
❑ If a superclass member is public, the subclass inherits it—regardless of package.
❑ Members accessed without the dot operator (.) must belong to the same class.
❑ this. always refers to the currently executing object.
❑ this.aMethod() is the same as just invoking aMethod().
❑ private members can be accessed only by code in the same class.
❑ private members are not visible to subclasses, so private members cannot be inherited.
❑ Default and protected members differ only when subclasses are involved:
 ❑ Default members can be accessed only by classes in the same package.
 ❑ protected members can be accessed by other classes in the same
 package, plus subclasses regardless of package.
 ❑ protected = package plus kids (kids meaning subclasses).
 ❑ For subclasses outside the package, the protected member can be
 accessed only through inheritance; a subclass outside the package cannot
 access a protected member by using a reference to a superclass instance
 (in other words, inheritance is the only mechanism for a subclass
 outside the package to access a protected member of its superclass).
 ❑ A protected member inherited by a subclass from another package is
 not accessible to any other class in the subclass package, except for the
 subclass' own subclasses.

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


### Khai báo biến
- Một biến có thể được khai báo với: `public`, `protected`, `private`, `static`, `transient`, `volatile`.
- Một biến instance không thể được khai báo với: `abstract`, `synchronized`, `native`, or `strictfp`.
- Một local variable có thể trùng tên với instance variable, kỹ thuật này gọi là "shadowing".
- Một `final` variable không thể được gán giá trị 2 lần.
- Một `final` variable phải được gán ngay lúc khởi tạo hoặc trong constructor.

❑ Instance variables can
❑ Have any access control
❑ Be marked final or transient
❑ Instance variables can't be abstract, synchronized, native, or strictfp.
❑ It is legal to declare a local variable with the same name as an instance
variable; this is called "shadowing."
❑ final variables have the following properties:
 ❑ final variables cannot be reinitialized once assigned a value.
 ❑ final reference variables cannot refer to a different object once the
 object has been assigned to the final variable.
 ❑ final reference variables must be initialized before the constructor
 completes.
❑ There is no such thing as a final object. An object reference marked final
does not mean the object itself is immutable.
❑ The transient modifier applies only to instance variables.
❑ The volatile modifier applies only to instance variables.
Array Declarations (Objective 1.3)
❑ Arrays can hold primitives or objects, but the array itself is always an object.
❑ When you declare an array, the brackets can be to the left or right of the
variable name.
❑ It is never legal to include the size of an array in the declaration.
❑ An array of objects can hold any object that passes the IS-A (or instanceof)
test for the declared type of the array. For example, if Horse extends Animal,
then a Horse object can go into an Animal array.
### Khai báo mảng
- Mảng có thể chứa các object hoặc kiểu dữ liệu nguyên thủy, nhưng bản thân mảng luôn là một object.
- Khi bạn khai báo một mảng, dấu `[]` có thể ở bên trái hoặc bên phải của mảng tên biến.
  ```java
  Dog [] dogs;
  Cat cats[];
  int x [];
  ```
- Việc đưa kích thước của mảng vào khai báo không bao giờ là hợp pháp.
- Một mảng các đối tượng có thể chứa bất kỳ đối tượng có quan hệ **IS-A** (hoặc instanceof) kiểm tra kiểu khai báo của mảng. 
  ```java
  Animal [] animal;
  animal[0] = new Dog(); // Hợp lệ nếu Dog kế thừa Animal
  ```
### Biến và Hàm Static
- Các biến và hàm static không thuộc về bất cứ một instance nào của đối tượng.
- Chúng ta có thể sử dụng các biến và hàm static mà không cần phải khởi tạo đối tượng.
- Một hàm static không thể gọi một hàm non-static, nhưng có thể gọi ngược lại.
  ```java
  static void staticMethod() {
        nonStaticMethod();
    } // không hợp lệ, static method không thể gọi một non-static method

    void nonStaticMethod() {
        staticMethod();
    }// hợp lệ, một non-static method có thể gọi một static method
  ```

### Enums
Một enum chỉ định một danh sách các giá trị không đổi. Enum KHÔNG phải là String hay int; kiểu của hằng số enum là enum kiểu. Ví dụ: MÙA HÈ và MÙA THU thuộc loại enum Season.

Một enum có thể được khai báo bên ngoài hoặc bên trong một lớp, nhưng KHÔNG được khai báo trong một phương thức. Khi một enum được khai báo bên ngoài một lớp KHÔNG được đánh dấu là static, final, abstract, protected, private.

Enums có thể chứa các hàm tạo, phương thức, biến và thân lớp không đổi.

Hằng số enum có thể gửi đối số tới hàm tạo enum bằng cách sử dụng cú pháp BIG(8), trong đó chữ int 8 được truyền cho hàm tạo enum.

hàm tạo enum có thể có đối số và có thể bị quá tải.

hàm tạo enum KHÔNG BAO GIỜ có thể được gọi trực tiếp trong mã. Họ luôn luôn được gọi tự động khi một enum được khởi tạo.

Dấu chấm phẩy ở cuối câu khai báo enum là tùy chọn. Đây là những điều hợp pháp:
```java
enum Foo { MỘT, HAI, BA}
enum Foo { MỘT, HAI, BA};
```
- MyEnum.values() trả về một mảng các giá trị của MyEnum.

//////////////



## Local Variables
❑ Local (method, automatic, or stack) variable declarations cannot have
access modifiers.
❑ final is the only modifier available to local variables.
❑ Local variables don't get default values, so they must be initialized before use.
Other Modifiers—Members (Objective 1.3)
❑ final methods cannot be overridden in a subclass.
❑ abstract methods are declared, with a signature, a return type, and
an optional throws clause, but are not implemented.
❑ abstract methods end in a semicolon—no curly braces.
❑ Three ways to spot a non-abstract method:
 ❑ The method is not marked abstract.
 ❑ The method has curly braces.
 ❑ The method has code between the curly braces.
❑ The first nonabstract (concrete) class to extend an abstract class must
implement all of the abstract class' abstract methods.
❑ The synchronized modifier applies only to methods and code blocks.
❑ synchronized methods can have any access control and can also be marked final.
❑ abstract methods must be implemented by a subclass, so they must be
inheritable. For that reason:
 ❑ abstract methods cannot be private.
 ❑ abstract methods cannot be final.
❑ The native modifier applies only to methods.
❑ The strictfp modifier applies only to classes and methods.
Methods with var-args (Objective 1.4)
❑ As of Java 5, methods can declare a parameter that accepts from zero to
many arguments, a so-called var-arg method.
❑ A var-arg parameter is declared with the syntax type... name; for instance:
doStuff(int... x) { }
❑ A var-arg method can have only one var-arg parameter.
❑ In methods with normal parameters and a var-arg, the var-arg must come last.


## Một Số Quy Tắc Trong Khai Báo Các Class Member
