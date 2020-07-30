# HTML Basic - HTML cơ bản

### HTML là gì?
HTML không phải là một ngôn ngữ lập trình, nó là một ngôn ngữ đánh dấu siêu văn bản (Hypertext Markup Language) định hình cấu trúc nội dung của bạn. HTML bao gồm một loạt elements, thứ bạn dùng để đính kèm, hoặc gói các phần khác nhau của nội dung để làm cho chúng xuất hiện hay hoạt động với một cách nhất định. Các tags kèm theo có thể làm một từ hay hình ảnh siêu liên kết từ nơi khác, có thể in nghiêng, làm cho phông chữ lớn hơn hoặc nhỏ hơn...

Chuẩn HTML được phát triển bởi W3C (World Wide Web Consortium) vào năm 1997. Trong HTML, tags được dùng để định nghĩa cấu trúc văn bản; tags, và elements được định nghĩa bằng ký tự < và >. Trong những ngày đầu tiên, tất cả nội dung và style tags được dồn vào một ngôn ngữ lớn, phức tạp. Qua thời gian, W3C quyết định tách nội dung và style của một trang web vì nghĩ nó cần thiết; việc này dẫn đến sự bắt đầu của style sheets. Ngày nay, tags được dùng để định nghĩa style của một văn bản (ví dụ: FONT) đã lỗi thời vì mọi người thích style sheets và chỉ còn có tag định nghĩa nội dung (ví dụ H1) là còn tồn tại như là một thành phần cốt lõi của HTML.

HTML được cập nhật nhiều qua thời gian, và hiện tại, chuẩn HTML mới nhất là HTML5 (được công bố năm 2014). HTML5 tất nhiên vẫn là ngôn ngữ markup chính, nhưng nó cung cấp thêm nhiều tính năng hơn HTML và đã xóa một số tính nghiêm ngặt thường thấy trong XHTML.

Cụ thể hơn, HTML5 đã bổ sung thêm rất nhiều các thẻ đánh dấu (markup) mới:
- Các thẻ `<header>` và `<footer>` giúp bạn tách các phần trên và dưới của các block nội dung. Để có thể sử dụng nhiều lần trên một trang duy nhất. 
- Thẻ `<article>` giúp xác định một phần cụ thể về nội dung, ví dụ, một bài blog hoặc một bình luận của độc giả.
- Thẻ `<nav>` để xác định những phần nào được coi là khối điều hướng.
- Thẻ `<section>` cho phép bạn xác định một phần nội dung nào đó; tương tự như các thẻ `<div>` hiện nay.
- Các thẻ `<audio>` và `<video>` để đánh dấu những nội dung bao gồm âm thanh hoặc video.
- Thẻ `<canvas>` cho phép bạn vẽ đồ họa sử dụng một ngôn ngữ kịch bản riêng biệt.
- Thẻ `<embed>` dùng để nhúng các nội dung hoặc các ứng dụng bên ngoài vào trang web.

*Trong các bài viết ở đây, mình sẽ sử dụng phiên bản HTML5 để giới thiệu đến mọi người!*

### Kết cấu của một trang HTML
```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My page</title>
  </head>
  <body>
    <p>HTML Basic</p>
  </body>
</html>
```
- `<!DOCTYPE html> ` khai báo xác định rằng tài liệu này là một tài liệu HTML5
- `<html></html>` đây là phần tử gốc của trang HTML
- `<head></head>` đây là phần tử chứa tất cả những nội dung bạn muốn đưa vào trang HTML không phải nội dung bạn hiển thị cho người xem trang của bạn. Điều này bao gồm những thứ như keywords và mô tả trang mà bạn muốn xuất hiện trong kết quả tìm kiếm, CSS tạo kiểu cho nội dung, khai báo bộ ký tụ và những thứ khác. 
- `<meta charset="utf-8">` thành phần này đặt tài liệu của bạn sử dụng ký tự ở định dạng UTF-8, hầu hết các ký tự phần lớn là các ngôn ngữ chữ viết của con người.
- `<title></title>` thành phần này đặt tiêu đề cho trang của bạn, là tiêu đề xuất hiện trong tab trình duyệt đang được tải.
- `<body></body>` thành phần này chứa tất cả nội dung mà bạn muốn hiển thị cho người dùng web khi họ truy cập trang của bạn, cho đó là văn bản, hình ảnh, video, trò chơi, bản âm thanh có thể phát hoặc bất kỳ nội dung nào khác.

#### 1. Thẻ
- Thẻ HTML là một trong các thành phần quan trọng , sử dụng để tạo ra phần tử nhất định trên trang web.
- Có 2 loại là thẻ đầy đủ và thẻ khuyết:
    - Thẻ đầy đủ bao gồm thẻ mở và thẻ đóng: `<p></p>, <h1></h1>`
    - Thẻ khuyết (hay thẻ tự đóng): `<br/>, <hr/>, <input/> `
    
#### 2. Thuộc tính của thẻ
- Mỗi thẻ HTML có thể được coi là một đối tượng, lúc này sẽ có các thuộc tính mô tả cho nó
- Ví dụ: `<input type="text" name="username" class="input-name" />` thẻ input bao gồm các thuộc tính như `type`, `name`, `class`...

