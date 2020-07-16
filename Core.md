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

```
// Convert to uppercase.
assert('structured web apps'.toUpperCase() ==
    'STRUCTURED WEB APPS');

// Convert to lowercase.
assert('STRUCTURED WEB APPS'.toLowerCase() ==
    'structured web apps');
```

##### Trimming and empty strings

Xóa tất cả trước và sau chuỗi sử dụng `trim()` function, còn muốn kiểm trả chuỗi có rỗng (độ dài duỗi = 0) thì sử dụng `isEmpty()`
```
// Trim a string.
assert('  hello  '.trim() == 'hello');

// Check whether a string is empty.
assert(''.isEmpty);

// Strings with only white space are not empty.
assert('  '.isNotEmpty);
```

##### Replacing part of a string

`Strings` là objects không thể thay đổi giá trị, điều đó có nghĩa là chỉ có thể tạo mà không thay đổi được giá trị của nó.
Ví dụ, function `replaceAll()` trả về `String` mới mà không thay đổi `String` gốc
```
var greetingTemplate = 'Hello, NAME!';
var greeting =
    greetingTemplate.replaceAll(RegExp('NAME'), 'Bob');

// greetingTemplate didn't change.
assert(greeting != greetingTemplate);
```

##### Building a string

Để sinh ra `String`, ta có thể sử dụng `StringBuffer` class. Class `StringBuffer` không tự động sinh ra `String` cho đến khi gọi hàm `toString()`.
```
var sb = StringBuffer();
sb
  ..write('Use a StringBuffer for ')
  ..writeAll(['efficient', 'string', 'creation'], ' ')
  ..write('.');

var fullString = sb.toString();

assert(fullString ==
    'Use a StringBuffer for efficient string creation.');
```

hàm `writeAll()` có param thứ 2 ý nghĩa rằng sẽ thêm giá trị tương ứng trong chuỗi của param 1

##### Regular expressions

Sử dụng `RexExp` để tìm kiếm chuỗi đúng theo parttern.
```
// Here's a regular expression for one or more digits.
var numbers = RegExp(r'\d+');

var allCharacters = 'llamas live fifteen to twenty years';
var someDigits = 'llamas live 15 to 20 years';

// contains() can use a regular expression.
assert(!allCharacters.contains(numbers));
assert(someDigits.contains(numbers));

// Replace every match with another string.
var exedOut = someDigits.replaceAll(numbers, 'XX');
assert(exedOut == 'llamas live XX to XX years');
```

```
var numbers = RegExp(r'\d+');
var someDigits = 'llamas live 15 to 20 years';

// Check whether the reg exp has a match in a string.
assert(numbers.hasMatch(someDigits));

// Loop through all matches.
for (var match in numbers.allMatches(someDigits)) {
  print(match.group(0)); // 15, then 20
}
```


#### Collections

Collection trong Dart bao gồm các class `lists`, `sets` và `maps`

##### Lists

Dưới đây là ví dụ về `List`
```
// Use a List constructor.
var vegetables = List();

// Or simply use a list literal.
var fruits = ['apples', 'oranges'];

// Add to a list.
fruits.add('kiwis');

// Add multiple items to a list.
fruits.addAll(['grapes', 'bananas']);

// Get the list length.
assert(fruits.length == 5);

// Remove a single item.
var appleIndex = fruits.indexOf('apples');
fruits.removeAt(appleIndex);
assert(fruits.length == 4);

// Remove all elements from a list.
fruits.clear();
assert(fruits.isEmpty);
```

Sử dụng function `indexOf` để tìm index của object tương ứng

```
var fruits = ['apples', 'oranges'];

// Access a list item by index.
assert(fruits[0] == 'apples');

// Find an item in a list.
assert(fruits.indexOf('apples') == 0);
```

Để sắp xếp trong `List`, ta dùng funtion `sort()`
```
var fruits = ['bananas', 'apples', 'oranges'];

// Sort a list.
fruits.sort((a, b) => a.compareTo(b));
assert(fruits[0] == 'apples');
```

Ta có thể ép kiểu trong `List`
```
// This list should contain only strings.
var fruits = List<String>();

fruits.add('apples');
var fruit = fruits[0];
assert(fruit is String);

fruits.add(5); // Error: 'int' can't be assigned to 'String'
```

##### Sets

`Set` trong `Dart` là `Unique Collections` không sắp xếp theo thứ tự. Bởi vì `Set` sắp xếp không theo thứ tự nên ta không thể lấy(get) hoặc cập nhật giá trị (get) theo index
```
var ingredients = Set();
ingredients.addAll(['gold', 'titanium', 'xenon']);
assert(ingredients.length == 3);

// Adding a duplicate item has no effect.
ingredients.add('gold');
assert(ingredients.length == 3);

// Remove an item from a set.
ingredients.remove('gold');
assert(ingredients.length == 2);
```

