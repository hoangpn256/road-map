# Conventions and Best Practices

Cho dù bạn là người mối bắt đầu hay là một chuyên gia về HTML, điều quan trong nhất là phải tuân theo một số thực tiễn tốt nhất để giữ cho trang của bạn nhất quán và có tổ chức. Với rất nhiều yếu tố như phần tử, thuộc tính, giá trị,... và nhiều hơn thế nữa.

Dưới đây là một số cách thực hành tốt nhất về HTML cần nhớ khi thực hiện dự án của bạn.

#### 1. Sử dụng cấu trúc tài liệu phù hợp

Các trang web vẫn sẽ hoạt động nếu không có các phần tử như `<!DOCTYPE html>`, `<html>`, `<head>`, `<body>`. Tuy nhiên các trang sẽ không được hiển thị đúng với mọi trình , vì vậy điều quan trọng là phải sử dụng cấu trúc tài liệu phù hợp.
```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My page</title>
  </head>
  <body>
    ....
  </body>
</html>
``` 
Việc sử dụng đầy đủ các phần tử trên giữ cho các trang tuân thủ các tiêu chuẩn và đầy đủ ngữ nghĩa (semantic) cũng như đảm bảo các trang hiển thị tốt nhất trên tất cả các trình duyệt.

#### 2. Sử dụng thẻ `<title>`
Thẻ `<title>` giúp làm cho một trang web có ý nghĩa hơn và thân thiện với công cụ tìm kiếm. 

Ví dụ: nội dung bên trong thẻ `<title>` sẽ xuất hiện trong trang kết quả của công cụ tìm kiếm Google, cũng như trong thanh và tab trình duyệt web của người dùng.

#### 3. Sử dụng thẻ `<meta>`
- Thẻ `<meta>` thường được sử dụng để chỉ định bộ ký tự, mô tả trang, từ khóa, tác giả của tài liệu và cài đặt chế độ xem.
- Thẻ `<meta>` mô tả mô tả mục đích cơ bản trang web của bạn (tóm tắt về những gì trang web chứa). Đối với mỗi trang web, bạn nên đặt một bản tóm tắt có liên quan bên trong thẻ mô tả `<meta>`.
- Ví dụ:
    - `<meta charset="UTF-8">`: Xác định bộ ký tự được sử dụng.
    - `<meta name="keywords" content="HTML, CSS, JavaScript">`: Xác định từ khóa cho công cụ tìm kiếm.
    - `<meta name="description" content="Free Web tutorials">`: Xác định một mô tả của trang web của bạn.
    - `<meta name="author" content="John Doe">`: Xác định tác giả của trang.
    - `<meta http-equiv="refresh" content="30">`: Làm mới tài liệu sau 30 giây.
    - `<meta name="viewport" content="width=device-width, initial-scale=1.0">`: Cài đặt chế độ xem phù hợp trên tất cả các trình duyệt.

#### 4. Tuân thủ đúng các nguyên tắc Semantic cho trang của bạn.
- Xem xét việc chia trang web của bạn thành các phần chính là bước đầu tiên trong việc xây dựng một thiết kế trang web.
- Thư viện các phần tử trong HTML khá lớn, với hơn 100 phần tử có sẵn để sử dụng. Quyết định những yếu tố nào được sử dụng để mô tả nội dung khác nhau có thể khó khăn, nhưng những yếu tố này là xương sống của ngữ nghĩa (Semantic). Chúng ta cần nghiên cứu và kiểm tra kỹ mã của mình để đảm bảo chúng ta đang sử dụng các yếu tố ngữ nghĩa phù hợp.

*Đừng dùng thẻ `<div>` ở mọi nơi*

- Theo dự thảo mới nhất về đặc tả HTML của W3C, `<div>` là một yếu tố vô nghĩa nên được sử dụng là một giải pháp cuối cùng, vì khi không có yếu tố nào khác phù hợp.
- Từ phiên bản HTML5 đã cho ra đời một số thẻ như `<section>`, `<main>`,... giúp các thành phần trong trang của bạn trở nên có nghĩa hơn.

