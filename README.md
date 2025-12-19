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

 # 3. Adapter Layer:
## Chức năng chính:
- Kết nối với hệ thống bên ngoài và chứa các thành phần liên quan đến công nghệ cụ thể như:Rest Controller, database, repositories, schedulers...
- Là layer outermost trong kiến trúc, có thể thay đổi mà không ảnh hưởng đến các layer bên trong
- Xử lý các tác vụ I/O như giao tiếp HTTP, truy cập DB ...
## Các thành phần chính
- in/rest: Rest API Controllers
- out: Các adapters kết nối với external systems
  - mysql: Database adapters (Triển khai theo chiều dọc- chứa nhiều folder và logic). Bao gồm:
    - configs
    - constants
    - converter
    - data
    - entities (Khai báo các class với từ khóa @Entity)
    - repositories
    - services
  
  - elasticsearch: (Trong folder này chứa nhiều các folder con). Ví dụ:
    - constants
    - converters
    - entities
    - helper
    - queries
    - services
    - utils
  - mongodb
  - iam
- config: Các configuration classes cho adapters (Ví dụ các folder dưới đây):
  - aop:
    - annotation
    - aspect
  - authorize:
  - cache
  - health_check
  - keycloak   
- events: Event listeners và object
- utils: Utility functions cho adapters
 
   
