# PDO (PHP Data Objects) & DTO (Data Transfer Object)

## Giới thiệu
Trong dự án này, chúng ta sẽ tìm hiểu về hai khái niệm quan trọng trong lập trình PHP: PDO (PHP Data Objects) và DTO (Data Transfer Object). 

- **PDO**: Cung cấp một giao diện nhất quán để truy cập vào cơ sở dữ liệu.
- **DTO**: Là một mẫu thiết kế dùng để chuyển giao dữ liệu giữa các thành phần trong ứng dụng.

## PDO (PHP Data Objects)

### Giới thiệu
PDO là một extension trong PHP giúp kết nối và tương tác với nhiều loại cơ sở dữ liệu khác nhau. PDO hỗ trợ các truy vấn đã chuẩn bị, xử lý lỗi, và giao dịch (transactions).

### Lợi ích của PDO
- **Abstraction Layer**: Cho phép chuyển đổi giữa các loại cơ sở dữ liệu mà không cần thay đổi mã nguồn nhiều.
- **Bảo mật**: Hỗ trợ prepared statements giúp bảo vệ ứng dụng khỏi SQL Injection.
- **Xử lý lỗi**: Sử dụng ngoại lệ để quản lý lỗi dễ dàng.
- **Hỗ trợ giao dịch**: Cho phép thực hiện nhiều thao tác như một giao dịch duy nhất.

### Ví dụ
```php
try {
    $pdo = new PDO('mysql:host=localhost;dbname=testdb', 'username', 'password');
    $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    $stmt = $pdo->prepare("SELECT * FROM users WHERE email = :email");
    $stmt->execute(['email' => $userEmail]);
    $user = $stmt->fetch();
} catch (PDOException $e) {
    echo "Connection failed: " . $e->getMessage();
}
DTO (Data Transfer Object)
Giới thiệu
DTO là một mẫu thiết kế được sử dụng để truyền dữ liệu giữa các lớp hoặc thành phần trong ứng dụng mà không cần chứa logic xử lý.

Lợi ích của DTO
Giảm thiểu số lượng phương thức gọi: Tích hợp dữ liệu trong một đối tượng để truyền tải nhanh chóng.
Tính rõ ràng: Tạo ra một cấu trúc dữ liệu dễ hiểu hơn.
Tối ưu hóa hiệu suất: Giúp giảm thiểu quá trình truyền tải dữ liệu phức tạp bằng cách nhóm dữ liệu lại.
Ví dụ
```php
class UserDTO {
    public $id;
    public $name;
    public $email;

    public function __construct($id, $name, $email) {
        $this->id = $id;
        $this->name = $name;
        $this->email = $email;
    }
}
```
```php
// Sử dụng DTO
$userDTO = new UserDTO(1, 'John Doe', 'john@example.com');
```

Kết luận
[PDO] và [DTO] là hai công cụ hữu ích trong phát triển ứng dụng PHP. Việc sử dụng chúng một cách hợp lý sẽ giúp tối ưu hóa quản lý cơ sở dữ liệu và cải thiện hiệu suất của ứng dụng.

Tài liệu tham khảo
[PDO Documentation](https://www.php.net/manual/en/book.pdo.php)
[Data Transfer Object Pattern](https://en.wikipedia.org/wiki/Data_transfer_object)
