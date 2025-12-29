# Tổng kết tuần 9 (21/12/2025 - 27/12/2025)

## 📅 Thông tin cơ bản
- **Thời gian**: 22/12/2025 - 27/12/2025
- **Tuần thực tập**: 9/8 (Tuần cuối cùng của Giai đoạn 5: Triển khai Cloud & Hoàn thiện)
- **Tổng số giờ làm việc**: 20 giờ (4 giờ/ngày x 5 ngày)

## 🎯 Mục tiêu tuần
- [x] Triển khai Frontend lên AWS S3 + CloudFront.
- [x] Thiết lập tự động hóa Frontend deployment bằng GitHub Actions và phân quyền IAM Role (OIDC).
- [x] Đưa Back-end (Page Service, AIChat Service) lên AWS ECS (Docker) và cấu hình RDS (PostgreSQL).
- [x] Cài đặt S3 Storage để lưu trữ tài nguyên hình ảnh cho Page và Event.
- [x] Cấu hình Application Load Balancer (ALB) để định tuyến traffic đến các Microservices Backend.
- [x] Sử dụng CloudFormation để đóng gói toàn bộ hạ tầng (Infrastructure as Code).
- [x] Kiểm tra hiệu năng thực tế trên môi trường Production.
- [x] Chuẩn bị báo cáo bàn giao sản phẩm và trình bày tổng kết thực tập.
- [x] Tham gia buổi bàn giao sản phẩm.

## ✅ Thành tựu nổi bật trong tuần (Key Achievements)

### 1. **Triển khai Frontend & Hoàn thiện CI/CD**
- **Mô tả**: Đã triển khai thành công Frontend (Next.js) lên AWS S3 và phân phối qua CloudFront. Toàn bộ quy trình deployment đã được tự động hóa bằng GitHub Actions, sử dụng OIDC và IAM Roles để xác thực an toàn, đảm bảo mỗi lần push code lên nhánh `main` đều tự động build, deploy và invalidate CloudFront cache. Tên miền tùy chỉnh đã được cấu hình qua Route53.
- **Ý nghĩa**: Đảm bảo Frontend có hiệu suất cao, bảo mật và quy trình cập nhật nhanh chóng, đáng tin cậy.
- **Evidence**: [Link GitHub Actions Workflow (final) (Cần thêm ảnh/link)], [URL Frontend (Cần thêm ảnh/link)]

### 2. **Triển khai Backend Microservices lên AWS ECS & RDS**
- **Mô tả**: Cả Page Service và AIChat Service (Spring Boot) đã được triển khai lên AWS ECS (Fargate) với Docker. Mỗi service đều có RDS PostgreSQL instance riêng, cấu hình an toàn trong private subnets. Đã tích hợp AWS Secrets Manager để quản lý database credentials, tuân thủ best practices bảo mật. S3 bucket riêng đã được thiết lập để lưu trữ tài nguyên hình ảnh.
- **Ý nghĩa**: Các Backend Microservices đã hoạt động trên môi trường Cloud có khả năng mở rộng, bảo mật và hiệu năng.
- **Evidence**: [Screenshot ECS Services (Cần thêm ảnh/link)], [Screenshot RDS Instances (Cần thêm ảnh/link)]

### 3. **Thành lập Hạ tầng với CloudFormation (IaC)**
- **Mô tả**: Toàn bộ hạ tầng Cloud (VPC, Subnets, Security Groups, IAM Roles, ECS Cluster, Task Definitions, ECS Services, RDS, S3, CloudFront, ALB, Route53) đã được định nghĩa bằng CloudFormation templates. Điều này cho phép triển khai, quản lý và tái tạo môi trường một cách nhất quán và tự động.
- **Ý nghĩa**: Chuyển đổi sang phương pháp Infrastructure as Code, nâng cao khả năng quản lý, nhất quán và độ tin cậy của hạ tầng.
- **Evidence**: [Link GitHub CloudFormation templates (final) (Cần thêm ảnh/link)], [Screenshot CloudFormation Root Stack (Cần thêm ảnh/link)]

