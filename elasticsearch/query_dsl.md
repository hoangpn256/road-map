## Query DSL trong Elasticsearch

### Nội dung

1. Query DSL
2. Filter context
3. Query context
3. Kết hơp nhiều truy vấn

### 1. Query DSL
Query DSL là một ngôn ngữ tìm kiếm linh hoạt, dự trên JSON để định nghĩa truy vấn mà elasticsearch sử dụng. Query DSL làm cho các truy vấn linh hoạt hơn, chính xác hơn, dễ đọc hơn và dễ gỡ lỗi hơn.
 
#### Cấu trúc truy vấn

Các truy vấn Elasticsearch bao gồm một hoặc nhiều mệnh đề truy vấn. Các mệnh đề truy vấn có thể được kết hợp để tạo ra các mệnh đề truy vấn khác, được gọi là truy vấn kép. Tất cả các mệnh đề truy vấn có một trong 2 định dạng sau:
 
![structure_query](elasticsearch/image/structure_query.png)

Các mệnh đề truy vấn (QUERY_CLAUSE) có thể lồng nhau trong các mệnh đề truy vấn khác:

![query_](elasticsearch/image/query_clause.png)

Tất cả các truy vấn có thể được phân loại thành 3 :

- Filter context: Filter theo giá trị chính xác.
- Query context: Tìm kiếm trên văn bản đã phân tích.
- Kết hợp của Query context và Filter context.

### 2. Filter context

Truy vấn này thường được sử dụng cho các dữ liệu kiểu số, ngày tháng, enum...trong một số trường như user_id, age, created_at... Filter context trả lời
cho câu hỏi 'Tài liệu này có phù hợp với mệnh đề truy vấn này không?', câu trả lời đơn giản là 'có' hoặc 'không'. Filter context chủ yếu được sử dụng để lọc dữ liệu có cấu trúc.

Filter context thường được sử dụng sẽ đuợc Elasticsearch tự động lưu vào bộ nhớ đệm để tăng tốc hiệu suất.

Ví dụ: truy vấn Filter context với gender là 'filter' và age >= 50

![filter_context_](elasticsearch/image/filter_context.png)

#### Một số truy vấn Filter context phổ biến

##### Term Filter 

Truy vấn term trả về những record có chứa giá trị chính xác boolean, integer, date, string(not_analyzed)... trong query.
 
![term_](elasticsearch/image/term.png)

##### Terms Filter 

Giống với term nhưng cho phép chỉ định nhiều giá trị phù hợp. Nếu trường chứa bất kỳ giá trị nào được chỉ định, thì document sẽ được lấy ra.

![terms_](elasticsearch/image/terms.png)

##### Range Filter 

Cho phép tìm kiếm các số hoặc ngày nằm trong một phạm vi được chỉ định. 

![range_](elasticsearch/image/range.png)

Một số toán tử trong range filter:

- gt: lớn hơn.
- gte: lớn hơn hoặc bằng.
- lt: nhỏ hơn.
- lte: nhỏ hơn hoặc bằng.

Có thể tham khảo các Filter context  ở [đây](https://www.elastic.co/guide/en/elasticsearch/reference/current/term-level-queries.html)

### 3. Query context

Một mệnh đề truy vấn được sử dụng trong query context trả lời câu hỏi "document này phù hợp với mệnh đề truy vấn nhiều như thế nào?".
Bên cạnh việc quyết định xem có khớp hay không, mệnh đề truy vấn cũng tính toán điểm liên quan trong trường _score ở meta

Các trường thực hiện query context thường được phân tính từ trước và có các loại phân tích (analyzer) cho mỗi loại field (xem bài mapping, analyzer).

#### Một số truy vấn Query context phổ biến

##### match_all Query

Truy vấn khớp với tất cả các ducument. Đây là truy vấn mặc định được sử dụng nếu không có truy vấn nào được chỉ định.

![match_all_](elasticsearch/image/match_all.png)

Ở truy vấn này tất cả các document được coi là liên quan như nhau, vì vậy tất cả các document đều có _score là 1.

##### match Query

Đây là truy vấn chuẩn bất cứ khi nào muốn truy vấn toàn văn hoặc chính xác trong hầu hết mọi trường. Bao gồm truy vấn kết hợp và truy vấn cụm từ hoặc gần đúng. Match query chấp nhận văn bản, số, ngày tháng.
 
Khi thực hiện truy vấn match với một trường full-text, nó sẽ phân tích chuỗi truy vấn bằng cách sử dụng analyzer cho trường đó trước khi search.

![match](elasticsearch/image/match.png)

Khi thực hiện truy vấn trên một trường có chứa giá trị chính xác như number, time, boolean, not_analyzed... nó sẽ tìm kiếm chính xác giá trị đó.

![match_2](elasticsearch/image/match_2.png)

##### multi_match Query

Truy vấn multi_match cho phép chạy cùng một truy vấn  trên nhiều trường:match

![multi_match](elasticsearch/image/multi_match.png)

###### Note
multi_match có thể đánh trọng số mức độ ưu tiên các fields:

![multi_2](elasticsearch/image/multi_2.png)

##### Một số params quan trọng trong query context

| Tham số | Các giá trị | Giải thích |
| ----- | -------- | -------- |
| query(Required) |  Text, number, boolean | sẽ được phân tích thành các tokens trước khi tìm kiếm |
| analyzer(Optional) | loại analyzer | sử dụng analyzer để chuyển đổi văn bản trong query thành token |
| operator(Optional) |  'and', 'or' | 'or' hoặc ‘and’ các tokens đã được tách|
| zero_terms_query | none, all | none: không trả về document khi không có tokens, all: trả về tất cả các document tương đương match_all |
                                 
Có thể tham khảo các query context  ở [đây](https://www.elastic.co/guide/en/elasticsearch/reference/current/term-level-queries.html)

### 4. Kết hợp nhiều truy vấn 

Bool query có thể kết hợp nhiều các truy vấn đơn (match, term….) để tăng hiệu quả các câu truy vấn. Nó được sử dụng để kết hợp nhiều mệnh đề query khác sử dụng toán tử boolean để tạo ra một logic hợp lý.

Các loại bool query:

- must:  phải phù hợp với tất cả các điều kiện và có tính _score.
- filter: giống với must nhưng bỏ qua _score.
- should: Chỉ cần phù hợp vs một trong các điều kiện.
- must_not: Ngược lại với must, phải không phù hợp với tất cả các điều kiện.

![bool](elasticsearch/image/bool.png)

###### Tác giả: Nguyễn Văn Nam (namnv1)

