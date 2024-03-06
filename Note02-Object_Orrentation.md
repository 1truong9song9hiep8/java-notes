## Tính đóng gói (Encapsulation)
Tính đóng gói trong Java thể hiện ở việc thiết lập các access modifier nhằm dấu những thứ không cần thiết, từ đó giúp người lập trình viên dấu những thông tin quan trọng và riêng tư trong ứng dụng.

private/public/protected method trong java cũng được xem là một thể hiện của tính đóng gói trong java, package cũng được xem là tính đóng gói trong java

Lợi ích từ getter và setter? nó là việc bạn có thể tùy chỉnh sử lý khi get và set giá trị cho biến.
## Iheritence, Is-A, Has-A
Mọi class mà chúng ta tạo ra đều kế thừa từ 1 class tên là `Object`, và có thể sử dụng một số method từ class này như: `equal()`, `hashCode()`, `toString()`...
Tính kế thừa trong Java được thể hiện bằng việc 1 class có thể extend 1 class và có thể implement nhiều interface.
Mối quan hệ Is-A và Has-A
Mối quan hệ Is-A chính là mối quan hệ kế thừa, khi một class A extends từ B, ta nói A-B là mối quan hệ Is-a (hay cha-con), hay A là một kiểu của B, mối quan hệ IS-A được thể hiện thông qua keyword extends và implements

Has-A
Nếu một class A có một properties là instance của class B, khi đó mối quan hệ A-B chính là quan hệ Has-a, từ đây các method trong B có thể được gọi từ A thông qua instance của B.

IS-a/ has-a hay escapsulation chỉ là phần cực kì nhỏ và cơ bản trong thiết kế,trong thực tế, mọi thứ phức tạp và to lớn hơn rất nhiều, và để hỗ trợ việc đó thì các mẫu thiết kế được ra đời nhằm hỗ trợ việc thiết kế ứng dụng java một cách hiệu quả..

## Tính trừu tượng (Polymorphism)
Tính đa hình được thể hiện qua kế thừa và override lại các phương thức của lớp cha.

Biến tham chiếu là những biến có kiểu là parent hoặc interface

Static variable vs method
Biến và hàm static được tạo khi class chứa nó được load vào JVM trước bất cứ instance nào được tạo, Biến và hàm static được dùng để lưu trữ dữ liệu mà có thể chia sẽ giữa các instance, nó không phụ thuộc vào instance của class
một static method không thể truy cập vào một biến nonstatic

## Static
### Biến và hàm static
Một số đặc điểm của hàm static:
- Biến static được các instance chia sẻ.
- Có thể gọi trực tiếp mà không cần khởi tạo instance của class.
- Hàm static chỉ có thể truy cập vào các static member, và không có quyền truy cập vào các non-static member.
- Hàm static không thể được ghi đè

## coupling vs cohesion
coupling(sự khớp nối) và cohesion(tính liên kết) để chỉ mức độ liên kết, mức độ phụ thuộc lẫn nhau giữa các đối tượng trong OOP. Một ứng dụng được thiết kế OOP tốt là một ứng dụng mà sự khớp nối được tránh đồng thời tính liên kết dược tăng cường.

### Tính khớp nối 
Một class A chỉ biết những thứ mầ class B thể hiện qua interface thì đó la một kết nối lỏng lẻo (một thiết kế tốt), ví dụ:
```java
  class DoTaxes {
        float rate;

        float doColorado() {
            SalesTaxRates str = new SalesTaxRates();
            rate = str.salesRate; // ouch
            // this should be a method call:
            // rate = str.getSalesRate("CO");
            // do stuff with rate
        }
    }
```

## 1. Encapsulation, IS-A, HAS-A
- Encapsulation helps hide implementation behind an interface (or API).
- Encapsulated code has two features:
- Instance variables are kept protected (usually with the private modifier).
- Getter and setter methods provide access to instance variables.
- IS-A refers to inheritance or implementation.
- IS-A is expressed with the keyword extends.
- IS-A, "inherits from," and "is a subtype of " are all equivalent expressions.
- HAS-A means an instance of one class "has a" reference to an instance of
another class or another instance of the same class.
## 2. Inheritance
- Inheritance allows a class to be a subclass of a superclass, and thereby
inherit public and protected variables and methods of the superclass.
- Inheritance is a key concept that underlies IS-A, polymorphism, overriding,
overloading, and casting.
- All classes (except class Object), are subclasses of type Object, and therefore
they inherit Object's methods.
## 3. Polymorphism
- Polymorphism means "many forms."
- A reference variable is always of a single, unchangeable type, but it can refer
to a subtype object.
- A single object can be referred to by reference variables of many different
types —as long as they are the same type or a supertype of the object.
- The reference variable's type (not the object's type), determines which
methods can be called!
- Polymorphic method invocations apply only to overridden instance methods.

