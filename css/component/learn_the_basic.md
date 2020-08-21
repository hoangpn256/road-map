[Home](../index.md) / Learn the basic

## CSS căn bản - Learn the basic

#### 1. CSS thật sự là gì?

Giống như HTML, CSS không phải là một ngôn ngữ lập trình, cũng không phải một ngôn ngữ đánh dấu, nó là ngôn ngữ định kiểu. Điều này có nghĩa là nó cho phép bạn áp dụng kiểu có chọn lọc cho các phần tử trong tài liệu HTML.

Ví dụ để để chọn tất cả các phần tử `đoạn văn` trên trang HTML và chuyển màu chữ thành màu đỏ, bạn sẽ viết CSS như thế này:
```
p {
    color: red;
}
```
Nhưng chúng ta cần nhúng CSS vào file HTML của bạn. Nếu không, các định dang CSS sẽ không ảnh hưởng đến việc hiển thị file HTML lên trình duyệt.  

Có 3 cách để nhúng CSS vào file HTML:
- External CSS
- Internal CSS
- Inline CSS

##### *External CSS*
- Bảng định kiểu được viết bên ngoài file HTML, đươc lưu bằng phần mở rộng `.css`. 
- Với bảng định kiểu bên ngoài, bạn có thể thay đổi giao diện của toàn bộ trang web chỉ bằng cách thay đổi trên một tệp. 
- Mỗi trang HTML phải bao gồm một tham chiếu đến tệp CSS bên trong thẻ `<link>`, được đặt trong `<head>`.
```
<!DOCTYPE html>
<html>
<head>
<link rel="stylesheet" type="text/css" href="mystyle.css">
</head>
<body>

<h1>This is a heading</h1>
<p>This is a paragraph.</p>

</body>
</html>
```

##### *Internal CSS*
- Bảng định kiểu được viết ngay tại file HTML, nằm trong thẻ `<style>`, được đặt trong `<head>`.
```
<!DOCTYPE html>
<html>
<head>
<style>
body {
  background-color: linen;
}

h1 {
  color: maroon;
  margin-left: 40px;
}
</style>
</head>
<body>

<h1>This is a heading</h1>
<p>This is a paragraph.</p>

</body>
</html>
```

##### *Inline CSS*
- Kiểu nội tuyến được sử dụng để áp dụng một kiểu duy nhất cho một thẻ.
- Được viết trược tiếp trên thẻ, thông qua thuộc tính `style`.
```
<!DOCTYPE html>
<html>
<body>

<h1 style="color:blue;text-align:center;">This is a heading</h1>
<p style="color:red;">This is a paragraph.</p>

</body>
</html>
```

*Lưu ý:*
- Không nên viết dạng `inline` vì nó khó quản lý và không tốt cho SEO.
- Dạng `internal` có thể chấp nhận, nên đặt CSS ở trong thẻ `<head>`, nhưng không khuyến khích vì nó cũng không tốt cho SEO.
- Dạng `external` khuyến khích sử dụng vì nó mang tính tách biết HTML với CSS, rất tốt cho SEO và dễ quản lý.

#### 2. Cơ cấu bộ quy tắc CSS
Hãy xem xét ví dụ về CSS ở trên chi tiết hơn: 

![](../image/css-declaration.png 'CSS ruleset')

Toàn bộ cấu trúc trên được gọi là một **bộ quy tắc**.

**Bộ chọn (Selector):** Tên phần tử HTML bắt đầu bộ quy tắc. Nó chọn (các) phần tử được tạo kiểu (trong trường hợp này là phần tử `p`). Để tạo kiểu cho một phần tử khác, chỉ cần thay đổi bộ chọn.
     
**Khai báo (Declaration):** Phần xác định thuộc tính của phần tử nào bạn muốn tạo kiểu.

**Thuộc tính (Properties):** Những cách mà bạn có thể tạo kiểu cho phần tử HTML. Đối với mỗi bộ chọn CSS, có thể áp dụng nhiều thuộc tính tạo kiểu.

**Giá trị thuộc tính (Property value)**: Xác định giá trị cho thuộc tính tạo kiểu.