Sử dụng `contains()` hoặc `containsALl()` để kiểm tra xem `Set` có chưa object tương ứng hay không
```
var ingredients = Set();
ingredients.addAll(['gold', 'titanium', 'xenon']);

// Check whether an item is in the set.
assert(ingredients.contains('titanium'));

// Check whether all the items are in the set.
assert(ingredients.containsAll(['titanium', 'xenon']));
```

Ngoài ra Dart còn cung cấp rất nhiều function của `Set` khác [tại đây](https://api.dart.dev/stable/2.8.4/dart-core/Set-class.html)

##### Map

`Map` được hiểu như là `dictionary` hoặc `has`, là một `Collections` không được sắp xếp theo thứ tự với các cặp `key-value` tương ứng.
```
// Maps often use strings as keys.
var hawaiianBeaches = {
  'Oahu': ['Waikiki', 'Kailua', 'Waimanalo'],
  'Big Island': ['Wailea Bay', 'Pololu Beach'],
  'Kauai': ['Hanalei', 'Poipu']
};

// Maps can be built from a constructor.
var searchTerms = Map();

// Maps are parameterized types; you can specify what
// types the key and value should be.
var nobleGases = Map<int, String>();
```

Bạn có thể thêm, lấy, và cập nhật giá trị của map bằng cách sử dụng `{}`
```
var nobleGases = {54: 'xenon'};

// Retrieve a value with a key.
assert(nobleGases[54] == 'xenon');

// Check whether a map contains a key.
assert(nobleGases.containsKey(54));
```

Để xóa key và value của map, sử dụng function `remove()`
```
// Remove a key and its value.
nobleGases.remove(54);
assert(!nobleGases.containsKey(54));
```

Ví dụ dưới đây là cách lấy tất cả `key` hoặc `value` của Map
```
var hawaiianBeaches = {
  'Oahu': ['Waikiki', 'Kailua', 'Waimanalo'],
  'Big Island': ['Wailea Bay', 'Pololu Beach'],
  'Kauai': ['Hanalei', 'Poipu']
};

// Get all the keys as an unordered collection
// (an Iterable).
var keys = hawaiianBeaches.keys;

assert(keys.length == 3);
assert(Set.from(keys).contains('Oahu'));

// Get all the values as an unordered collection
// (an Iterable of Lists).
var values = hawaiianBeaches.values;
assert(values.length == 3);
assert(values.any((v) => v.contains('Waikiki')));
```

Danh sách các function Dart hỗ trợ `Map` [tại đây](https://api.dart.dev/stable/2.8.4/dart-core/Map-class.html)

##### Common collection methods

Sử dụng `isEmpty()` hoặc `isNotEmpty()` để kiểm tra sự tồn tại của `List`, `Sets` hoặc `Map` có chưa item nào không
```
var coffees = [];
var teas = ['green', 'black', 'chamomile', 'earl grey'];
assert(coffees.isEmpty);
assert(teas.isNotEmpty);
```

Sử dụng `forEach()` để lấy từng phần tử trong `List`, `Set`
```
var teas = ['green', 'black', 'chamomile', 'earl grey'];

teas.forEach((tea) => print('I drink $tea'));
```

Đối với `Map`, khi sử dụng `forEach` sẽ trả về 2 giá trị là `key` và `value`
```
hawaiianBeaches.forEach((k, v) {
  print('I want to visit $k and swim at $v');
  // I want to visit Oahu and swim at
  // [Waikiki, Kailua, Waimanalo], etc.
});
```

Ngoài các cách trên, Dart cũng cung cấp Iterables gọi là `map()`, giúp ngắn gọn code hơn
```
var teas = ['green', 'black', 'chamomile', 'earl grey'];

var loudTeas = teas.map((tea) => tea.toUpperCase());
loudTeas.forEach(print);
```

Sử dụng `where()` để lấy tất cả các items thỏa mãn điều kiện
```
var teas = ['green', 'black', 'chamomile', 'earl grey'];

// Chamomile is not caffeinated.
bool isDecaffeinated(String teaName) =>
    teaName == 'chamomile';

// Use where() to find only the items that return true
// from the provided function.
var decaffeinatedTeas =
    teas.where((tea) => isDecaffeinated(tea));
// or teas.where(isDecaffeinated)
```
Sử dụng `any()` và `every()` để kiểm tra 1 hoặc nhiều items thỏa mãn điều kiện
```
// Use any() to check whether at least one item in the
// collection satisfies a condition.
assert(teas.any(isDecaffeinated));

// Use every() to check whether all the items in a
// collection satisfy a condition.
assert(!teas.every(isDecaffeinated));
```

# Asynchronous programming

Trong kĩ thuật `Asynchronous`, thường chúng ta sử dụng `callback` function, nhưng đối với Dart cung cấp 2 khái niệm là `Future` và `Stream` object.
`Future` giống với `Promise` trong JS, còn `Stream` là cách để nhận dữ liệu tuần tự, giống như `events`.


**Note**
>  Bạn không phải lúc nào cũng sử dụng `Future` hay `Stream`. Dart hỗ trợ asynchronous bằng cách sử dụng `async` và `await`.

#### Future

`Future` thường sử dụng trong asynchronous. Khi một future *hoàn thanh*, giá trị của nó đã sẵn sàng để sử dụng.
Áp dụng trong các bài toán 

*  Call api lấy data từ server
*  Đọc/ghi dữ liệu vào Database
*  Đọc/ghi dữ liệu vào File

Có 2 trạng thái khi sử dụng `Future`, đó là `Uncompleted` và `Completed`

#### Uncompleted

Trong khi gọi asynchronous function, `Future` sẽ trả về `uncompleted` future. Future này sẽ đợi đến khi thực thi xong quá trình bất đồng bộ, sau đó sẽ trả về success hoặc trả về exception

#### Completed

Sau khi thực thi xong quá trình bất đồng bộ, future thành công sẽ trả về giá trị, còn không sẽ bắn về lỗi

##### Completing with a value

Một future thuộc `Future<T>` sau khi thực thi xong sẽ trả về giá trị `T`. Ví dụ một future loại `Future<String>` sau khi thực thi xong sẽ trả về `String`.
Nếu một future không trả về giá trị, ta khai báo `Future<Void>`

##### Completing with an error

Nếu trong quá trình thực thi bất đồng bộ có lỗi vì 1 lý do bất kỳ, future sẽ ném về ngoại lệ.

##### Using await

Trước khi tìm hiểu về `Future`, bạn cần hiêu về `await` trước.
Code sử dụng `await` dễ hiểu hơn sử dụng `Future`.

* Để khai báo async function, thêm `async` trước body của function đó.
* Keyword `await` chỉ sử dụng được trong async function.

Cách khai báo
```
void main() async { ··· }
```

Nếu function của bạn cần trả về kết quả, thì sẽ được viết như dưới đây
```
Future<String> createOrderMessage() async {
  var order = await fetchUserOrder();
  return 'Your order is: $order';
}

Future<String> fetchUserOrder() =>
    // Imagine that this function is
    // more complex and slow.
    Future.delayed(
      Duration(seconds: 2),
      () => 'Large Latte',
    );

Future<void> main() async {
  print('Fetching user order...');
  print(`await` createOrderMessage());
  print("...End fetching");
}
```

##### Execution flow with async and await

`async` function thực đồng bộ cho đến khi gặp từ khóa `await` đầu tiên.

Theo ví dụ dưới đây, `Future` sử dụng `then()` để thực hiện 3 asynchronous trong 1 dòng lệnh, đợi từng lệnh một thực hiện xong trước khi chuyển qua lệnh mới.
```
runUsingFuture() {
  // ...
  findEntryPoint().then((entryPoint) {
    return runExecutable(entryPoint, args);
  }).then(flushThenExit);
}
```

Nếu sử dụng `await` với đoạn code trên ta sẽ có ví dụ như dưới
```
runUsingAsyncAwait() async {
  // ...
  var entryPoint = await findEntryPoint();
  var exitCode = await runExecutable(entryPoint, args);
  await flushThenExit(exitCode);
}
```

`async` function có thể bắt ngoại lệ của `Future`, xem ví dụ dưới đây
```
var entryPoint = await findEntryPoint();
try {
  var exitCode = await runExecutable(entryPoint, args);
  await flushThenExit(exitCode);
} catch (e) {
  // Handle the error...
}
```

###### Basic usage

Bạn có thể sử dụng `then()` để thực thi code khi future hoành thành.
Ví dụ, `HttpRequest.getString()` trả về future, sử dụng `then()` để trả về giá trị `String`
```
HttpRequest.getString(url).then((String result) {
  print(result);
});
```

Dùng `catchError()` để bắt exception
```
HttpRequest.getString(url).then((String result) {
  print(result);
}).catchError((e) {
  // Handle or ignore the error.
});
```

**Note**
> `then().catchError()` là pattern asynchronous của `try-catch`


##### Chaining multiple asynchronous methods

`then()` được sử dụng trong multiple asynchoronous. Ví dụ
```
Future result = costlyQuery(url);
result
    .then((value) => expensiveWork(value))
    .then((_) => lengthyComputation())
    .then((_) => print('Done!'))
    .catchError((exception) {
  /* Handle exception... */
});
```

Chuyển ví dụ trên qua `await` ta được
```
try {
  final value = await costlyQuery(url);
  await expensiveWork(value);
  await lengthyComputation();
  print('Done!');
} catch (e) {
  /* Handle exception... */
}
```

##### Waiting for multiple futures

Dưới đây là ví dụ về cách đợi multiple futures
```
Future deleteLotsOfFiles() async =>  ...
Future copyLotsOfFiles() async =>  ...
Future checksumLotsOfOtherFiles() async =>  ...

await Future.wait([
  deleteLotsOfFiles(),
  copyLotsOfFiles(),
  checksumLotsOfOtherFiles(),
]);
print('Done with all the long steps!');
```
# I/O for servers and command-line apps