### 4. **Kiểm tra Hiệu năng & Bàn giao Sản phẩm**
- **Mô tả**: Đã thực hiện kiểm tra hiệu năng cơ bản trên môi trường Production, giám sát tài nguyên bằng CloudWatch và đảm bảo hệ thống hoạt động ổn định. Toàn bộ tài liệu dự án, mã nguồn và cấu hình hạ tầng đã được tổng hợp và chuẩn bị cho buổi bàn giao cuối cùng. Buổi bàn giao và trình bày tổng kết đã diễn ra thành công, nhận được phản hồi tích cực từ mentor và team.
- **Ý nghĩa**: Xác nhận hệ thống sẵn sàng cho Production và hoàn tất mọi công tác bàn giao một cách chuyên nghiệp.
- **Evidence**: [Screenshot CloudWatch Metrics (Cần thêm ảnh/link)], [Link Folder bàn giao tài liệu (Cần thêm ảnh/link)]

## 📈 Đánh giá tiến độ (Progress Review)
- **Mục tiêu hoàn thành**: 100% các mục tiêu đặt ra cho tuần này.
- **So với kế hoạch**: Đã đi đúng lộ trình và hoàn thành xuất sắc tất cả các nhiệm vụ triển khai Cloud và hoàn thiện sản phẩm. Giai đoạn 5 đã kết thúc một cách thành công.
- **Trạng thái dự án**: Dự án đã được triển khai hoàn chỉnh trên AWS, toàn bộ hạ tầng được định nghĩa bằng code, sẵn sàng để bàn giao và tiếp tục phát triển.

## 🚧 Phân tích thách thức (Challenges Analysis)

### 1. **Cấu hình Mạng VPC và Bảo mật cho Microservices**
- **Mô tả**: Khi triển khai Microservices trên ECS và RDS, việc cấu hình chính xác VPC (Subnets, Route Tables, NAT Gateway) và Security Groups là cực kỳ phức tạp. Các vấn đề như ECS Task không kết nối được RDS, hoặc AIChat Service không gọi được API bên ngoài là phổ biến.
- **Nguyên nhân gốc rễ**: Thiếu hiểu biết sâu sắc về cách các thành phần mạng AWS tương tác với nhau trong kiến trúc Microservices phân tán.
- **Cách giải quyết**: Rà soát kỹ tài liệu, debug log chi tiết (CloudWatch Logs), và thực hiện các thử nghiệm cấu hình nhỏ. Đảm bảo Security Groups chỉ cho phép traffic cần thiết và RDS Subnet Groups bao gồm đủ các private subnets.
- **Bài học rút ra**: Mạng là nền tảng của Cloud. Hiểu rõ VPC và Security Groups là thiết yếu để xây dựng hệ thống Microservices an toàn và hoạt động tốt.

### 2. **Quản lý Credentials và Secrets**
- **Mô tả**: Ban đầu, có nguy cơ hardcode database credentials hoặc API keys vào Task Definition của ECS.
- **Nguyên nhân gốc rễ**: Thiếu kinh nghiệm với các giải pháp quản lý secrets trên Cloud.
- **Cách giải quyết**: Nhanh chóng tích hợp AWS Secrets Manager để lưu trữ và truy xuất các thông tin nhạy cảm. Đồng thời, cấu hình IAM Roles cho ECS Tasks để chỉ có quyền truy cập vào các secrets cụ thể, tuân thủ nguyên tắc đặc quyền tối thiểu.
- **Bài học rút ra**: Luôn ưu tiên bảo mật. Sử dụng các dịch vụ quản lý secrets chuyên dụng (như AWS Secrets Manager) và IAM Roles là bắt buộc cho môi trường Production.