*Lưu ý:* 
- Mỗi bộ quy tắc phải được bao bọc bởi cặp dấu ngoặc nhọn ({}).
- Trong mỗi khai báo, phải sử dụng dấu hai chấm (:) để ngăn cách thuộc tính và giá trị của nó. Kết thúc bằng dấu chấm phảy (;), để ngăn cách với các thuộc tính tiếp theo.

**Một số cách chọn phần tử:**
- Chọn nhiều phần tử: Bạn cũng có thể chọn nhiều kiểu phần tử và áp dụng một quy tắc duy nhất được đặt cho tất cả các yếu tố đó. Bao gồm nhiều bộ chọn được phân biệt bởi dấu phẩy (,).  
Ví dụ:
```
    p, li, h1 {
      color: red;
    }
```
- Các loại bộ chọn khác nhau:
    - **Bộ chọn phần tử (hay còn gọi là thẻ HTML)**: Chọn tất cả các phần tử HTML của loại được chỉ định.
     ```
        p {
          color: red;
        }
     ```
     
    - **Bộ chọn ID**: Sử dụng thuộc tính id của một phần tử HTML để chọn một phần tử cụ thể. ID của phần tử là duy nhất trên một trang, do đó bộ chọn ID sử dụng để chon một phần tử duy nhất. Để chọn một phần tử có một `id` cụ thể, bắt đầu bằng một ký tự dấu thăng (#), theo sau là `id` của phần tử.
    ```
        #para1 {
          color: red;
        }
    ```
    *Lưu ý:* Tên ID không được bắt đầu bằng số.
    
    - **Bộ chọn class**: Chọn các phần tử HTML với một thuộc tính `class` cụ thể. Để chọn các phần tử với một `class` cụ thể, bắt đầu bằng một ký tự dấu chấm (.), theo sau là tên `class`.
     ```
        .text-red {
          color: red;
        }
     ```
     Bạn cũng có thể chỉ định rằng chỉ các phần tử HTML cụ thể mới bị ảnh hưởng bởi một class.
     ```
         p.center {
           text-align: center;
           color: red;
         }
     ```
     Các phần tử HTML cũng có thể tham chiếu đến nhiều hơn một class.
     ```
        <p class="center large">This paragraph refers to two classes.</p>
     ```
     *Lưu ý:* Tên class không được bắt đầu bằng số.
     
    - **Bộ chọn thuộc tính**: Chọn (các) phần tử trên trang có thuộc tính được chọn.
     ```
        a[target='_blank'] {
            color: red;
        }
     ```
     Trong ví dụ trên, chọn ra những thẻ `<a>` có thuộc tính `target='_blank'`, nhưng không phải chọn toàn bộ thẻ `<a>`.
    
    - **Bộ chọn Pseudo-class**: Chọn (các) thành phần được chỉ định.
    Cú pháp:
    ```
        selector:pseudo-class {
          property: value;
        }
    ```
    Ví dụ:
    `<a href='#'>Click me</a>`
     ```
        a:hover {
            background: yellow;
        }
     ```
     Thẻ `<a>` chỉ được áp dụng đoạn CSS khi ở ở trạng thái di chuột qua liên kết.

#### 3. Mô hình hộp 
Một điều bạn sẽ nhận thấy về việc viết CSS là rất nhiều trong số đó là về các hộp (khối) - thiết lập kích thước, màu sắc, vị trí,... Hầu hết các phần tử HTML trên trang của bạn có thể coi là các hộp nằm trên đỉnh của nhau.

![](../image/box-model.png 'CSS Box Model')

Bố cục CSS chủ yếu dựa vào mô hình hộp. Mỗi hộp chiếm khoảng trống trên trang của bạn có các thuộc tính như sau:
- `padding (vùng đệm)`: không gian xung quanh nội dung.
- `border (đường viền)`: đường viền nằm ngay bên ngoài bao bọc nội dung.
- `margin (lề)`: khoảng cách xung quanh bên ngoài phần tử.

Theo ảnh minh hoạ trên, ví dụ:
```
    <p>
        Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Nulla id neque....
    </p>
```

CSS:
```
    div { 
          border: 5px solid black;
          padding: 20px;
          margin: 20px;
        }
```

*Luyện tập thêm về CSS Selector qua trò chơi [CSS Dinner](https://flukeout.github.io/)*
