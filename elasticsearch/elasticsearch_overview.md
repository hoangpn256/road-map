### Elasticsearch Overview
##### Tác giả: Nguyễn Thị Hà @hant

### Nội dung
1. Giới thiệu
2. Các khái niệm cơ bản 
3. Mô hình hoạt động cluster-node-shard
4. Mô hình hoạt động lưu dữ liệu
5. Mô hình hoạt động lấy dữ liệu.


#### 1. Giới thiệu

- Cha đẻ: Shay banon
- Elasticsearch là công cụ tìm kiếm(mã nguồn mở) được phát triển dựa trên Apache Lucene, 
tìm kiếm phân tán, giao diện web HTTP có hỗ trợ dữ liệu Json
- Viết bằng: Java
- Hệ điều hành: Đa nền tảng
- Được phát triển từ năm 2004 với tên là Compass. Từ 2/2010 đổi tên thành elasticsearch. 
Đến nay đã có 33v được release(2020)


#### 2. Các khái niệm cơ bản
- Document: là một JSON object, đây là basic information unit trong ES. Đây là đơn vị nhỏ nhất để lưu dữ liệu trong ES.

![document](elasticsearch/image/document.png)

- Index: Mỗi index là một tập hợp các document.
- Type: Một định nghĩa về schema của một document bên trong một index. (một index có thể có nhiều type)

![index](elasticsearch/image/index.png)

Nhìn trong ảnh ta sẽ thấy 1 document sẽ có 1 trường type. Đây chính là định danh của một document.

  - ES sử dụng cấu trúc **inverted index**, được thiết kế cho việc tìm kiếm full-text-search.
  
  ![inverted%20index](elasticsearch/image/inverted%20index.png)
  
  - Khi search, đầu vào sẽ được tách ra thành các từ có nghĩa (term), dựa vào term tìm ra các doc có chứa term và đưa ra các doc tương đồng với tỉ lệ trùng khớp là **score**

- Cluster: 

![cluster](elasticsearch/image/cluster.png)

  - Cluster là nơi chứa tất cả mọi thứ, là một hệ thống bao gồm nhiều node(máy chủ).
  - Trong cluster có thể có rất nhiều node - node là nơi xử lý và lưu trữ dữ liệu.
  - Mỗi cluster có một node chính (master) - được chọn tự động, ngẫu nhiên và có thể thay thế nếu có sự cố xảy ra.
- Shards: Tập con các documents của một index. Một index có thể được chia thành nhiều shard.
- Thông thường, khi khởi tạo một cluster mặc định thì sẽ chỉ có một node, nếu muốn có nhiều node hơn thì sẽ phải tự setting. Nên setting node ở các server khác nhau thì mới thể hiện được bản chất của nó.
Nếu để tất cả các node ở cùng một chỗ, khi có lỗi thì toàn bộ node sẽ chết hết.
- Trong một node có các shard. Hiểu đơn giản hãy tưởng tượng node là nơi lưu dữ liệu, cụ thể là nó lưu vào shard. Tức là shard là đơn vị lưu trữ nhỏ nhất. Thường ta sẽ không tác động gì vào shard hết, nên chỉ cần hiểu như vậy là đủ.
- Shard được chia làm 2 loại: Primary Shard(PS) và Replica Shard(RS). PS là shard chính còn RS là bản sao của PS. Mặc định của hệ thống, mỗi index sẽ có 5 PS và 5 RS.

Vì sao lại phải phân ra 2 loại như vậy thì sẽ giải thích bên dưới.

#### 3. Mô hình hoạt động cluster-node-shard

![cluster-node-shard](elasticsearch/image/cluster-node-shard.png)

Đầu tiên, hãy chú ý đến node master. Như đã nói ở trên, node master sẽ được chọn một cách tự động và ngẫu nhiên. 
- PS là shard chính, là nơi chịu trách nhiệm đánh index và lưu dữ liệu. 
- RS là shard được sao chép từ PS tương ứng. 1 PS có thể có 1 hoặc nhiều hơn 1 RS.
- PS và RS không bao giờ cùng hoạt động trên cùng 1 node. Trong trường hợp default, cluster chỉ có 1 node, vẫn sẽ có 5 PS và 5 RS, tuy nhiên chỉ có 5 PS hoạt động.
- Khi cluster có 2 node trở lên, dựa vào thuật toán Round-robin để sắp xếp các PS và các RS sao cho PS và RS của nó không nằm trên cùng 1 node, để tất cả các shard này đều hoạt động tốt.
- Để công thức tính phân phối shard không bị sai. chúng ta không nên thay đổi số lượng shard mặc định của hệ thống.

#### 4. Mô hình hoạt động (lưu trữ)

![save_document](elasticsearch/image/save_document.png)

   - Request được gửi đến node master. Tại đây, với thuật toán round-robin, xác định được shard dùng để lưu trữ. Trong trường hợp này hệ thống tính ra được sẽ lưu dữ liệu vào shard0.
   - Hệ thống tim được PS0 ở node 3. Tiến hành đánh index và lưu dữ liệu vào PS0.
   - Sao chép dữ liệu PS0 sang RS0 ở node 1 và node 2.
   
#### 5. Mô hình hoạt động (lấy dữ liệu)

![get_document](elasticsearch/image/get_document.png)

  - Request được gửi tới node master. Tại đây xác định PS cho document sẽ là 0.
  - Do tất cả node đều lưu dữ liệu, nên master node sẽ chọn ra 1 node và lấy dữ liệu ở shard số 0. Việc chọn này giúp giảm tập trung vào một node. Thuật toán Round-robin được sử dụng để các shard được chọn khác nhau ở mỗi request. Trong trường hợp này Node 2 được chọn.
  - Replica 0 ở Node 2 trả về kết qủa cho master node
  
