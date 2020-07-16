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

