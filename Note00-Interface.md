# Interface

Mọi method được khai báo bên trong thân của một interface đều được ngầm định là *public.* Các cố gắng chỉ định *protect* hay *private* đều không cho phép và sẽ bị trình biên dịch báo lỗi.

Một *default method* là một method mà nó được khai báo bên trong một interface và được chỉ định là *default.* Phần thân của một *default method* luôn là một khối.

*Default method* giúp ta thêm các chức năng mới vào một interface mà không cần phải override lại các lớp implement nó.  Tuy nhiên, một vấn đề lưu ý là nếu một lớp triển khai 2 interface có cùng defalut method thì? 

Khi một class triển khai 2 interface chứa default method cùng tên sẽ xảy ra xung đột (conflict). Bởi vì lúc này Java sẽ không biết phải sử dụng phương thức mặc định nào cho phù hợp. Khi đó, trình biên dịch của Java sẽ thông một lỗi tương tự như sau: lúc này ta có thể giải quyết bằng cách Override lại phương thức doSomething từ lớp con.
Gọi default method của một interface cụ thể bằng cách sử dụng từ khóa super.

Bên trong interface cũng có thể khai báo static method, Phương thức static cũng giống như phương thức default, ngoại trừ việc nó không thể được override chúng trong class được implements.

Chúng ta có thể gọi static method từ class implement interface đó

## 8. Functional Interface
Một *Functional interface* là một interface mà chỉ có duy nhất một abstract method.
