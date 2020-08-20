## Mapping và Analyzers trong Elasticsearch

### Nội dung

1. Giới thiệu
2. Mapping
3. Inverted Index
4. Analysis


### 1. Giới thiệu

Elasticsearh là một công cụ tìm kiếm và phân tích toàn văn mã nguồn mở của khả năng mở rộng cao. Nó cho phép lưu trữ, tìm kiếm và phân tích khối lượng lớn dữ liệu một cách nhanh chóng.

Elasticsearch được coi là không có schema, điều này khác với cơ sở dữ liệu truyền  nơi chúng ta phải xác định rõ ràng các loại bảng, trường và kiểu dữ liệu. Elasticsearch sử dụng mapping giống như schema.thống

### 2. Mapping
Mapping mô tả các fields trong document cùng với các kiểu dữ liệu của chúng, và cách chúng được thiết lập. Cụ thể mapping dùng để định nghĩa:

- Fields nào được sử dụng như full text search, fields nào cần analysis(phân tích).
- Kiểu dữ liệu của fields: number, date, geolocations…
- Các custom khác...

Tạo mapping là phần đầu tiên cũng là phần quan trọng nhất trong quá trình xây dựng lên base ES, nên cần chú ý tổ chức Mapping hợp lý và tối ưu nhất.


![document](elasticsearch/image/mapping-1.png)

##### Giải thích:

- Các Properties ("title", "name" và "age") được định nghĩa với type ( kiểu dữ liệu và cách Mapping cho từng Field ) ngay khi Index được khởi tạo.
- Properties "created" có type "date" khai báo thêm format.

##### Chú ý:
 
 Nếu không chỉ định mapping rõ ràng, Elasticsearch sẽ cố tạo mapping dự trên document đầu tiên chèn vào. Mapping cũng sẽ được tự động cập nhật khi các trường mới được thêm vào document.
 
### 3. Inverted Index

Sở dĩ ES trả về kết quả search cực nhanh bởi vì thay vì tìm kiếm text by text, ES tìm kiếm theo Inverted Index.

Cách thức của Inverted Index khá đơn giản các văn bản được phân tách ra thành từng từ có nghĩa sau đó được map xem thuộc văn bản nào. Khi Search tùy thuộc vào loại search sẽ đưa ra kết quả cụ thể.

VD: Chúng ta có 2 văn bản cụ thể như sau 

    1. The quick brown fox jumped over the lazy dog
    
    2. Quick brown foxes leap over lazy dogs in summer
    
Kết quả khi Inverted Index như sau:
  

![document](elasticsearch/image/inverted-index.png)

Có thể thấy các từ sẽ được tách thành tổ hợp các Tokens of Terms. Và công việc tìm kiếm sẽ dựa trên tổ hợp các Tokens of Terms này. Vậy làm thể nào để ES tác được các chuỗi thành Tokens of Terms như vậy? Đó là quá trình Analysis.

### 4. Analysis

Là quá trình chuyển đổi các document properties từ dạng text sang dạng Tokens of Terms. Các Tokens of Terms này được thêm vào Inverted Index để searching. Quá trình Analysis sẽ được thực hiện qua các Analyzer, các Analyzer có thể là các Analyzer sẵn có của Elasticsearch hoặc các Analyzer do chúng ta định nghĩa. Ta có thể chỉ định Analyzer ngay khi khởi tạo Index hoặc trong quá trình Searching.

Cấu trúc cơ bản của một Analyzer:


![document](elasticsearch/image/analyzer.png)

#### Character Filter

Là bước đầu tiên của quá trình Analysis, ở bước này các ký tự được chuyển đổi thành dữ liệu phù hợp với yêu cầu search. Quá trình này sẽ giúp thêm, loại bỏ hoặc thay đổi ký tự, chuyển đổi các ký tự thành từ có nghĩa. 

VD: chuyển đổi đoạn văn bản html thành văn bản thông thường

![document](elasticsearch/image/character_filter.png)

example:

![document](elasticsearch/image/ex1.png)

thành 

![document](elasticsearch/image/ex2.png)

Quá trình Character Filter gồm có:
- HTML Strip Character Filter: chuyển đổi văn bản html thành văn bản thường loại bỏ các thẻ html.
- Mapping Character Filter: thay thể, chuyển đổi ký tự, từ thành các ký tự, từ phù hợp. Ví dụ: ký tự ‘&’ thành ‘and’.
- Pattern Replace Character Filter: lọc thay thế bất kỳ các từ khớp với pattern bằng các từ, ký tự thay thể được chỉ định.

##### Chú ý:
Một analyzer có thể có 0 hoặc nhiều bộ lọc Character Filter.

#### Tokenizers

Sau khi đoạn text đã được xử lý chuyển đổi các ký tự xong, nó sẽ được phân tách thành các Tokens of Terms độc lập sử dụng các Tokenizers. 

Elasticsearch cung cấp rất nhiều các tokenizers để phục vụ yêu cầu phân tách. Tokenizer cũng chịu trách nhiệm ghi lại thứ tự hoặc vị trí của mỗi term và các ký tự bắt đầu, kết thúc của từ gốc mà  này đại diện.token

Ví dụ: whitespace tokenizer sẽ phân tách văn bản thành token dựa vào các khoảng trắng (space).

![document](elasticsearch/image/whitespace.png)

thành các token

![document](elasticsearch/image/ex2.png)

Các bạn có thể tham khảo các tokenizers ở [đây](https://www.elastic.co/guide/en/elasticsearch/reference/current/analysis-tokenizers.html)

##### Chú ý: 

Note: Một Analyzer có duy nhất một Tokenizer

#### TokenFilter

Sau khi các đoạn text được tách và cho ra các token, các token sẽ được đưa và một hoặc nhiều TokenFilter, tại đây các token sẽ được thêm, bớt, hoặc chỉnh sửa tùy thuộc vào TokenFilter.

Các TokenFilter các chức năng chuyển đổi các token như lowercase chuyển đổi các token thành chữ thường, stopwords loại bỏ các từ thường dùng stopwords không mang nhiều ý nghĩa thể hiện nội dung văn bản.
TokenFilter không được phép thay đổi vị trí hoặc ký tự của các token.

Ví dụ: sử dụng TokenFilter loại bỏ các stopwords

![document](elasticsearch/image/filter.png)

Các bạn có thể tham khảo các TokenFilter ở [đây](https://www.elastic.co/guide/en/elasticsearch/reference/6.8/analysis-tokenfilters.html)

##### Note: 

Một Analyzer có 0 hoặc nhiều TokenFilter.

###### Tác giả: Nguyễn Văn Nam (namnv1)







