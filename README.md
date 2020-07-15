# Định nghĩa

 - Dart là ngôn ngữ lập trình phát triển ứng dụng cho mọi nền tảng. Được phát triển bởi Google và sử dụng xây ứng dụng cho **thiết bị di động(mobile app)**, **máy tính(desktop)**, **hệ thống(server)** và **ứng dụng trên trình duyệt(web app)**
 - Dart là một ngôn ngữ hướng đối tượng, được xác định theo lớp, với cơ chế garbage-collected, sử dụng cú pháp kiểu C để dịch mã tùy ý sang JavaScript.
 - Dart có thể biên dịch mã sang Javascript hoặc native mobile. Có hỗ trợ interfaces, mixins, abstract classes, reified generics, và type inference.

# Hello World

Mọi ứng dụng đều phải chạy qua `main()` function. Để hiển thị text trên console, sử dụng lệnh `print()`

```
void main() {
  print('Hello, World!');
}
```

# Variables

Dưới đây là cách tạo biến và khởi tạo nó:
```
var name = "datnx";
```
biến `name` chứa reference với `String` Object và có giá trị là `datnx`

Ngoài ra ta có các cách khai báo biên khác
```
String name = "datnx";
```

Ta có thể gán giá trị cho biến bằng cách
```
name = "datNX";
assert(name == datNX);
```

Nếu không muốn thay đổi giá trí của biến, ta có thể sử dụng
```
const name = "datnx";
name = "datNX"; // Trình biên dịch sẽ thông báo lỗi chỗ này
```
```
final name = "datnx";
name = "datNX"; // Trình biên dịch sẽ thông báo lỗi chỗ này
```

Các biến không được khởi tạo mặc định sẽ là `null`
```
int age;
assert(age == null);
```

# Control flow statements

Dart hỗ trợ các control flow statements sau:
- ```if``` và ```else```
- Vòng lặp ```for```
- Vòng lặp```while``` và ```do while``` 
- ```break``` và ```continue```
- ```switch``` và ```case```
- ```assert```

#### `If` và `else`
Ví dụ
```
if (isRaining()) {
  you.bringRainCoat();
} else if (isSnowing()) {
  you.wearJacket();
} else {
  car.putTopDown();
}
```

#### Vòng lặp `for`

Ví dụ
```
var message = StringBuffer('Dart is fun');
for (var i = 0; i < 5; i++) {
  message.write('!');
}
```

Hoặc `forEach`
```
candidates.forEach((candidate) => candidate.interview());
```

Hoặc `for-in`
```
var collection = [0, 1, 2];
for (var x in collection) {
  print(x); // 0 1 2
}
```

#### Vòng lặp `while` và `do while`

Ví dụ
```
while (!isDone()) {
  doSomething();
}
```

```
do {
  printLine();
} while (!atEndOfPage());
```

#### `Break` và `Continue`

Sử dụng `break` để dừng vòng lặp
```
while (true) {
  if (shutDownRequested()) break;
  processIncomingRequests();
}
```

Sử dụng `continue` để chuyển qua vòng lặp tiếp theo
```
for (int i = 0; i < candidates.length; i++) {
  var candidate = candidates[i];
  if (candidate.yearsExperience < 5) {
    continue;
  }
  candidate.interview();
}
```
Ngoài cách trên ta có thể sử dụng cách sau
```
candidates
    .where((c) => c.yearsExperience >= 5)
    .forEach((c) => c.interview());
```

#### `Switch` và `Case`

`switch` có thể sử dụng để so sánh giữa `integer`, `string`, hoặc `enum`

```
var command = 'OPEN';
switch (command) {
  case 'CLOSED':
    executeClosed();
    break;
  case 'PENDING':
    executePending();
    break;
  case 'APPROVED':
    executeApproved();
    break;
  case 'DENIED':
    executeDenied();
    break;
  case 'OPEN':
    executeOpen();
    break;
  default:
    executeUnknown();
}
```

Kết thúc mỗi `case` đều phải có `break`, nếu không sẽ gặp lỗi trong quá trình biên dịch
```
var command = 'OPEN';
switch (command) {
  case 'OPEN':
    executeOpen();
    // ERROR: Missing break

  case 'CLOSED':
    executeClosed();
    break;
}
```

Tuy nhiên, Dart có hỗ trợ empty `case`
```
var command = 'CLOSED';
switch (command) {
  case 'CLOSED': // Empty case falls through.
  case 'NOW_CLOSED':
    // Runs for both CLOSED and NOW_CLOSED.
    executeNowClosed();
    break;
}
```
Nếu bạn muốn chạy tiếp case dưới, thì có thể sử dụng `continue` và `label`
```
var command = 'CLOSED';
switch (command) {
  case 'CLOSED':
    executeClosed();
    continue nowClosed;
  // Continues executing at the nowClosed label.

  nowClosed:
  case 'NOW_CLOSED':
    // Runs for both CLOSED and NOW_CLOSED.
    executeNowClosed();
    break;
}
```

#### Assert

Dùng để kiểm tra điều kiện, nếu không sẽ bắn ra lỗi `AssertionError`

```
// Make sure the variable has a non-null value.
assert(text != null);

// Make sure the value is less than 100.
assert(number < 100);

// Make sure this is an https URL.
assert(urlString.startsWith('https'));
```



