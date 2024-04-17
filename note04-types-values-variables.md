# NOTE 04: TYPES, VALUES, AND VARIABLES
Java là một ngôn ngữ có kiểu tĩnh (statically typed), có nghĩa là mọi dữ liệu phải được xác định kiểu dữ liệu tại thời điểm biên dịch.

## 3. Variables
Biến là vùng nhớ có tên để lưu trữ dữ liệu trong chương trình. Chúng ta truy xuất giá trị của biến qua tên của chúng.

Phạm vi của biến quyết định vị trí lưu trữ của nó trong bộ nhớ. Biến cục bộ được lưu trữ trên stack. Biến thể hiện được lưu trữ trên heap. Biến static được lưu trữ trong vùng nhớ tĩnh(static memory).

Các biến class, biến instance và array đều có giá trị mặc định: byte(0), short(0), int(0), long(0L), float(0.0f), double(0.0d), char('\u0000'), boolean(false), các biến tham chiếu(null).

Các biến local không có giá trị mặc định và chúng cần phải được gán giá trị trước khi sử dụng.