## 4. Overriding and Overloading
- Methods can be overridden or overloaded; constructors can be overloaded
but not overridden.
- Abstract methods must be overridden by the first concrete (non-abstract)
subclass.
- With respect to the method it overrides, the overriding method
 - Must have the same argument list.
 - Must have the same return type, except that as of Java 5, the return type
 can be a subclass—this is known as a covariant return.
 - Must not have a more restrictive access modifier.
 - May have a less restrictive access modifier.
 - Must not throw new or broader checked exceptions.
 - May throw fewer or narrower checked exceptions, or any
 unchecked exception.
- final methods cannot be overridden.
- Only inherited methods may be overridden, and remember that private
methods are not inherited.
- A subclass uses super.overriddenMethodName() to call the superclass
version of an overridden method.
- Overloading means reusing a method name, but with different arguments.
- Overloaded methods
 - Must have different argument lists
 - May have different return types, if argument lists are also different
 - May have different access modifiers
 - May throw different exceptions
- Methods from a superclass can be overloaded in a subclass.
- Polymorphism applies to overriding, not to overloading.
- Object type (not the reference variable's type), determines which overridden
method is used at runtime.
- Reference type determines which overloaded method will be used at
compile time.

## 5. Reference Variable Casting (Objective 5.2)
- There are two types of reference variable casting: downcasting and upcasting.
- Downcasting: If you have a reference variable that refers to a subtype object,
you can assign it to a reference variable of the subtype. You must make an
explicit cast to do this, and the result is that you can access the subtype's
members with this new reference variable.
- Upcasting: You can assign a reference variable to a supertype reference variable explicitly or implicitly. This is an inherently safe operation because the
assignment restricts the access capabilities of the new variable.
## 6. Implementing an Interface
- When you implement an interface, you are fulfilling its contract.
- You implement an interface by properly and concretely overriding all of the
methods defined by the interface.
- A single class can implement many interfaces.
## 7. Return Types
- Overloaded methods can change return types; overridden methods cannot,
except in the case of covariant returns.
- Object reference return types can accept null as a return value.
- An array is a legal return type, both to declare and return as a value.
- For methods with primitive return types, any value that can be implicitly
converted to the return type can be returned.
- Nothing can be returned from a void, but you can return nothing. You're
allowed to simply say return, in any method with a void return type, to bust
out of a method early. But you can't return nothing from a method with a
non-void return type.
- Methods with an object reference return type, can return a subtype.
- Methods with an interface return type, can return any implementer.
## 8. Constructors and Instantiation
- A constructor is always invoked when a new object is created.
- Each superclass in an object's inheritance tree will have a constructor called.
- Every class, even an abstract class, has at least one constructor.
- Constructors must have the same name as the class.
- Constructors don't have a return type. If you see code with a return type, it's a
method with the same name as the class, it's not a constructor.
- Typical constructor execution occurs as follows:
 - The constructor calls its superclass constructor, which calls its superclass
 constructor, and so on all the way up to the Object constructor.
 - The Object constructor executes and then returns to the calling
 constructor, which runs to completion and then returns to its calling
 constructor, and so on back down to the completion of the constructor of
 the actual instance being created.
- Constructors can use any access modifier (even private!).
- The compiler will create a default constructor if you don't create any constructors in your class.
- The default constructor is a no-arg constructor with a no-arg call to super().
- The first statement of every constructor must be a call to either this() (an
overloaded constructor) or super().
- The compiler will add a call to super() unless you have already put in a call
to this() or super().
- Instance members are accessible only after the super constructor runs.
- Abstract classes have constructors that are called when a concrete
subclass is instantiated.
- Interfaces do not have constructors.
- If your superclass does not have a no-arg constructor, you must create a constructor and insert a call to super() with arguments matching those
of the superclass constructor.
- Constructors are never inherited, thus they cannot be overridden.
- A constructor can be directly invoked only by another constructor (using
a call to super() or this()).
- Issues with calls to this()
 - May appear only as the first statement in a constructor.
 - The argument list determines which overloaded constructor is called.
 - Constructors can call constructors can call constructors, and so on, but
 sooner or later one of them better call super() or the stack will explode.
 - Calls to this() and super() cannot be in the same constructor. You can
 have one or the other, but never both.
## 9. Statics
- Sử dụng static method để hiện thực các hành động mà không ảnh hưởng bởi bất kỳ instance nào.
- Sử dụng static variable để dành riêng cho class thay vì instance.
- All static members belong to the class, not to any instance.
- A static method can't access an instance variable directly.
- Use the dot operator to access static members, but remember that using a
reference variable with the dot operator is really a syntax trick, and the compiler will substitute the class name for the reference variable, for instance:
 d.doStuff();
 becomes:
 Dog.doStuff();
- static methods can't be overridden, but they can be redefined.

## 10. Coupling and Cohesion
- Coupling refers to the degree to which one class knows about or uses members of another class.
- Loose coupling is the desirable state of having classes that are well encapsulated, minimize references to each other, and limit the breadth of API usage.
- Tight coupling is the undesirable state of having classes that break the rules of
loose coupling.
- Cohesion refers to the degree in which a class has a single, well-defined role
or responsibility.
- High cohesion is the desirable state of a class whose members support a
single, well-focused role or responsibility.
- Low cohesion is the undesirable state of a class whose members support multiple, unfocused roles or responsibilities.