Bạn có thể tham khảo thêm [tại đây](html_semantic.md)

#### 5. Sử dụng các thẻ tiêu đề một cách khôn khéo
- Các tiêu đề HTML được xác định bằng các thẻ `<h1>` đến `<h6>`.
- Các công cụ tìm kiếm sử dụng các tiêu đề để lập chỉ mục cấu trúc và nội dung của các trang web của bạn. Người dùng thường lướt qua một trang bởi các tiêu đề của nó. Điều quan trọng là sử dụng các tiêu đề để hiển thị cấu trúc tài liệu. Các tiêu đề `<h1>` nên được sử dụng cho các tiêu đề chính, tiếp theo là các tiêu đề `<h2>`, sau đó các tiêu đề `<h3>` ít quan trọng hơn, v.v.
- Chỉ sử dụng các thẻ tiêu đề HTML cho các tiêu đề của trang. Đừng sử dụng chúng để làm cho văn bản **LỚN** hoặc **in đậm**.

#### 6. Hãy mở và đóng thẻ đúng cách
- Trong một số trường hợp, việc bạn không đóng thẻ hay đóng thẻ sai thứ tự sẽ không làm ảnh hưởng đến trang web, nhưng nó sẽ không đảm bảo mọi trình duyệt có thể hiển thị như mong muốn. Vì thế, hãy mở và đóng thẻ theo đúng tiêu chuẩn.
- Ví dụ:
    ```
    <p>Hello World! <span>This is my page</p></span> 
    ```
Oh no!!! Đừng làm như vậy, hãy coi việc lồng thẻ như những chiếc hộp vậy, hộp ở trong sẽ được đóng trước hộp bên ngoài.

    <p>Hello World! <span>This is my page</span></p>
    
#### 7. Hãy dùng định dạng chữ thường cho tên thẻ của bạn
Mặc dù HTML không phân biệt chữ hoa chữ thường, nhưng nếu một trang HTML lộn xộn giữa các thẻ chữ hoa và chữ thường thì chắc chắn sẽ gây khó chịu cho người khác khi đọc code của bạn.

#### 8. Sử dụng thuộc tính `alt` với hình ảnh
Không bắt buộc phải có thuộc tính `alt` cho hình ảnh, nhưng nó sẽ giúp ích cho trang web của bạn khi gặp sự cố (ví dụ như đặt sai đường dẫn, sự cố về internet khiến không thể hiển thị hình ảnh,...). Mặt khác nó còn cung cấp ngữ caảnh cho trình đọc màn hình. Do đó, nội dung của thuộc tính `alt` là mô tả những gì hình ảnh chứa.

#### 9. Hãy dùng `<label>` cho các ô `<input>` của bạn
Bạn hoàn toàn có thể tạo ra nhãn gắn cho các trường nhập bằng nhiều cách khác nhau. Nhưng hãy dùng thẻ `<label>` vì nó có thể tạo ra liên kết đến các trường (khi click vào nhãn, con trỏ sẽ được focus vào phần tử liên kết với nó). 
```
<form>
    <label for="username">Name</label>
    <input type="text" id="username"/>
    <input type="radio" id="male" name="gender" value="male">
    <label for="male">Male</label><br>
    <input type="radio" id="female" name="gender" value="female">
    <label for="female">Female</label><br>
</fom>
```
Điều này sẽ làm cho biểu mẫu của bạn dễ sử dụng hơn đối với người dùng và cải thiện chất lượng mã của bạn.

#### 10. Tách biệt CSS ra khỏi trang HTML của bạn
- HTML là phần nội dung, CSS cung cấp các kiểu trình bày, vì thế đừng để lẫn chúng với nhau.
- Không sử dụng các kiểu `inline style` trong HTML. Làm như vậy sẽ tạo ra các trang mất nhiều thời gian hơn để tải, khó bảo trì. Thay vào đó, sử dụng kiểu `external style`, sử dụng các `class` hoặc `id` để nhắm mục tiêu các phần tử và áp dụng các kiểu nếu cần.