### 3. **Phức tạp của Infrastructure as Code với CloudFormation**
- **Mô tả**: Xây dựng CloudFormation templates cho toàn bộ hạ tầng (gồm nhiều dịch vụ và dependency phức tạp) đòi hỏi sự hiểu biết sâu sắc về cú pháp YAML, các hàm nội tại và cách quản lý dependency giữa các tài nguyên/stacks. Lỗi triển khai stack và rollback là thường xuyên.
- **Nguyên nhân gốc rễ**: Độ phức tạp vốn có của IaC khi mới bắt đầu.
- **Cách giải quyết**: Chia nhỏ template thành các nested stacks hoặc các independent stacks theo chức năng. Tập trung vào việc tạo ra các stack nhỏ, dễ debug trước, sau đó mới tổng hợp. Sử dụng `DependsOn` và `Fn::ImportValue` một cách cẩn thận để quản lý các liên kết.
- **Bài học rút ra**: IaC là một kỹ năng thiết yếu. Bắt đầu từ những cấu hình đơn giản, thực hành liên tục và tham khảo tài liệu chi tiết sẽ giúp thành thạo.

## 💡 Phát triển kỹ năng (Skills Development)
- **Kỹ năng Kỹ thuật**:
    - **Cloud Deployment**: Master việc triển khai toàn diện ứng dụng lên AWS (S3, CloudFront, Route53, ECS Fargate, RDS, ALB, Secrets Manager, CloudWatch).
    - **DevOps & CI/CD**: Xây dựng CI/CD pipeline (GitHub Actions với OIDC) cho cả Frontend và Backend (mặc dù backend CI/CD chưa hoàn thiện hoàn toàn, nhưng đã có nền tảng).
    - **Infrastructure as Code (IaC)**: Thành thạo việc sử dụng AWS CloudFormation để định nghĩa, triển khai và quản lý toàn bộ hạ tầng.
    - **Container Orchestration**: Kinh nghiệm làm việc với ECS và Docker containers.
    - **Security & Networking**: Nâng cao hiểu biết về VPC, Security Groups, IAM Roles, Secrets Management.
- **Kỹ năng Mềm**:
    - **Problem Solving & Debugging**: Phát triển khả năng xác định và giải quyết các vấn đề phức tạp trong môi trường Cloud.
    - **Project Management**: Đưa một dự án từ giai đoạn thiết kế đến triển khai và bàn giao một cách có tổ chức.
    - **Technical Documentation & Presentation**: Kỹ năng tổng hợp tài liệu, báo cáo và trình bày các giải pháp kỹ thuật một cách rõ ràng, chuyên nghiệp.
    - **Perseverance & Adaptability**: Khả năng kiên trì vượt qua các thách thức và thích nghi với các công nghệ, công cụ mới.

## 🚀 Kế hoạch tuần tới (Next Week Planning)
- **Giai đoạn 6: Sau thực tập (28/12/2025 onwards)**
- **Mục tiêu chính**: Áp dụng các kiến thức và kỹ năng đã học để tìm kiếm cơ hội việc làm hoặc bắt đầu một dự án cá nhân mới.
- **Nhiệm vụ cụ thể**:
    - **28/12/2025**:
        - Hoàn tất mọi thủ tục hành chính liên quan đến thực tập.
        - Dọn dẹp môi trường làm việc cá nhân.
        - Phản tư sâu sắc về toàn bộ hành trình thực tập, đánh giá lại mục tiêu ban đầu và những gì đã đạt được.
    - **Từ 29/12/2025**:
        - Cập nhật CV và LinkedIn profile với các dự án và kỹ năng mới.
        - Bắt đầu tìm kiếm các vị trí Software Engineer/DevOps Engineer Junior.
        - Nghiên cứu sâu hơn về AWS CDK như một giải pháp IaC thay thế.
        - Khám phá các công nghệ và xu hướng mới trong lĩnh vực Cloud Native.

---
_Worklog created by: Lư Hiếu Trung_  
_Next review: N/A (Thực tập đã kết thúc)_