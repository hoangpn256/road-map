## Table of Contents - Cấu trúc **node**

[1. Foreword - Mở đầu ](#head1)

[2. What is Ajax? - Ajax là gì ?](#head2)

[3. Basic Ajax request - Một số Ajax request cơ bản](#head3)

[4. Conclusion - Kết luận](#head4)

<a name='head1' />

### **1. Foreword - Mở đầu**

Vấn đề

Nhưng chúng ta đều biết, để có được trang web hiển thị trên trình duyệt, bạn chỉ đơn giản là gõ url -> enter, điều này thực chất là bạn đang `gửi 1 request lên server`, và nếu mọi việc `OK` thì trang web của bạn được hiển thị lên trình duyệt.

<img src="./images/basic-request.png">

Vấn đề xảy ra ở đây khi bạn muốn update chỉ 1 phần nào đó của trang web, ví dụ như để hiển thị sản phẩm mới, ... thì bắt buộc bạn phải tải lại toàn bộ cả trang web. Điều này khiến cho chúng ta có 1 số vấn đề sau đây
- Cực kì lãng phí tài nguyên, thay vì load 1 phẩn nhỏ của trang web, mà bạn phải load lại toàn bộ cả trang
- Gây ra cảm giác website của bạn chậmmmm, dẫn đến trải nghiệm người dùng sẽ giảm đi rất nhiều
- Hãy thử tưởng tượng trang web của bạn lớn, thì việc load trang sẽ `bị delay` 1 khoảng thời gian khá lớn.
- Trong thời điểm hiện tại, thì website còn dành cho phần lớn người dùng moblie nữa, vậy thì ôi thôi rồi, tốc độ load trang sẽ càng tăng hơn nữa.

Vậy đâu là giải pháp. Chúng ta hãy cùng đi tiếp sang phần sau nhé.


<a name='head2' />

### **2. What is Ajax? - Ajax là gì ?**

Tiếp theo phần đầu, để giải quyết vấn đề trên chúng ta cần giải pháp cho phép trang web `request` để lấy các `response` nhỏ(như HTML, CSS, `JSON`, hoặc thậm chí là plain text) và hiển thị chúng khi cần thiết.

Các công nghệ có thể kể đến như `XMLHttpRequest` hoặc gần đây chúng ta hay sử dụng nhất như `Fetch API`.

Các công nghệ này cho phép các trang web trực tiếp xử lý các yêu cầu `HTTP` đối với các `tài nguyên - resources` cụ thể có sẵn trên `máy chủ - server` và định dạng dữ liệu kết quả khi cần trước khi nó được hiển thị.

Chúng ta gọi chung chúng là `AJAX - Asynchronous JavaScript and XML`

- Lưu ý: AJAX - Vì ban đầu nó sử dụng `XMLHttpRequest` để `yêu cầu` dữ liệu dạng `XML`, khác phần lớn cách sử dụng hiện này - là `yêu cầu dữ liệu dạng JSON`, nhưng mục đích chung thì không thay đổi. Vậy nên, cho đến tận giờ chúng ta vẫn sử dụng thuật ngữ `AJAX` để mô tả kỹ thuật trên.

Để hiểu cơ bản về cách hoạt động của AJAX, hãy xem hình vẽ dưới đây

<img src="./images/ajax.png">

`AJAX model` liên quan đến việc sử dụng `API` Web làm` proxy - cổng` để `request data(dữ liệu)` 1 cách tốt hơn, thông minh hơn thay vì để trình duyệt load lại toàn bộ trang.

- Lưu ý: Trong thực tế, chúng ta còn rất nhiều kiến trúc khác sử dụng AJAX để tăng tốc độ load trang, nhưng về cơ bản, các bạn có thể hiểu như vậy. Các bạn có thể google để tìm hiểu rõ hơn về phần này nếu muốn nhé.

<a name='head3' />

### **3. Basic Ajax request - Một số Ajax request cơ bản**

Chúng ta cùng tìm hiểu 2 cách tạo request cơ bản là `XMLHttpRequest` và `Fetch API`

**`XMLHttpRequest`**

Cùng tham khảo 1 ví dụ từ trang [MDN](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/Using_XMLHttpRequest) nhé

```js
function reqListener() {  
  var data = JSON.parse(this.responseText);  
  console.log(data);  
}

function reqError(err) {  
  console.log('Fetch Error :-S', err);  
}

var oReq = new XMLHttpRequest();  
oReq.onload = reqListener;  
oReq.onerror = reqError;  
oReq.open('get', './api/some.json', true);  
oReq.send();
```
Các bạn có thể thấy là object này yêu cầu `2 hàm chính`, đó là hàm `open()` để tạo ra kết nối và `send()` để gửi request đi, thêm vào đó chúng ta có `2 hàm định nghĩa listener` cho trường hợp `thành công và lỗi`.

Có thể thấy là ví dụ khá là phức tạp, và có kèm `2 callback`.

- Lưu ý: Ở thời điểm hiện tại, thì gần như chúng ta không còn sử dụng phương pháp này nữa.

**`Fetch`**

- Về cơ bản, `fetch` là bản nâng cấp của `XMLHttpRequest`, cách này sẽ giúp JS tạo các `bất đồng bộ HTTP request` dễ dàng hơn, cho cả 2 phía là các lập trình viên, và các APIs được xây dựng.

Cùng 1 ví dụ bên trên, chúng ta có thể viết lại bằng cách dùng `fetch` như sau

```js
fetch('./api/some.json')  
  .then(  
    function(response) {  
      if (response.status !== 200) {  
        console.log('Looks like there was a problem. Status Code: ' +  
          response.status);  
        return;  
      }

      // Examine the text in the response  
      response.json().then(function(data) {  
        console.log(data);  
      });  
    }  
  )  
  .catch(function(err) {  
    console.log('Fetch Error :-S', err);  
  });
```
Nhìn qua 1 lượt thì chúng ta có thể thấy sự xuất hiện của `then()` và `catch()` ở đây, ồ chính nó là `promise` - một khái niệm mà hiện giờ các bạn đã gặp rất nhiều, điển hình của nó là `async/await`, mình sẽ không đi sâu ở bài viết này, hãy google để thêm thông tin nhé.

So với việc dùng `XMLHttpRequest` thì `fetch` thưc sự dễ hơn rất rất nhiều.

Chúng ta sẽ đi sâu hơn về `response` một chút cùng với `fetch` nhé.

**_`Response`_**

Với ví dụ ở trên, `response` là một `Response object` được trả về, chúng ta có thể truy xuất rất nhiều `metadata` dê dàng từ object này, vd ở trên chúng ta truy xuất status, rồi sau đó chúng ta `trả về JSON`.

Xin lưu ý là `object response` này cũng là một `Stream object`(hãy google nếu chưa hiểu khái niệm này nhé) và chúng ta có thể tiếp tục gọi `json() `(shortcut của `JSON.parse(jsonString)`) lên stream này và in JSON ra màn hình.

Thế mới thấy là `object` này rất là nhiều ưu điểm và đươc thiết kế để tận dụng các `kỹ thuật lập trình JS mới`. Không dừng ở đó, mình rất mong muốn các bạn tham khảo các API khác như 

```js
response.statusText
response.type
response.url
response.headers
```
Thậm chí có thể truy cập header của `response` như
```js
response.headers.get('header-name')
```
- Lưu ý: Hãy tìm hiểu thêm về `Response Type` nhé, vì xung quanh nó có khá nhiều khái niệm quan trọng cần nắm vững.

**Chỉ định các `HTTP method`**

Mặc định của `fetch` là `GET`, nhưng chúng ta có thể thay đổi nó như
```js
fetch(url, {  
    method: 'post',  
...
}
```
bên cạnh đó, chúng ta cũng có thể set các `header` như
```js
fetch(url, {
    headers: {  
      "Content-type": "application/x-www-form-urlencoded; charset=UTF-8"  
    },
    ...
}
```
hoặc có thể gửi dữ liệu kèm theo ajax như
```js
fetch(url, {
    body: JSON.stringify({
        email: document.getElementById('email').value
        answer: document.getElementById('answer').value
    })
```

- Lưu ý: Đến thời điểm hiện tại thì `fetch` đã được hầu hết các trình duyệt lớn hỗ trợ. Hiện tại thì cả `Window và ServiceWorker` đều cho phép sử dụng `fetch`. Nhưng nếu chẳng may do quá đen, trình duyệt không hỗ trợ, nhưng bạn vẫn muốn dùng `fetch` thì hãy sử dụng `polyfill fetch` để chuyển đổi code tương thích nhé.


<a name='head4' />

### **4. Conclusion - Kết luận**

Một số khái niệm cần nắm vững như
- AJAX
- XMLHttpRequest
- Fetch

Một số lưu ý
- `Fetch` là bản nâng cấp của `XMLHttpRequest`
- `Fetch` được thiết kế theo kiểu `Promise`
- `Fetch` cung cấp `Request, Response, Body và Status` dưới dạng object.
- Gần như hầu hết các trình duyệt đều đã hỗ trợ `fetch`
- Cần tìm hiểu thêm khái niệm về `Promise` và các vấn đề xoay quanh nó


******
Copyright © **[@hoangpn](https://hoangpn.com)**, member of **Hituno Team**, 2020