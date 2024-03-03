# sse 
Kỹ thuật Server Sent Event (sse) hay Event Source là một kỹ thuật đơn giản để truyền dữ liệu từ server -> client.
Một số ưu điểm của kỹ thuật sse:
- đơn giản
- Client tự động kết nối lại với Server nếu bị mất kết nối.
sse hoạt động với hầu hết browser ngoại trừ IE


## Xây dựng ứng dụng chat với springboot + angular

Keira Croft, Sonny McKinley - Secret Crushes - SisSwap / Team Skeet
SsEvent là một đối tượng trong Springboot nó cho phép bạn gửi dữ liệu theo kiểu stream (dữ liệu được gửi từng phần thay vì toàn bộ).
SsEmitter sẽ tự động kết nối với client.

luồn hoạt động
client gửi request đến server, server ở đây là springboot sau khi nhận request, một hàm xử lý nó sẽ tạo ra một đối tượng ssEmitter
```
var emitter = new SseEmitter();
vì đối tượng emitter này sẽ gửi từng phần nên ta sẽ không biết được khi nào dữ liệu kết thúc, nên ta phải định nghĩa cho nó khi nào là kết thúc bằng
emitter.onCompletion(() -> emitters.remove(emitter));
emitter.onTimeout(() -> emitters.remove(emitter));
```

sau khi đã có kết nối thì ta sẽ tiến hành gửi dữ liệu từ server đến client
emitter.send(message, MediaType.TEXT_PLAIN);