#### 3. Các thẻ định dạng văn bản
Một số thẻ thông dụng:
- Thẻ `p`: phân đoạn văn, kết thúc cặp thẻ `p` văn bản sẽ tự động ngắt dòng.
- Thẻ `br`: văn bản sẽ ngắt dòng khi gặp thẻ `br`.
- Thẻ `b`: tạo chữ in đậm.
- Thẻ `strong`: nội dung được bôi đậm nhằm nhấn mạnh.
- Thẻ `i`: tạo chữ in nghiêng.
- Thẻ `u`: tạo chữ gạch chân.
- Thẻ `small`: tạo chữ nhỏ. 
- Thẻ `mark`: tạo hightline
- Thẻ `sub`: tạo chữ nhỏ nằm dưới so với đoạn văn.
- Thẻ `sup`: tạo chữ nhỏ nằm trên so với đoạn văn.

#### 4. Thẻ định dạng Heading và list
- Thẻ định dạng Heading: bao gồm các cặp thẻ từ `h1` đến `h6`, dùng để tạo tiêu đề chính và tiêu đề phụ cho trang web, rất có lợi cho việc SEO.
    ```
    <h1>Tiêu đề h1</h1>
    <h2>Tiêu đề h2</h2>
    <h3>Tiêu đề h3</h3>
    <h4>Tiêu đề h4</h4>
    <h5>Tiêu đề h5</h5>
    <h6>Tiêu đề h6</h6>
    ```
    Hiển thị:
    <h1>Tiêu đề h1</h1>
    <h2>Tiêu đề h2</h2>
    <h3>Tiêu đề h3</h3>
    <h4>Tiêu đề h4</h4>
    <h5>Tiêu đề h5</h5>
    <h6>Tiêu đề h6</h6>
    
- Thẻ định dạng list: dùng để tạo một nhóm danh sách liên quan.
    ```
    <ul>
         <li>item1</li>
         <li>item2</li>
         <li>item3</li>
     </ul>
     ```
    Hiển thị: 
    <ul>
        <li>item1</li>
        <li>item2</li>
        <li>item3</li>
    </ul>

#### 5. Thẻ định dạng bảng
- Mỗi bảng sẽ gồm 2 thành phần là cột và hàng, và được tạo bởi các thẻ `table`, `tr`, `td`, `thead`, `tbody`, `tfood`, `th`.
```
<table border="1" cellspacing="0" cellpadding="5">
    <tr>
        <td colspan="2">Hàng 1 cột 1 và Hàng 1 cột 2</td>
        <td>Hàng 1 cột 3</td>
    </tr>
    <tr>
        <td>Hàng 2 cột 1</td>
        <td>Hàng 2 cột 2</td>
        <td>Hàng 2 cột 3</td>
    </tr>
</table>
```
- Thuộc tính border="1" là khai báo đường viền của table.
- Thuộc tính cellspacing="0" là khai báo khoảng cách giữa viền trên và viền dưới của đường viền.
- Thuộc tính cellpadding="5" là khai báo khoảng cách giữa nội dung trong ô so với đường viền.
- Nếu muốn thêm một cột thì bổ sung một td.
- Nếu muốn thêm một hàng thì bổ sung một tr.
- Thuộc tính `colspan` và `rowspan`:
    - `colspan="số_lượng"`: dùng để gộp 2 hay nhiều ô lại với nhau.
    - `rowspan="số_lượng"`: dùng để gộp 2 hay nhiều dòng lại với nhau.
    
#### 6. Thẻ liên kết
- Trong một trang web luôn tồn tại các link liên kết với nhau , giúp liên kết trang web hiện taị đến một trang web khác hoặc liên kết các vị trí trên cùng một trang web với nhau.
- Liên kết trang này đến trang khác: 

  `<a href="facebook.com" target="_blank" rel="follow">Facebook</a>`
  - `href` là đường link đến địa chi website đích
  - `rel` là các giá trị dành cho SEO
  - `target` là các tùy chọn, nếu nó có giá trị (giá trị mặc định là _self):
    - `_blank` thì nó sẽ chuyên link trên tab mới
    - `_self` thì nó sẽ chuyển link trên tab hiện tại
    - `_parent` thì nó sẽ chuyển link tới tab mở tab hiện tại. Ta còn hay gọi là tab cha của tab hiện tại
    - `_top` thì nó sẽ nhảy tới tab hiện tại và thường dùng trong iframe khi muốn thoát khỏi iframe và chạy tới trang gốc luôn.
- Liên kết vị trí này đến vị trí khác: Với cú pháp `href="#id_name"` để khi người dùng click vào thì nó sẽ nhảy tới vị trí của thẻ HTML có `id="id_name"` trong trang hiện tại.

Ví dụ: `<a href="#more">Xem thêm</a>`

Và tại ví trí hiển thị nội dung: `<div id="more">Chi tiết sản phẩm</div>`

#### 7. Tạo hình ảnh
- Sử dụng thẻ `img` để hiển thị hình ảnh với cú pháp sau:
    `<img src="đường_dẫn_file_ảnh" alt="mô_tả" />`
- Một số thuộc tính của thẻ `img`:
    - `src`: chứa đường dẫn trỏ đến hình ảnh.
    - `alt`: thuộc tính sẽ hiển thị nội dung khi việc hiển thị ảnh gặp sự cố (ví dụ: truyền đường dẫn sai, không hiển thị ảnh do gặp vấn đề kết nối internet,...)
    - `width`, `height`: thiết lập chiều rộng, chiều cao cho hình ảnh.
