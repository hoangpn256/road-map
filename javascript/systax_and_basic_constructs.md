## Table of Contents - Cấu trúc **node**

[1. Introduction to Javascript - Giới thiệu về JS(Javascript)](#head1)

[2. How to Use Javascript - Cách sử dụng JS](#head2)

[3. Syntax and Basic Construct - Cú pháp và cấu trúc cơ bản](#head3)

[4. Conclusion - Kết luận](#head4)

<a name='head1' />

### **1. Introduction to Javascript - Giới thiệu về JS(Javascript)**

- Js là một ngôn ngữ lập trình động, hoặc kịch bản cho phép tạo ra trang web động(cập nhật nội dung theo ngữ cảnh, điều khiển đa phương tiện, hình ảnh, validates dữ liệu đầu vào(bên phía người dùng)... và rất nhiều thứ khác nữa.)

- Đấy là hồi trước thôi, giờ thì JS là 1 ngôn ngữ lập trình rất mạnh mẽ, với tốc độ phát triển đáng kinh ngạc, và gần như bất kì 1 developer nào cũng đều phải biết nó. Không chỉ xử lý ở phía người dùng (_client side_) mà giờ đây js còn rất mạnh mẽ ở phía máy chủ(_server side_)

**_Note:_** Ở phần này, chúng ta sẽ tìm hiểu cơ bản về JS

<a name='head2' />

### **2. How to Use Javascript - Cách sử dụng JS**

Để sử dụng JS trong dự án về website, có 2 cách chính, thường thấy là:

#### INTERNAL JAVASCRIPT

- Js được viết trực tiếp cùng với file **HTML** mà bạn mong muốn sử dụng.
- Code JS sẽ được đặt trong cặp thẻ `<script> </script>`

Ví dụ:

```html
<!-- index.html -->
<!DOCTYPE html>
<html>
  <head>
    <title>Javascript Syntax and Basic Constructs</title>
  </head>
  <body>
    <h1>Hello</h1>

    <!-- Javascript area -->
    <script>
      console.log("Hey, Javascript!!");
    </script>
  </body>
</html>
```

`console.log` có thể làm bạn bối rối, đừng lo lắng, chúng ta sẽ tìm hiểu nó sau.

#### EXTERNAL JAVASCRIPT

- Js được viết trong một file khác
- Được tham chiếu 1 cách đơn giản vào file **HTML** mà bạn mong muốn sử dụng.

Ví dụ:

```js
// script.js
console.log("Hey, Javascript!!");
```

Trong file html của bạn(ví dụ: `index.html`), chúng ta sẽ tham chiếu đến file js này bằng cách chèn đoạn mã sau: `<script src='script.js'></script>`

`src` ở đây có nghĩa là nơi chưa `file script` mà bạn muốn tham chiếu đến

**_Note:_**

- Qua đó, chúng ta thấy dược việc sử dụng `EXTERNAL JAVASCRIPT` so với `INTERNAL JAVASCRIPT` là tách biệt code script và html. Do đó làm cho code của bạn `dễ đọc`, `dễ bảo trì`, `dễ phát triển hơn`.

- Việc đặt tham chiếu trong file HTML ở đâu? Có thể đặt ở bất kì đâu trong trang web của bạn, nhưng thường thì tham chiếu sẽ được đặt trong cặp thẻ `head` của file `HTML`, hoặc sẽ là trong cặp thẻ `body`, gần thẻ đóng `</body>` vì lúc này, các phần tử `HTML` đã được load hết, do đó `code Js` có thể chạy 1 cách tốt nhất.

<a name='head3' />

### **3. Syntax and Basic Construct - Cú pháp và cấu trúc cơ bản**

#### 1. Thường thì tất cả các câu lệnh nên được kết thúc bằng dấu `;`

- Điều này giúp các trình biên dịch hiểu được là bạn đã kết thúc câu lệnh này.

- Nếu không có `;` đôi khi bạn có thể gặp kết quả không mong muốn với các câu lệnh của chính mình. Trình biên dịch có thể nối tiếp câu lệnh phía sau, với phía trước luôn, từ đó có thể dẫn đến lỗi logic, hoặc syntax không mong muốn.

- Thực ra thì đến thời điểm hiện tại, việc có dấu `;` ở cuối này cũng sẽ không làm bạn sai logic được, nhưng nó là `1 thói quen nên có`.

#### 2. Comments

- **Comments** là rất cần thiết, để giúp chính bạn, hoặc người khác có thể hiểu rõ hơn về các đoạn code của mình.

- Trình biên dịch sẽ không biên dịch các _comments_ này

Ví dụ

```js
// This is a single-line comment, but guess what,
/*
  I am a comment that can span
  over
  multiple
  lines
  The interesting part is the interpreter does not try to execute me
*/
```

#### 3. Statements - Các câu lệnh

- Các câu lệnh JS sẽ đuợc browser(trình duyệt web của bạn, ví dụ: firefox, chrome, ...) thực thi.

```js
//statements
const x = 3;
const y = 7;
let z = x + y;
alert("Wow, this is an alert!!");
```

Như thấy ví dụ bên trên, các câu lệnh thường sẽ được kết thúc bằng `;`

#### 4. Whitespaces - Khoảng trắng

- JS khi biên dịch sẽ bỏ qua các khoảng trắng, do đó đoạn code trên có thể viết lại như sau:

```js
//statements
const x = 3;
const y = 7;
let z = x + y;
alert("Wow, this is an alert!!");
```

- Việc bạn dùng `Khoảng trắng` sẽ giúp cho code dễ đọc hơn. Chứ không có tác dụng ngăn cách các câu lệnh.

#### 5. Variables - Biến

- Các `biến`, bạn có thể hiểu đơn giản như 1 thùng chứa, sử dụng để lưu giá trị, thay vì lặp đi, lặp lại một giá trị cho cùng 1 mục đích sử dụng, bạn có thể chỉ định nó cho 1 `biến`

```js
var a = 1;
const b = 2;
let c = 3;
let sum = a + b + c;
console.log("sum is", sum);
```

- Các từ khóa để khai báo biến như `var`, `let, const` là 2 từ khóa được xuất hiện ở những phiên bản update sau, hiện giờ thì chúng ta gần như không sử dụng từ khóa `var`

#### 6. Operators - Toán tử

- Có rất nhiều các toán tử trong JS, ở đây mình chỉ ví dụ 1 vài, các bạn có thể tìm hiểu kĩ hơn về phần này ở trên [GOOGLE](https://google.com).

1. Arithmetic Operators - Toán tử số học

- Cộng `+`, Trừ `-`, Nhân `*`, Chia `/`, Increment(tăng) `++`, Decrement(giảm) `--`, Module(phép chia lấy số dư) `%`

```js
let num1 = 5;
let num2 = 6;

num1 + num2;
//returns 11

num2 % num1;
//returns 1
```

2. Assignment Operators - Toán tử gán

- Các toán tử này dùng để gán giá trị cho các biến.
- Ví dụ một số toán tử như: `=, /=, *=, %=, -=, +=`

```js
let num1 = 10;
// num1 would return 10

num1 += 10;
// num1 would would return 10 + 10 = 20
```

#### 7. Loops - Vòng lặp

- Đối với các lập trình viên thì quá quen thuộc với thuật ngữ `loop` này rồi.
- Thi thoảng, bạn muốn làm đi làm việc 1 đoạn mã nhiều lần, 1, 2, 3 lần thì không sao, nhưng nếu với số lượng lớn, 100 lần, 1000 lần, thì nó sẽ là `vấn đề`, ví dụ:

```js
let number = 5;
number = number + 1; // add 1st time
number = number + 2; // add 2nd time
number = number + 3; // add 3rd time
number = number + 4; // add 4th time
number = number + 5; // add 5th time
console.log(number); // Expected output: 10
```

- **Types of Loops in Javascript - Các kiểu lặp trong JS**

  Một số các kiểu thường thấy là:

  - While loop
  - Do...while loop
  - for loop

**while loop**

```js
let number = 5;
// we have to initialize the count variable
let count = 0;
// while loop
while (count <= 5) {
  number = number + 1;
  count = count + 1;
}
console.log(number);
// Expected output: 10
```

- Hiểu đơn giản cách sử dụng vòng lặp này là: Cho đến khi `điều kiện` trong `while` còn đúng, thì còn thực hiện câu lệnh bên trong `{}` cạnh `while`

- Lưu ý nhỏ ở đây là tại sao chúng ta lại tăng biến `count = count + 1`. Nếu không tăng biến `count` thì nó cứ mãi bằng `0` và vòng lặp sẽ diễn ra mãi mãi. Cũng vì thế, khi nào bạn muốn thực hiện 1 vòng lặp vô hạn, hãy sử dụng điều kiện `luôn đúng` cho nó.

**do while loop**

```js
let number = 5;
// we have to initialize the count variable
let count = 6;
do {
  number = number - 1;
  count = count - 1;
} while (count <= 5 && count >= 0);
console.log(number);
//Expected output: 10
```

- Phương pháp này tương tự sử dụng **while loop**, chỉ có 1 khác biệt lớn nhất là: **while loop** sẽ kiểm tra điều kiện trước, rồi sau đó mới thực hiện vòng lặp. Nhưng **do while** thì sẽ thực hiện vòng lặp `ít nhất 1 lần`, trước khi kiểm tra `điều kiện` thoả mãn cho những vòng lặp tiếp theo

**for loop**

- Cấu trúc vòng lặp for thường thấy như sau

```js
for (initialization; condition; incremental) {
  // run this code
}
```

- Dành cho ví dụ trên, chúng ta có thể viết lại

```js
let number = 5;
for (let count = 0; count <= 5; count++) {
  number = number + 1;
}
console.log(number);
// Expected output: 10
```

- Cách viết này theo mình là được sử dụng nhiều nhất, phần lớn có thể kiểm soát hết các trường hợp cần đến lặp. Tuy nhiên, không có gì là hoàn hảo, nhiều trường hợp chúng ta vẫn phải sử dụng các kiểu lặp bên trên.

> Ngoài ra, hiện giờ còn sử dụng khá nhiều cách `loop` khác nữa, nhưng về cơ bản thì cơ chế hoạt động là như nhau. bạn có thể google để tham khảo thêm nhé.

#### 8. Conditions - Điều kiện rẽ nhánh

- Đôi khi trong lúc viết code, bạn cần xử lý rẽ nhánh kiểu như, `nếu > 0 thì in ra là số dương, nếu < 0 thì in ra số âm` chẳng hạn, thì đây là lúc chúng ta cần đến `điều kiện rẽ nhánh`

- Trong JS, có 2 kiểu thường thấy:
  - `if statements`
  - `switch statements`

**if statements**

```js
const number = 5;

if (number > 5) {
  console.log("The number is greater than 5");
}
// Expected output is nothing
```

- Như bạn thấy ở ví dụ, `if(điều kiện)`, bên trong `{}` chính là các `câu lệnh được thực thi nếu điều kiện đúng`

```js
const number = 5;
if (number > 5) {
  console.log("The number is greater than 5");
} else if (number == 10) {
  console.log("The number is equal to 10");
} else {
  console.log("The number is not greater than 5 and not equal to 10");
}
// Expected output: The number is not greater than 5 and not equal to 10
```

- Dùng kết hợp cùng `if`, đương nhiên là `else` rồi, thậm chí chúng ta có thể `else if` như ví dụ bên trên.

**if statements**

- Tương tự như `if`, sử dụng trong trường hợp bạn có nhiều lựa chọn, ví dụ:

```js
const dayOfWeek = 2;

switch (number) {
  case 2:
    console.log("The day is Monday");
    break;
  case 3:
    console.log("The day is Tuesday");
    break;
  case 4:
    console.log("The day is Wednesday");
    break;
  case 5:
    console.log("The day is Thursday");
    break;
  case 6:
    console.log("The day is Friday");
    break;
  case 7:
    console.log("The day is Saturday");
    break;
  default:
    console.log("The day is Sunday");
}
// Expected output: The day is Monday
```

- Câu lệnh `default` ở đây nghĩa là nếu không có `case` nào bên trên phù hợp, thì nó sẽ thực thi câu lệnh ở `default`
- Câu lệnh `break` ở đây dùng để thoát khỏi `{}`. Nếu không có câu lệnh `break`, thì JS sẽ tự chạy những câu lệnh tiếp theo, nghĩa là khi đó `logic` của bạn có thể bị sai, để hiểu rõ hơn, hay google nha.

#### 9. Functions - Hàm

- Thường được dùng để nhóm các câu lệnh cùng chức năng lại với nhau, giúp cho việc dễ kiểm soát code, dễ `tái sử dụng lại`

```js
function myFunction1(args) {
  // block of codes
}
```

`args` là tham số truyền vào cho hàm

Để hiểu rõ hơn, chúng ta cùng xem ví dụ dưới đây:

```js
function sum(a, b) {
  return a + b;
}

let result = sum(3, 4);
// Expected output: 7
```

Như chúng ta thấy, chúng ta nhóm chức năng `tính tổng` thành 1 `hàm`, sau đó sử dụng chúng như bên dưới.

- Lưu ý, ở đây có câu lệnh `return` nghĩa là mong muốn `hàm` của chúng ta trả về 1 `kết quả` nào đó, để hiểu rõ hơn, hãy google nhé.

<a name='head4' />

### **4. Conclusion - Kết luận**

- JS là ngôn ngữ rất mạnh mẽ mà phần lớn lập trình viên cần biết, xin nhắc lại là **phần lớn cần phải biết**
- JS còn rất nhiều khái niệm quan trọng khác, nếu bạn muốn hiểu nó sâu hơn, thì cần tìm hiệu học hỏi nhiều hơn nữa.

---

Copyright © **[@hoangpn](https://hoangpn.com)**, member of **Hituno Team**, 2020
