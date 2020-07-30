# Accessibility

Khi thiết kế và tạo các trang web, điều quan trọng là các trang web có thể truy cập được đối với mọi đối tượng. Đặc biệt, do tính chất trực quan và năng động của các trang web mà bạn sẽ tạo ra, điều quan trọng là phải đảm bảo rằng trang web của bạn cũng sẽ có ý nghĩa đối với người dùng khiếm thị.

Viết HTML với khả năng tiếp cận tốt, ung cấp cho người dùng một cách tốt để điều hướng và tương tác với trang web của bạn. Làm cho mã HTML của bạn càng có ngữ nghĩa càng tốt, để mã dễ hiểu cho khách truy cập và trình đọc màn hình.

#### 1. Semantic HTML
Semantic HTML (hay Viết HTML có ngữ nghĩa) là cách viết HTML mà sử dụng các thẻ HTML ứng với nội dung được chứa trong nó chứ không phải sử dụng các thẻ theo cách mà chúng ta muốn nội dung trong đó được hiển thị. nếu bạn cần một nút, hãy sử dụng phần tử `<button>` (chứ không phải `<div>`).

- Non-Semantic: `<div>Click Me</div>`
- Semantic: `<button>Click Me</button>`

Bạn có thể tham khảo thêm [tại đây](./html_semantic.md)

#### 2. Nội dung văn bản
Một trong những khả năng tiếp cận tốt nhất mà người dùng đọc màn hình có thể có là một cấu trúc nội dung tuyệt vời với các tiêu đề, đoạn văn, danh sách,...

Ví dụ:
```
<h1>My heading</h1>
<p>This is the first section of my document.</p>
<p>I'll add another paragraph here too.</p>
<ol>
  <li>Here is</li>
  <li>a list for</li>
  <li>you to read</li>
</ol>
<h2>My subheading</h2>
<p>This is subsection of my document. I'd love people to be able to find this content!</p>
```

- Các công cụ tìm kiếm sử dụng các tiêu đề để lập chỉ mục cấu trúc và nội dung của các trang web của bạn.
- Người dùng đọc lướt các trang của bạn bằng các tiêu đề của nó. Điều quan trọng là sử dụng các tiêu đề để hiển thị cấu trúc tài liệu và các mối quan hệ giữa các phần khác nhau.

#### 3. Khai báo ngôn ngữ
Khai báo một ngôn ngữ rất quan trọng đối với trình đọc màn hình và công cụ tìm kiếm và được khai báo bằng thuộc tính lang. Sử dụng như sau để hiển thị một trang web bằng tiếng Anh:
```
<!DOCTYPE html>
<html lang="en">
<body>

...

</body>
</html>
```

#### 4. Sử dụng thuộc tính `alt` với hình ảnh
Không bắt buộc phải có thuộc tính `alt` cho hình ảnh, nhưng nó sẽ giúp ích cho trang web của bạn khi gặp sự cố (ví dụ như đặt sai đường dẫn, sự cố về internet khiến không thể hiển thị hình ảnh,...). Mặt khác nó còn cung cấp ngữ caảnh cho trình đọc màn hình. Do đó, nội dung của thuộc tính `alt` là mô tả những gì hình ảnh chứa.

#### 5. Bố cục trang
Trước kia, mọi người thường tạo bố cục trang bằng các bảng HTML - sử dụng các ô bảng khác nhau để chứa tiêu đề, chân trang, thanh bên, cột nội dung chính, v.v. Đây không phải là một ý tưởng hay vì trình đọc màn hình có thể sẽ gây nhầm lẫn bài đọc, đặc biệt nếu bố cục phức tạp và có nhiều bảng lồng nhau.
```
<table width="1200">
      <!-- main heading row -->
      <tr id="heading">
        <td colspan="6">

          <h1 align="center">Header</h1>

        </td>
      </tr>
      <!-- nav menu row  -->
      <tr id="nav" bgcolor="#ffffff">
        <td width="200">
          <a href="#" align="center">Home</a>
        </td>
        <td width="200">
          <a href="#" align="center">Our team</a>
        </td>
        <td width="200">
          <a href="#" align="center">Projects</a>
        </td>
        <td width="200">
          <a href="#" align="center">Contact</a>
        </td>
        <td width="300">
          <form width="300">
            <input type="search" name="q" placeholder="Search query" width="300">
          </form>
        </td>
        <td width="100">
          <button width="100">Go!</button>
        </td>
      </tr>
      <!-- spacer row -->
      <tr id="spacer" height="10">
        <td>

        </td>
      </tr>
      <!-- main content and aside row -->
      <tr id="main">
        <td id="content" colspan="4" bgcolor="#ffffff">

          <!-- main content goes here -->
        </td>
        <td id="aside" colspan="2" bgcolor="#ff80ff" valign="top">
          <h2>Related</h2>

          <!-- aside content goes here -->

        </td>
      </tr>
      <!-- spacer row -->
      <tr id="spacer" height="10">
        <td>

        </td>
      </tr>
      <!-- footer row -->
      <tr id="footer" bgcolor="#ffffff">
        <td colspan="6">
          <p>©Copyright 2050 by nobody. All rights reversed.</p>
        </td>
      </tr>
    </table>
```
Trình đọc màn hình sẽ hiểu đây là 1 bảng tài liệu, nó sẽ không phân biệt được các bố cục của trang.

Để cải thiện điều này, từ phiên bản của HTML5 đã cung cấp một số các phần tử phân đoạn bố cục. Bạn có thể tạo bố cục chỉ sử dụng các `<div>` lồng nhau, nhưng tốt hơn là sử dụng các yếu tố phân đoạn thích hợp để bọc điều hướng chính (`<nav>`), chân trang của bạn (`<footer>`), lặp lại các đơn vị nội dung (`<article>`),... Điều này không chỉ làm cho bố cục rõ ràng hơn mà còn không gây nhầm lẫn cho trình đọc màn hình.
```
<header>
  <h1>Header</h1>
</header>

<nav>
  <!-- main navigation in here -->
</nav>

<!-- Here is our page's main content -->
<main>

  <!-- It contains an article -->
  <article>
    <h2>Article heading</h2>

    <!-- article content in here -->
  </article>

  <aside>
    <h2>Related</h2>

    <!-- aside content in here -->
  </aside>

</main>

<!-- And here is our main footer that is used across all the pages of our website -->

<footer>
  <!-- footer content in here -->
</footer>
```

