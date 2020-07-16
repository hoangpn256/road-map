# Numbers, Collections, Strings, and more

#### Numbers

dart:core định nghĩa các lớp `num`, `int`, và `double`.

Bạn có thể chuyển kiểu dữ liệu `String` sang `integer` hoặc `double` bằng cách sử dụng function `parse()`.
```
assert(int.parse('42') == 42);
assert(int.parse('0x42') == 66);
assert(double.parse('0.50') == 0.5);
```

hoặc có thể sử dụng function `parse()` của `num`. Function này sẽ ép thành kiểu `integer`, nếu không thì sẽ là kiểu `double`
```
assert(num.parse('42') is int);
assert(num.parse('0x42') is int);
assert(num.parse('0.50') is double);
```

Đặc biệt trong `integer`, nếu muốn chuyển hệ cơ số bạn thêm param `radix` như ví dụ dưới đây:
```
assert(int.parse('42', radix: 16) == 66);
```

Sử dụng function `toString()` để có thể ép kiểu `int` hoặc `double` thành `String`.
```
// Convert an int to a string.
assert(42.toString() == '42');

// Convert a double to a string.
assert(123.456.toString() == '123.456');
```

Sử dụng function `toStringAsFixed()` để làm tròn sau dấu `,`
```
// Specify the number of digits after the decimal.
assert(123.456.toStringAsFixed(2) == '123.46');
```

#### Strings and regular expressions

Class `Strings` cung cấp các function `split()`, `contain()`, `startsWith()`, `endWith()` và nhiều hơn thế nữa.

##### Searching inside a string

Bạn có thể tìm kiếm chuỗi theo ví dụ dưới đây
```
// Check whether a string contains another string.
assert('Never odd or even'.contains('odd'));

// Does a string start with another string?
assert('Never odd or even'.startsWith('Never'));

// Does a string end with another string?
assert('Never odd or even'.endsWith('even'));

// Find the location of a string inside a string.
assert('Never odd or even'.indexOf('odd') == 6);
```

##### Extracting data from a string

Sử dụng `split()` với chuỗi rỗng `''` để lấy được tất cả `characters` trong `String`
```
for (var char in 'hello'.split('')) {
  print(char); // h e l l o
}
```

Lấy `UTF-16` trong chuỗi bằng cách sử dụng `index` của nó (kết quả là `String`)
```
assert('Never odd or even'[0] == 'N');
```

hoặc lấy `UTF-16` theo mã ACSII
```
var codeUnitList =
    'Never odd or even'.codeUnits.toList();
assert(codeUnitList[0] == 78);
```

##### Converting to uppercase or lowercase


