Mục lục
- [\[JAVA\] - BUỔI 3: CÁCH JAVA LƯU TRỮ DỮ LIỆU](#java---buổi-3-cách-java-lưu-trữ-dữ-liệu)
  - [Cách Java lưu trữ dữ liệu](#cách-java-lưu-trữ-dữ-liệu)
    - [Kiểu dữ liệu nguyên thủy](#kiểu-dữ-liệu-nguyên-thủy)
    - [Kiểu dữ liệu tham chiếu](#kiểu-dữ-liệu-tham-chiếu)
    - [Kiểu dữ liệu Object](#kiểu-dữ-liệu-object)
      - [Các phương thức của lớp Object](#các-phương-thức-của-lớp-object)
      - [Khai báo Object](#khai-báo-object)
    - [Lớp Wrapper trong Java](#lớp-wrapper-trong-java)
      - [Quá trình Autoboxing](#quá-trình-autoboxing)
      - [Quá trình Unboxing](#quá-trình-unboxing)
      - [Các Lớp Wrapper cho Kiểu Dữ Liệu Nguyên Thủy](#các-lớp-wrapper-cho-kiểu-dữ-liệu-nguyên-thủy)
      - [Đặc Điểm của Lớp Wrapper trong Java](#đặc-điểm-của-lớp-wrapper-trong-java)
        - [Khởi Tạo](#khởi-tạo)
        - [Hàm toString()](#hàm-tostring)
        - [Hàm typeValue()](#hàm-typevalue)
        - [Hàm equals()](#hàm-equals)
  - [Các phương thức khởi tạo trong java](#các-phương-thức-khởi-tạo-trong-java)
    - [Từ khóa this trong java](#từ-khóa-this-trong-java)
      - [Tham chiếu tới biến của lớp hiện tại.](#tham-chiếu-tới-biến-của-lớp-hiện-tại)
      - [Gọi phương thức của lớp hiện tại.](#gọi-phương-thức-của-lớp-hiện-tại)
      - [Gọi Constructor của lớp hiện tại.](#gọi-constructor-của-lớp-hiện-tại)
      - [Trả về instance của lớp hiện tại](#trả-về-instance-của-lớp-hiện-tại)
      - [Được truyền như một tham số trong phương thức (method).](#được-truyền-như-một-tham-số-trong-phương-thức-method)
      - [Được truyền như một tham số trong hàm dựng (constructor).](#được-truyền-như-một-tham-số-trong-hàm-dựng-constructor)
    - [Từ khóa super trong java](#từ-khóa-super-trong-java)
      - [Gọi trực tiếp constructor của lớp cha gần nhất.](#gọi-trực-tiếp-constructor-của-lớp-cha-gần-nhất)
      - [Gọi trực tiếp biến của lớp cha gần nhất.](#gọi-trực-tiếp-biến-của-lớp-cha-gần-nhất)
      - [Gọi trực tiếp phương thức (method) của lớp cha gần nhất.](#gọi-trực-tiếp-phương-thức-method-của-lớp-cha-gần-nhất)
  - [Garbage Collector trong Java](#garbage-collector-trong-java)
  - [Pass by value trong Java là gì?](#pass-by-value-trong-java-là-gì)


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

| Kiểu dữ liệu | Độ dài theo số bit | Phạm vi biểu diễn giá trị                                 | Mô tả                                                                                                                                     |
| ------------ | ------------------ | --------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| byte         | 8                  | -128 đến 127                                              | Số liệu kiểu byte là một loại điển hình dùng để lưu trữ một giá tri bằng một byte. Chúng được sử dụng rộng rãi khi xử lý một file văn bản |
| char         | 16                 | ‘\u0000’ to ’u\ffff ’                                     | Kiểu Char sử dụng để lưu tên hoặc các dữ liệu ký tự .Ví dụ tên ngườI lao động                                                             |
| boolean      | 1                  | “True” hoặc “False”                                       | Dữ liệu boolean dùng để lưu các giá trị “Đúng” hoặc “sai” Ví dụ : Người lao đông có đáp ứng được yêu cầu của công ty hay không ?          |
| short        | 16                 | -32768 đến 32767                                          | Kiểu short dùng để lưu các số có giá trị nhỏ dưới 32767.Ví dụ số lượng người lao động.                                                    |
| Int          | 32                 | -2,147,483,648 đến +2,147,483,648                         | Kiểu int dùng để lưu một số có giá trị lớn đến 2,147,483,648.Ví dụ tổng lương mà công ty phải trả cho nhân viên.                          |
| long         | 64                 | -9,223,372,036’854,775,808 đến +9,223,372,036’854,775,808 | Kiểu long được sử dụng để lưu một số cố giá trị rất lớn đến 9,223,372,036’854,775,808 .Ví dụ dân số của một nước                          |
| float        | 32                 | -3.40292347E+38 đến +3.40292347E+38                       | Kiểu float dùng để lưu các số thập phân đến 3.40292347E+38 Ví dụ : giá thành sản phẩm                                                     |
| double       | 64                 | -1,79769313486231570E+308 đến +1,79769313486231570E+308   | Kiểu double dùng để lưu các số thập phân có giá trị lớn đến1,79769313486231570E+308 Ví dụ giá trị tín dụng của ngân hàng nhà nước.        |

* Tất cả các biến thuộc kiểu dữ liệu tham chiếu đều được lưu trên vùng nhớ stack.
* Ex: int a = 10;
* Giải thích: int a là cấp phát một ô nhớ 4 byte (kiểu int có độ dài 4 byte) trên vùng nhớ stack. Ô nhớ gồm có Value và địa chỉ.
* A = 10 gán value cho ô nhớ là 10.

### Kiểu dữ liệu tham chiếu
| Kiểu dữ liệu          | Mô tả                                                                                                                                                    |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mảng (Array)          | Tập hợp các dữ liệu cùng kiểu. Ví dụ : tên sinh viên                                                                                                     |
| Lớp (Class)           | Tập hợp các biến và các phương thức.Ví dụ : lớp “Sinhviên” chứa toàn bộ các chi tiết của một sinh viên và các phương thức thực thi trên các chi tiết đó. |
| Giao diện (Interface) | Là một lớp trừu tượng được tạo ra cho phép cài đặt đa thừa kế trong Java.                                                                                |

* Kiểu dữ liệu tham chiếu:những biến thuộc kiểu dữ liệu tham chiếu (hay biến tham chiếu) sẽ được lưu tại vùng nhớ stack và đối tượng sinh ra (sau toán tử new) sẽ được lưu tại vùng nhớ heap. Giá trị của biến tham chiếu chính là địa chỉ của đối tượng được sinh ra đó. (Biến được lưu tại vùng nhớ stack, giá trị là địa chỉ của một đối tượngđược lưu tại vùng nhớ heap).
* Example:
String a = newString(“Java”);

Tương tự ở trên, chúng ta cùng chia nhỏ câu lệnh trên dể dễ hình dung các bước mà chương trình sẽ thực thi trong câu lệnh đó
* Đầu tiên là String a: Cấp phát một ô nhớ trên vùng nhớ stack, ô nhớ này chính là biến tham chiếu a.
* newString(): Cấp phát một ô nhớ trên vùng nhớ heap, ô nhớ này là một đối tượng kiểu String, việc cấp ô nhớ này do toán tử new thực hiện.
* String(“Java”): Gán giá trị “Java” cho ô nhớ trên vùng nhớ heap.
* a = new String(“Java”): Gán địa chỉ của đối tượng trên vùng nhớ heapcho value của ô nhớ trên vùng nhớ stack(biến tham chiếu a).

Như ví dụ trên, ta thấy biến tham chiếu a tương tự như con trỏ (pointer) trong ngôn ngữ C/C++, nó được lưu tại vùng nhớ stack và tham chiếu đến địa chỉ của một đối tượng được tạo ra trên vùng nhớ heap.

### Kiểu dữ liệu Object
Mặc định lớp Object là lớp cha của tất cả các lớp trong java. Nói cách khác nó là 1 lớp cáo nhất trong java.

Sử dụng lớp Object là hữu ích nếu bạn muốn tham chiếu bất kỳ đối tượng nào mà bạn chưa biết kiểu dữ liệu của đối tượng đó. Lưu ý rằng biến tham chiếu của lớp cha có thể tham chiếu đến đối tượng của lớp con được gọi là upcasting.

Lớp Object cung cấp 1 vài cách xử lý chung cho tất cả các đối tượng như đối tượng có thể được so sánh, đối tượng có thể được cloned, đối tượng có thể được notified…

#### Các phương thức của lớp Object

| PHƯƠNG THỨC                                                               | MÔ TẢ                                                                                                                                                              |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
|                                                                           |
| public final Class getClass()                                             | trả về đối tượng lớp Class của đối tượng hiện tại. Từ lớp Class đó có thể lấy được các thông tin metadata của class hiện tại.                                      |
| public int hashCode()                                                     | trả về số hashcode cho đối tượng hiện tại.                                                                                                                         |
| public boolean equals(Object obj)                                         | so sánh đối tượng đã cho với đối tượng hiện tại.                                                                                                                   |
| protected Object clone() throws CloneNotSupportedException                | tạo và trả về bản sao chép (clone) của đối tượng hiện tại.                                                                                                         |
| public String toString()                                                  | trả về chuỗi ký tự đại diện của đối tượng hiện tại.                                                                                                                |
| public final void notify()                                                | đánh thức một luồng, đợi trình giám sát của đối tượng hiện tại.                                                                                                    |
| public final void notifyAll()                                             | đánh thức tất cả các luồng. đợi trình giám sát của đối tượng hiện tại.                                                                                             |
| public final void wait(long timeout)throws InterruptedException           | làm cho Thread hiện tại đợi trong khoảng thời gian là số mili giây cụ thể, tới khi Thread khác thông báo (gọi phương thức notify() hoặc notifyAll()).              |
| public final void wait(long timeout,int nanos)throws InterruptedException | làm cho Thread hiện tại đợi trong khoảng thời gian là số mili giây và nano giây cụ thể, tới khi Thread khác thông báo (gọi phương thức notify() hoặc notifyAll()). |
| public final void wait()throws InterruptedException                       | làm Thread hiện tại đợi, tới khi Thread khác thông báo (gọi phương thức notify() hoặc notifyAll()).                                                                |
| protected void finalize()throws Throwable                                 | Được gọi bởi Garbage Collector trước khi đối tượng bị dọn rác.                                                                                                     |




#### Khai báo Object
1 Object (đối tượng) nó chứa trong đó bao gồm các method (phương thức) và properties (thuộc tính) để tạo ra 1 kiểu dữ liệu hữu ích.

Object xác định hành vi của class. Khi bạn gửi 1 thông điệp vào 1 object, có nghĩa là bạn đang yêu cầu gọi các object hoặc thực hiện 1 trong các phương thức của nó.

Từ 1 quan điểm của lập trình hướng đối tượng, một đối tượng có thể là 1 cấu trúc dữ liệu (data structure), 1 biến (variable) hoặc 1 chức năng (function).

Object được phân bổ vị trí bộ nhớ. Các Object được thiết kế như class phân cấp
```js
ClassName ReferenceVariable = new ClassName();
```
### Lớp Wrapper trong Java
Lớp Wrapper trong Java cung cấp cơ chế cho phép chuyển đổi giữa kiểu dữ liệu nguyên thủy và kiểu đối tượng.

**Autoboxing** là quá trình mà trình biên dịch của Java tự động chuyển đổi giữa kiểu dữ liệu cơ bản **(Primitive type)** về đối tượng tương ứng với lớp **(Wrapper class)** của kiểu dữ liệu đó. Ví dụ, trình biên dịch sẽ chuyển đổi kiểu dữ liệu int sang Integer, kiểu double sang Double, …Và ngược lại là **unboxing**.

![Markdown](https://gpcoder.com/wp-content/uploads/2017/10/Boxing-Unboxing.png)

#### Quá trình Autoboxing
Autoboxing hay Boxing là quá trình chuyển dữ liệu từ kiểu tham trị sang kiểu tham chiếu. Quá trình boxing một biến kiểu tham trị sẽ khởi tạo một đối tượng trong vùng nhớ Heap và copy giá trị của biến tham trị vào đối tượng mới này. Và quá trình boxing được thực hiện nhờ quá trình chuyển đổi ngầm định.
![Markdown](https://gpcoder.com/wp-content/uploads/2017/10/boxing.png)
#### Quá trình Unboxing
**Unboxing** là quá trình ngược lại với Boxing, tức là đưa từ kiểu tham chiếu ra kiểu tham trị. Quá trình này sẽ được thực hiện một cách tường minh. Gồm có 2 bước :
* Bước 1 : Kiểm tra chắc chắn rằng đối tượng đã được boxing đúng kiểu giá trị đưa ra.
* Bước 2 : Copy giá trị sang biến dữ liệu kiểu tham trị.

![Markdown](https://gpcoder.com/wp-content/uploads/2017/10/unboxing.png)

#### Các Lớp Wrapper cho Kiểu Dữ Liệu Nguyên Thủy
Java cung cấp các lớp Wrapper tương ứng cho mỗi kiểu dữ liệu nguyên thủy. Dưới đây là bảng liệt kê các kiểu dữ liệu nguyên thủy và các lớp Wrapper tương ứng:

| Kiểu Nguyên Thủy | Lớp Wrapper |
| ---------------- | ----------- |
| boolean          | Boolean     |
| char             | Character   |
| byte             | Byte        |
| short            | Short       |
| int              | Integer     |
| long             | Long        |
| float            | Float       |
| double           | Double      |


Ví dụ: Chuyển đổi kiểu dữ liệu nguyên thủy thành kiểu Wrapper và ngược lại.
```js
public class WrapperExample {


   public static void main(String[] args) {

       int primitiveInt = 42;

       Integer wrapperInt = Integer.valueOf(primitiveInt); // Chuyển từ int thành Integer (autoboxing)

       int backToInt = wrapperInt.intValue(); // Chuyển từ Integer thành int (unboxing)

       System.out.println(primitiveInt + " " + wrapperInt + " " + backToInt);

   }
```
Kết quả:
> 42 42 42

#### Đặc Điểm của Lớp Wrapper trong Java
##### Khởi Tạo

Các lớp Wrapper có hai cách khởi tạo. Cách thứ nhất là sử dụng giá trị nguyên thủy để tạo đối tượng tương ứng, cách thứ hai là chuyển một chuỗi biểu diễn kiểu dữ liệu nguyên thủy thành đối tượng Wrapper tương ứng. Lưu ý rằng nếu giá trị chuỗi không hợp lệ, nó sẽ ném ra ngoại lệ NumberFormatException.
```js
Integer intObj1 = Integer.valueOf(42); // Tạo từ giá trị nguyên thủy

Integer intObj2 = Integer.valueOf("42"); // Tạo từ chuỗi
```
##### Hàm toString()
Các lớp Wrapper (trừ lớp Character) viết đè hàm toString() để trả về biểu diễn chuỗi của giá trị nguyên thủy.
```js
String intStr = intObj1.toString(); // "42"
```
##### Hàm typeValue()
Các lớp Wrapper có hàm typeValue() để trả về giá trị nguyên thủy tương ứng với đối tượng Wrapper.
```js
int intValue = intObj1.intValue(); // 42
```
##### Hàm equals()
Các lớp Wrapper viết đè hàm equals() để so sánh bằng nhau của các đối tượng Wrapper.
```js
Integer intObj3 = Integer.valueOf(42);
boolean isEqual = intObj1.equals(intObj3); // true
```
Lớp Wrapper trong Java cung cấp một cách tiện lợi để làm việc với kiểu dữ liệu nguyên thủy trong môi trường OOP, cho phép bạn chuyển đổi dễ dàng giữa kiểu dữ liệu nguyên thủy và kiểu đối tượng. Tính năng autoboxing và unboxing giúp giảm thiểu công việc chuyển đổi và làm cho mã nguồn của bạn trở nên dễ đọc hơn
## Các phương thức khởi tạo trong java
### Từ khóa this trong java
Từ khóa this trong java là một biến tham chiếu được sử dụng để tham chiếu tới đối tượng của lớp hiện tại.

Từ khóa this có 6 cách sử dụng sau:
* Tham chiếu tới biến instance của lớp hiện tại.
* Gọi phương thức (method) của lớp hiện tại.
* Gọi hàm dựng (constructor) của lớp hiện tại.
* Trả về instance của lớp hiện tại
* Được truyền như một tham số trong phương thức (method).
* Được truyền như một tham số trong hàm dựng (constructor).

#### Tham chiếu tới biến của lớp hiện tại.
Từ khóa this trong java có thể được dùng để tham chiếu tới biến instance của lớp hiện tại.

Ví dụ:
```js
package com.gpcoder.oop;
 
public class UsingThisExample {
     
    private int id;
     
    private String website;
     
    private String subject;
     
    public UsingThisExample(String website, String subject) {
        website = website;
        subject = subject;
    }
     
    public void print() {
        System.out.println("Id = " + id);
        this.printWebsite();
        this.printSubject();
    }
     
    private void printWebsite() {
        System.out.println("Subject = " + subject);
    }
     
    private void printSubject() {
        System.out.println("Website = " + website);
    }
     
    public static void main(String[] args) {
        UsingThisExample ex1 = new UsingThisExample("gpcoder.com", "OOP");
        ex1.print();
    }
     
}
```
Kết quả:
```js
Id = 0
Subject = null
Website = null
```
Như chúng ta thấy, gía trị của biến được gán trong hàm construct không có tác dụng, do tên thuộc tính và tên biến giống nhau.
Để giải quyết vấn đề này ta sử dụng từ khóa **this** như ví dụ sau:
```js
package com.gpcoder.oop;
 
public class UsingThisExample {
     
    private int id;
     
    private String website;
     
    private String subject;
     
    public UsingThisExample(String website, String subject) {
        this.website = website;
        this.subject = subject;
    }
     
    public void print() {
        System.out.println("Id = " + id);
        this.printWebsite();
        this.printSubject();
    }
     
    private void printWebsite() {
        System.out.println("Subject = " + subject);
    }
     
    private void printSubject() {
        System.out.println("Website = " + website);
    }
     
    public static void main(String[] args) {
        UsingThisExample ex1 = new UsingThisExample("gpcoder.com", "OOP");
        ex1.print();
    }
     
}

```
Kết quả:
```js
Id = 0
Subject = OOP
Website = gpcoder.com
```
Nếu biến cục bộ và biến toàn cục có tên khác nhau thì không cần sử dụng từ khóa this. Tuy nhiên, nên sử dụng từ khóa this để chương trình được rõ ràng và dễ hiểu.
Ví dụ:
Persion.java
```js
package com.gpcoder.oop;
 
public class Student extends Person {
    private int id;
    private String name;
 
    public Student(int id, String name) {
        this.id = id;
        this.name = name;
    }
 
    public void print() {
        System.out.println("id = " + id + ", name = " + name);
    }
 
    public void printChild1() {
        this.print();
    }
 
    public void printChild2() {
        super.print();
    }
 
    public static void main(String args[]) {
        Student student = new Student(1, "gpcoder");
        student.print();
        System.out.println("---");
        student.printChild1();
        System.out.println("---");
        student.printChild2();
    }
 
}
```
Kết quả:
```js
id = 1, name = gpcoder
---
id = 1, name = gpcoder
---
This is parent class
```
Như ví dụ trên, rõ ràng là trong trường hợp mà chương trình của bạn có nhiều class, các class có sử dụng kế thừa thì việc để từ khóa this sẽ giúp chương trình của bạn rõ ràng hơnc hạn chế sai sót do không xác định được đang gọi phương thức ở lớp cha hay lớp hiện tại.
#### Gọi phương thức của lớp hiện tại.
Chúng ta có thể sử dụng từ khóa **this** để gọi phương thức của lớp hiện tại. Nếu không sử dụng từ khóa **this**, trình biên dịch sẽ tự động thêm từ khóa **this** cho việc gọi phương thức.
Ví dụ:
```js
package com.gpcoder.oop;
 
public class UsingThisExample {
     
    private int id;
     
    private String website;
     
    private String subject;
     
    public UsingThisExample(String website, String subject) {
        this.website = website;
        this.subject = subject;
    }
     
    public void print() {
        System.out.println("Id = " + id);
        this.printWebsite();
        printSubject();
    }
     
    private void printWebsite() {
        System.out.println("Subject = " + subject);
    }
     
    private void printSubject() {
        System.out.println("Website = " + website);
    }
     
    public static void main(String[] args) {
        UsingThisExample ex1 = new UsingThisExample("gpcoder.com", "OOP");
        ex1.print();
    }
     
}
```
Kết quả:
```js
Id = 0
Subject = OOP
Website = gpcoder.com
```
Như ví dụ trên, từ khóa **this** được sử dụng để gọi phương thức *this.printWebsite()*. Phương thức *printSubject()* trình biên dịch sẽ tự động thêm từ khóa this cho việc gọi phương thức.
#### Gọi Constructor của lớp hiện tại.
Phương thức **this()** có thể được sử dụng để gọi constructor của lớp hiện tại. Cách sử dụng này sẽ hữu dụng hơn nếu bạn có nhiều constructor trong một lớp và bạn muốn sử dụng lại constructor.
Phương thức **this()** phải được khai báo dòng lệnh đầu tiên trong constructor.
Ví dụ:
```js
package com.gpcoder.oop;
 
public class UsingThisExample {
 
    private int id;
 
    private String website;
 
    private String subject;
 
    public UsingThisExample() {
        this.id = 1;
        this.website = "https://gpcoder.com";
    }
 
    public UsingThisExample(String website ) {
        this(); // Bắt buộc phải dòng lệnh đầu tiên trong constructor
        this.website = website ;
    }
 
    public UsingThisExample(String website, String subject) {
        this(website); // Bắt buộc phải dòng lệnh đầu tiên trong constructor
        this.subject = subject;
    }
 
    public void print() {
        System.out.println("Id = " + id);
        this.printWebsite();
        this.printSubject();
    }
 
    private void printWebsite() {
        System.out.println("Subject = " + subject);
    }
 
    private void printSubject() {
        System.out.println("Website = " + website);
    }
 
    public static void main(String[] args) {
        UsingThisExample ex1 = new UsingThisExample("gpcoder.com", "OOP");
        ex1.print();
    }
 
}
```
Kết quả:
```js
Id = 1
Subject = OOP
Website = gpcoder.com
```
#### Trả về instance của lớp hiện tại
Chúng ta có thể trả về instance của lớp hiện tại bằng cách sử dụng từ khóa **this**. Trong trường hợp này, kiểu trả về của phương thức phải là **class của lớp hiện tại**.

Ví dụ:
```js
package com.gpcoder.oop;
 
public class UsingThisExample {
 
    private int id;
 
    private String website;
 
    private String subject;
 
    public UsingThisExample() {
        this.id = 1;
    }
 
    public UsingThisExample setWebsite(String website) {
        this.website = website;
        return this;
    }
 
    public UsingThisExample setSubject(String subject) {
        this.subject = subject;
        return this;
    }
 
    public void print() {
        System.out.println("Id = " + id);
        this.printWebsite();
        this.printSubject();
    }
 
    private void printWebsite() {
        System.out.println("Subject = " + subject);
    }
 
    private void printSubject() {
        System.out.println("Website = " + website);
    }
 
    public static void main(String[] args) {
        UsingThisExample ex1 = new UsingThisExample()
                .setSubject("OOP")
                .setWebsite("gpcoder.com");
        ex1.print();
    }
 
}
```
Kết quả:
```js
Id = 1
Subject = OOP
Website = gpcoder.com
```

Như ví dụ trên, phương thức *setWebsite* và *setSubject* trả về tham chiếu tới biến instance của lớp hiện tại.
#### Được truyền như một tham số trong phương thức (method).
Từ khóa **this** có thể được dùng như một tham số trong phương thức (method). Cách dùng này chủ yếu được sử dụng trong sử lý sự kiện.
Ví dụ:
Helper.java
```js
public class Helper {
     
    public void print(UsingThisExample ex) {
        System.out.println("Id = " + ex.getId());
        System.out.println("Website = " + ex.getWebsite());
    }
     
}
```
UsingThisExample.java

```js
public class UsingThisExample {
    private int id;
    private String website;
     
    UsingThisExample () {
        this.id = 1;
        this.website = "gpcoder";
    }
     
    public void print() {
        Helper helper = new Helper();
        helper.print(this);
    }
 
    public int getId() {
        return id;
    }
 
    public String getWebsite() {
        return website;
    }
     
    public static void main(String[] args) {
        UsingThisExample ex = new UsingThisExample();
        ex.print();
    }
}
```
Kết quả:
```js
Id = 1
Website = gpcoder
```

Như ví dụ trên, phương thức print của lớp *UsingThisExample* truyền tham số là **this** (tham chiếu biến instance của lớp *UsingThisExample*) sang cho phương thức print của lớp *Helper* xử lý.
#### Được truyền như một tham số trong hàm dựng (constructor).
Từ khóa this có thể được dùng như một tham số trong constructor. Cách dùng này rất hữu ích nếu chúng ta sử dụng một đối tượng trong nhiều lớp.
Ví dụ:
Helper.java
```js
public class Helper {
     
    private UsingThisExample ex;
     
    public Helper(UsingThisExample ex) {
        this.ex = ex;
    }
     
    public void printId() {
        System.out.println("Id = " + ex.getId());
    }
     
    public void printWebsite() {
        System.out.println("Website = " + ex.getWebsite());
    }
     
}
```
UsingThisExample.java
```js
public class UsingThisExample {
    private int id;
    private String website;
     
    UsingThisExample () {
        this.id = 1;
        this.website = "gpcoder";
    }
     
    public void print() {
        Helper helper = new Helper(this);
        helper.printId();  
        helper.printWebsite();
    }
 
    public int getId() {
        return id;
    }
 
    public String getWebsite() {
        return website;
    }
     
    public static void main(String[] args) {
        UsingThisExample ex = new UsingThisExample();
        ex.print();
    }
}
```
Kết quả:
```js
Id = 1
Website = gpcoder
```
Như ví dụ trên, phương thức print gọi hàm khởi tạo của lớp *Helper* với tham số là **this** (tham chiếu biến instance của lớp *UsingThisExample())*, sau đó gọi hàm *printId* và *printWebsite* để xử lý. Cách này hữu ích khi cần tái sử dụng object ở nhiều phương thức khác nhau, trong ví dụ này là *printId* và *printWebsite*.
### Từ khóa super trong java
Từ khóa **super** trong java là một biến tham chiếu được sử dụng để tham chiếu trực tiếp đến **đối tượng của lớp cha gần nhất**.

Bất cứ khi nào bạn tạo ra instance (thể hiện) của lớp con, một instance của lớp cha được tạo ra ngầm định, nghĩa là được tham chiếu bởi biến **super**.

Từ khóa super có 3 cách sử dụng sau:
* Gọi trực tiếp hàm dựng (constructor) của lớp cha gần nhất.
* Gọi trực tiếp thuộc tính (field) của lớp cha gần nhất.
* Gọi trực tiếp phương thức (method) của lớp cha gần nhất.
####  Gọi trực tiếp constructor của lớp cha gần nhất.
Ví dụ:
Parent.java
```js
public class Parent {
     
    private String website;
     
    public Parent() {
        System.out.println("This is parent");
        print();
    }
     
    public Parent(String website) {
        this.website = website;
        System.out.println("This is parent");
        print();
    }
     
    public void print() {
        System.out.println("Website = " + website);
    }
}
```
Child.java
```js
public class Child extends Parent {
 
    public Child() {
        System.out.println("This is child");
    }
 
    public Child(String website) {
        super(website);
        System.out.println("This is child");
    }
     
    public static void main(String[] args) {
        Child child1 = new Child();
        System.out.println("---");
        Child child2 = new Child("gpcoder.com");
    }
}
```
Kết quả:
```js
This is parent
Website = null
This is child
---
This is parent
Website = gpcoder.com
This is child
```
Như ví dụ trên:

* Trong hàm *main*, *child1* gọi hàm khởi tạo không có tham số, hàm khởi tạo *Child()* không gọi **super()**, khi đó trình biên dịch sẽ tự động thêm **super()** vào hàm constructor để gọi khởi tạo ở lớp cha.
* Trong hàm *main*, *child2* gọi hàm khởi tạo có tham số, hàm khởi tạo *Child(str)* gọi **hàm super()** để gọi khởi tạo ở lớp cha có tham số.

#### Gọi trực tiếp biến của lớp cha gần nhất.
Ví dụ:
Parent.java
```js
public class Parent {
     
    public String website = "gpcoder.com";
    public String subject = "OOP";
     
    public Parent() {
         
    }
}
```
Child.java
```js
public class Child extends Parent {
     
    public String website = "https://gpcoder.com";
     
    public Child() {
         
    }
     
    public void printParent() {
        System.out.println("Short link: " + super.website);
        System.out.println("Subject " + subject);
    }
     
    public void printChild() {
        System.out.println("Full link: " + website);
        System.out.println("Subject " + subject);
    }
     
    public static void main(String[] args) {
        Child child = new Child();
        child.printParent();
        System.out.println("---");
        child.printChild();
    }
}
```
Kết quả:
```js
Short link: gpcoder.com
Subject OOP
---
Full link: https://gpcoder.com
Subject OOP
```
Như ví dụ trên:
* Phương thức *printParent()* sử dụng **super** để sử dụng biến *website* của lớp *Parent*, do lớp *Child* có biến *website* cùng tên với lớp *Parent*. Nếu không gọi *super*, như phương thức *printChild* thì sẽ gọi biến *website* của lớp *Child*.
* Trường hợp lớp *Child* không có biến trùng tên với lớp cha thì có thể không cần sử dụng từ khóa **super**. Trong ví dụ trên là biến *subject*, ở lớp *Child* không có biến này nên không cần sử dụng từ khóa **super**.
#### Gọi trực tiếp phương thức (method) của lớp cha gần nhất.
Ví dụ:
Parent.java
```js
public class Parent {
     
    private String website;
     
    public Parent(String website) {
        this.website = website;
    }
     
    public void print() {
        System.out.println("Website = " + website);
    }
     
    public void welcome() {
        System.out.println("Welcome to gpcoder.com");
    }
}
```
Child.java
```js
public class Child extends Parent {
     
    public Child(String website) {
        super(website);
    }
 
    public void printChild1() {
        print();
    }
 
    public void printChild2() {
        super.print();
        welcome();
    }
     
    public void print() {
        System.out.println("Subject = OOP");	
    }
     
    public static void main(String[] args) {
        Child child = new Child("gpcoder.com");
        child.printChild1();
        System.out.println("---");
        child.printChild2();
    }
}
```
Kết quả:
```js
Subject = OOP
---
Website = gpcoder.com
Welcome to gpcoder.com
```
Như ví dụ trên:
* Phương thức *printChild2()* sử dụng **super** để gọi phương thức *print* của lớp *Parent*, do lớp *Child* đã ghi đè (override) lại phương thức của lớp cha. Nếu không gọi **super** như phương thức *printChild1* thì sẽ gọi hàm *print* của lớp *Child*.
* Trường hợp lớp *Child* không ghi đè (override) lại phương thức của lớp cha thì có thể không cần sử dụng từ khóa **super**. Trong ví dụ trên là phương thức *welcome()*, ở lớp *Child* không có viết lại phương thức này.
## Garbage Collector trong Java
Garbage collection (Quá trình thu gom rác) trong máy ảo Java (JVM) là quá trình xác định và loại bỏ các Object không được sử dụng (unreferenced) khỏi bộ nhớ Heap. Không gian trống này sẽ được cấp phát cho những Object mới. Với các ngôn ngữ như C thì việc giải phóng bộ nhớ được thực hiện một cách thủ công (bằng những lệnh khởi tạo, giải phóng bộ nhớ). Với Java thì việc giải phóng bộ nhớ được thực hiện một cách tự động.

Garbage collector là chương trình chạy nền, nó theo dõi toàn bộ các Object trong bộ nhớ (Heap) và tìm ra những Object nào không được dùng nữa (không có Object nảo reference đến nó). Toàn bộ những Object không có reference sẽ bị xóa.

Quá trình thu gom rác cơ bản thông qua 3 bước sau:

* Marking: Là bước đánh dấu những Object còn sử dụng và những Object không còn sử dụng.

![Markdown](https://images.viblo.asia/70713868-22b1-40c9-853b-4bade54c0c5d.png)

* Normal deleting: Trình Garbage Collector sẽ xóa cá Object không còn sử dụng.

![Markdown](https://images.viblo.asia/24d99c89-1631-4c33-9e88-6b22f37c8a1f.png)

* Deletion with Compacting: Sau khi những Object không còn được sử dụng bị xóa, những Object còn được sử dụng sẽ được "gom" lại gần nhau. Điều đó làm tăng hiệu xuất sử dụng bộ nhớ trống để cấp phát cho những Object mới.

![Markdown](https://images.viblo.asia/e8667a54-e7fa-4521-9b5c-536085d8f95b.png)

Để thực hiện việc tự động giải phóng các Object khi chúng không được sử dụng thì bộ nhớ Heap được chia thành các phần nhỏ như hình dưới đây.

![Markdown](https://images.viblo.asia/3befc0de-4ea3-4153-b8c3-6d4035c9ace4.png)

Young Generation Là nơi chứa toàn bộ Object mới được khởi tạo. Khi vùng nhớ Young generation đầy thì garbage collectior là Minor GC hoạt động. Vùng Young generation lại được chia thành 3 vùng nhỏ hơn là Eden và 2 vùng Survivor là S0, S1.

Ban đầu mọi Object mới tạo được chứa ở vùng Eden, khi Eden đầy thì Minor GC chuyển chúng sang vùng S0, S1.

![Markdown](https://images.viblo.asia/53ccbc48-dfbf-4cd3-9b64-60649e8f0346.png)

Minor GC liên tục theo dõi các Object ở S0, S1. Sau "nhiều" chu kỳ quét mà Object vẫn còn được sử dùng thì chúng mới được chuyển sang vùng nhớ Old generation. Old generation được quản lý bởi garbage collectior khác là Major GC.

![Markdown](https://images.viblo.asia/c7046f31-68e5-406e-a32a-fc8131e86963.png)

Hình trên mô phòng 2 Object được chuyển từ vùng Young generation sang Old generation sau 9 chu kỳ quét của Minor GC. Những ô màu vàng tượng chưng cho những Object đã không còn được sử dụng (unreferenced). Chúng sẽ được xóa khi Minor GC hay Majo GC clear vùng nhớ nó quản lý.

Mô hình vùng nhớ Heap có vùng Perm (Permanent Generation), Perm không phải một phần của Heap. Perm không chứa Object, nó chứa metadata của JVM như các thư viện Java SE, mô tả các class và các method của ứng dụng.

## Pass by value trong Java là gì?
Khi các tham số đầu vào của một method là
* Pass-by-value: Method được gọi sẽ sao chép một bản sao của tham số truyền vào và hoạt động trên chúng. Mọi thay đổi trên bản sao này không ảnh hưởng đến giá trị ban đầu.

![Markdown](https://luanvv.com/static/img/uploads/0_q5Tkq9ctyYd0gd1F.gif)

Ví dụ về việc truyền giá trị (pass by value) trong java
Trong ví dụ này, giá trị data không bị thay đổi sau khi gọi phương thức change()
```js
public class Operation1 {
    int data = 50;
 
    void change(int data) {
        data = data + 100;
    }
 
    public static void main(String args[]) {
        Operation1 op = new Operation1();
 
        System.out.println("Trước khi thay đổi: " + op.data);
        op.change(500);
        System.out.println("Sau khi thay đổi: " + op.data);
    }
}
```
Output:
```js
Trước khi thay đổi: 50
Sau khi thay đổi: 50
```












