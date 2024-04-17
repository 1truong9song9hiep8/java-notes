# Threads
Trong lập trình **thread** là một tiến trình xử lý tác vụ, những tác vụ này có thể là xử lý một phép toán hoặc xử lý một hàm...

Java hỗ trợ lập trình đa luồng, cho phép chương trình sử dụng nhiều luồng song song. Điều này giúp tăng tốc độ xử lý và sử dụng bộ nhớ hiệu quả hơn. Tuy nhiên, lập trình đa luồng cũng khiến chương trình phức tạp hơn và đòi hỏi xử lý các vấn đề về tranh chấp bộ nhớ.

Vòng đời của một thread gồm có các trạng thái sau:
- new
- active
- waiting/block
- timed waiting
- terminated

Trong Java, một thread được đại diện bởi một đối tượng của lớp Thread. Vậy nên để sử dụng một thread chúng ta có thể kế thừa class Thread hoặc triển khai interface Runnable



## 1. Defining, Instantiating, and Starting Threads
Các thread có thể được tạo bằng cách kế thừa class Thread và ghi đè lại phương thức `public void run()`.

Thread cũng có thể được tạo bằng cách truyền một Runnable.

Một thread chỉ có thể gọi hàm `start()` một lần duy nhất. Nếu start() được gọi nhiều lần trên một đối tượng Thread, nó sẽ ném ra ngoại lệ RuntimeException.

Chúng ta có thể nhiều đối tượng Thread mà chỉ sử dụng cùng một đối tượng Runnable.

Khi một đối tượng Thread được tạo, nó không trở thành một luồng thực thi cho đến khi phương thức start() của nó được gọi. Khi một đối tượng Thread tồn tại nhưng chưa được khởi động, nó ở trạng thái mới và không được coi là còn tồn tại.

## 2. Transitioning Between Thread States
Khi một thread gọi `start()` nó sẽ ở trạng thái runable.

The thread scheduler có trách nhiệm di chuyển trạng thái của thread từ runnable sang running.

Một thread ở trạng thái running có thể chuyển qua trạng thái block

## Communicating with Objects by Waiting and Notifying
Phương thức `wait()` cho phép một thread nói với JVM là "Hiện tôi đang rảnh, hãy đưa tôi vào danh sách chờ và thực thi thread khác!".

Phương thức notification() được sử dụng để gửi tín hiệu đến một và chỉ một trong số các thread đang chờ trong vùng chờ của cùng đối tượng đó.

Cả ba phương thức—wait(), notification(), và notificationAll()—phải được gọi từ bên trong ngữ cảnh được đồng bộ hóa! Một luồng gọi wait() hoặc notification() trên một đối tượng cụ thể và luồng đó hiện phải giữ khóa trên đối tượng đó.

## Deadlocked Threads
Deadlock là khi 2 hoặc nhiều thread cùng truy cập đến một tài nguyên trong cùng một thời khắc.
Deadlock có thể xảy ra khi một đối tượng bị khóa cố gắng truy cập vào một đối tượng bị khóa khác đang cố truy cập vào đối tượng bị khóa đầu tiên. Nói cách khác, cả hai luồng đang chờ khóa của nhau được giải phóng; do đó, ổ khóa sẽ không bao giờ được mở ra!


Future ComplitableFuture, Callable

# java Doc

