# [JAVA] - BUỔI 3: CÁCH JAVA LƯU TRỮ DỮ LIỆU
## Cách Java lưu trữ dữ liệu
Khi một chương trình Java được thực thi, nó sẽ yêu cầu hệ điều hành cấp phát một không gian trên bộ nhớ để lưu trữ toàn bộ dữ liệu và thông tin của nó.
Sau đó, nó sẽ chia vùng không gian đó thành 4 vùng nhớ (memory segment) để lưu trữ.

![](https://toithacmac.files.wordpress.com/2015/04/13.png?w=620)

* **Vùng nhớ code (code segment)**: theo như tên gọi của nó, tất cả mã chương trình (machine code) được lưu ở đây khi chương trình được thực thi.
* **Vùng nhớ data (data segment)**: đây là nơi lưu trữ những dữ liệu chung của chương trình như các biến static, constant,… những biến dữ liệu mà được sinh ra khi chương trình bắt đầu thực thi và chỉ được giải phóng khi chương trình kết thúc.
* **Vùng nhớ stack (stack segment)**: đây sẽ là nơi lưu trữ các biến thuộc nhóm kiểu dữ liệu cơ sở (primitive data type như là boolean, int, char,…) và địa chỉ của ô nhớ (memory address).

Tại sao gọi là vùng nhớ stack? Bởi vì dữ liệu ở đây chia theo các nhóm gọi là stack frame, và mỗi stack frame sẽ được lưu vào vùng nhớ stack theo cơ chế Last-in-first-out (LIFO) như một stack.

Vậy, stack frame (SF) là gì? Nó là nơi lưu trữ toàn bộ các biến của một phương thức (method), mỗi phương thức được thực thi sẽ tạo ra một SF. 

* **Vùng nhớ heap (heap segment)**: đây là nơi lưu trữ tất cả các đối tượng (object) được sinh ra trong thời gian thực thi chương trình (run time).

Với vùng nhớ Code và Data, khi chương trình thực thi sẽ cấp phát một không gian có kích thước không đổi.

Còn đối với vùng nhớ Stack và Heap, kích thước của nó sẽ thay đổi (hoặc mở rộng khi tạo thêm biến hoặc đối tượng, hoặc thu hẹp khi một biến hoặc đối tượng được giải phóng) và nếu cần mở rộng thêm, nó sẽ lấy không gian từ Free memory.

Ngoài ra, trong bộ nhớ máy tính, mỗi ô nhớ sẽ được đánh địa chỉ để xác định chính xác vị trí của nó trong bộ nhớ. Vì vậy trong mỗi ô nhớ sẽ bao gồm 2 thành phần là **Value** và **Address** như hình vẽ.

### Kiểu dữ liệu nguyên thủy


* Tất cả các biến thuộc kiểu dữ liệu tham chiếu đều được lưu trên vùng nhớ stack.
* Ex: int a = 10;
* Giải thích: int a là cấp phát một ô nhớ 4 byte (kiểu int có độ dài 4 byte) trên vùng nhớ stack. Ô nhớ gồm có Value và địa chỉ.
* A = 10 gán value cho ô nhớ là 10.




