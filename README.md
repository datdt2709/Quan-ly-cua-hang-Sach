# Kiến trúc Hexagonal (Ports and Adapters):
 # 1. Domain Layer:
## Chức năng chính
- Lớp core chứa bussines logic cốt lõi và các quy tắc nghiệp vụ của hệ thống.
- Định nghĩa các entity, value object (VO), constants và các exception liên quan đến domain.
- Không phụ thuộc vào bất kỳ layer nào khác
- Là layer innermost trong kiến trúc onion/ layered architecture
## Các thành phần chính
- model folder ( hoặc có thể đặt tên là entities folder): Chứa entity chính của hệ thống như User, Course...
- vo (Value Object): Các đối tượng giá trị như ...
- dto:Các đối tượng chuyển đổi dữ liệu giữa các layer như CourseRequest, CourseResponse ...
- constants: Các hằng số
- events: Domain events 
- exceptions:Các exception đặc thù như BadRequestException, DataNotFoundException....
- annotations:Custom annotations
- util:Các tiện ích hỗ trợ cho domain như ExcelUtil, TimeUtil...

  
 # 2. Application Layer: 
## Chức năng chính
- Chức năng use case của hệ thống
- Điều phối luồng dữ liệu giữa domain và infrastructure
- Triển khai các interface được định nghĩa trong domain layer (???)
## Các thành phần chính
- service: Các business services
- usecases: Các use case chính của hệ thống (khai báo các Interface)
- helper:Các helper services hỗ trợ xử lý business logic
- ports:t  input: Input ports ( Implement các interface cho usecase)
  output: Output ports ( Các interface cho external services để truy cập dữ liệu) được triển khai trong adapter
- proxies: Proxy pattern implementation cho các ports
- scheduler: Các scheduled tasks (cron jobs)
- constants: Application-level constants
- utils: Các tiện ích hỗ trợ cho application layer như DateUtil, EnvironmentUtil ....

 # 3. Infrastruc
   
