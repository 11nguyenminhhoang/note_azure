# SKILLCERTPRO Microsoft Azure Solutions Architect Expert (AZ-305) Master Cheat Sheet

## 1. Azure Basics (Cơ bản về Azure)

### Interacting with Azure (Tương tác với Azure)
- Azure is based on REST APIs. (Azure dựa trên các REST APIs.)
- You can use the Portal, PowerShell, Azure CLI that wrap REST APIs. (Bạn có thể sử dụng Portal, PowerShell, Azure CLI để bọc REST APIs.)
- Azure Cloud Shell: Browser-accessible shell on the portal that can run PowerShell, Azure CLI, and even more like git/bash/pip/maven, etc. (Azure Cloud Shell: Shell có thể truy cập qua trình duyệt trên portal, có thể chạy PowerShell, Azure CLI và thậm chí là các công cụ khác như git/bash/pip/maven, v.v.)
- Azure CLI can often handle everything that other wrappers can and even more. (Azure CLI thường có thể xử lý tất cả những gì các công cụ khác có thể và thậm chí nhiều hơn.)

### Service-level Agreement (SLA) (Thỏa thuận mức dịch vụ)
- A guarantee that Azure gives to customers for different offerings. (Một cam kết mà Azure đưa ra cho khách hàng cho các dịch vụ khác nhau.)
- Guarantees Monthly Uptime Percentage. (Đảm bảo tỷ lệ hoạt động hàng tháng.)
- Monthly Uptime % = (Maximum Available Minutes – Downtime) / Maximum Available Minutes x 100. (Tỷ lệ hoạt động hàng tháng % = (Số phút có thể hoạt động tối đa - Thời gian ngừng hoạt động) / Số phút có thể hoạt động tối đa x 100.)

### Regions (Khu vực)
- Azure has different regions. (Azure có các khu vực khác nhau.)
- Each Azure Region has one or more (often 3) availability zones. (Mỗi Khu vực Azure có một hoặc nhiều (thường là 3) khu vực có khả năng sẵn sàng.)
  - Each availability zone is made up of one or more data centers. (Mỗi khu vực khả dụng bao gồm một hoặc nhiều trung tâm dữ liệu.)
  - Data centers have independent power, cooling, and networking. (Trung tâm dữ liệu có nguồn điện, làm mát và mạng độc lập.)
- Each region includes a pair in its country (>500 kms away if possible). (Mỗi khu vực bao gồm một cặp trong nước của nó (> 500 km nếu có thể).)
  - Pairs enable system update isolation where regions are updated in a queue. (Các cặp cho phép cô lập cập nhật hệ thống trong đó các khu vực được cập nhật theo hàng đợi.)
  - Azure region pair is highly prioritized during recovery. (Cặp khu vực Azure được ưu tiên cao trong quá trình khôi phục.)
  - Services with geo-redundant storage use the paired region automatically. (Các dịch vụ có lưu trữ đa vùng địa lý sử dụng khu vực ghép cặp một cách tự động.)

### Resource Group (Nhóm tài nguyên)
- Logical group to manage resources together. (Nhóm logic để quản lý tài nguyên cùng nhau.)
- Groups values, e.g. analyzing and forecasting resource consumption and spending. (Nhóm các giá trị, ví dụ: phân tích và dự báo tiêu thụ và chi phí tài nguyên.)
- You can create policies on a resource group. (Bạn có thể tạo chính sách trên một nhóm tài nguyên.)
- A resource is an object in Azure (Azure object). (Một tài nguyên là một đối tượng trong Azure (đối tượng Azure).)

## Azure Resource Manager (ARM) (Trình quản lý tài nguyên Azure)

- Each object in Azure has ARM files associated with it. (Mỗi đối tượng trong Azure có các tệp ARM đi kèm.)
- Can be deployed directly from Visual Studio. (Có thể triển khai trực tiếp từ Visual Studio.)
- They are JSON text files. (Chúng là các tệp văn bản JSON.)
  - $schema (required): URL of the JSON schema file describing the version. ($schema (bắt buộc): URL của tệp mô tả phiên bản của JSON schema.)
  - contentVersion (required): Version of the template (e.g. 1.0.0.0). (contentVersion (bắt buộc): Phiên bản của mẫu (ví dụ: 1.0.0.0).)
  - resources (required): Resource types that are deployed or updated in the group. (resources (bắt buộc): Các loại tài nguyên được triển khai hoặc cập nhật trong nhóm.)
  - parameters: Customizable values provided when the deployment is executed. (parameters: Các giá trị có thể tùy chỉnh được cung cấp khi triển khai được thực hiện.)
  - variables: JSON fragments in the template to simplify language expressions. (variables: Các đoạn JSON trong mẫu để đơn giản hóa biểu thức ngôn ngữ.)
  - outputs: Values that are returned after deployment. (outputs: Các giá trị được trả về sau khi triển khai.)
  - Secure any username, password parameters in JSON files. (Bảo mật bất kỳ tham số tên người dùng, mật khẩu trong các tệp JSON.)
- Usually, parameters (azuredeploy.parameters.json) and the file (azuredeploy.json) are separated. (Thường thì, các tham số (azuredeploy.parameters.json) và tệp (azuredeploy.json) được tách ra.)
- It's recommended to use a base and modify later. (Nên sử dụng một cơ sở và sau đó chỉnh sửa.)
  - Create a resource, copy its auto-generated ARM from the Automation blade. (Tạo một tài nguyên, sao chép tệp ARM tự động được tạo ra từ lưỡi cắt Tự động hóa.)
  - Use Azure QuickStart templates maintained by Microsoft and the community on GitHub. (Sử dụng các mẫu Azure QuickStart được duy trì bởi Microsoft và cộng đồng trên GitHub.)

### Egress Charges (Phí xuất cảnh)
- Moving data to Azure is mostly free. (Di chuyển dữ liệu đến Azure hầu như miễn phí.)
- From Azure to outside (without ExpressRoute or Content Delivery Network), you get extra egress charges. (Từ Azure ra bên ngoài (không có ExpressRoute hoặc Mạng phân phối nội dung), bạn sẽ phải trả thêm phí xuất cảnh.)

## 2.1. Monitoring (Giám sát)

### Monitoring (Giám sát)
- Act of collecting & analyzing data to determine the performance, health, and availability of applications and their dependent resources. (Hoạt động thu thập & phân tích dữ liệu để xác định hiệu suất, sức khỏe và khả năng sẵn có của các ứng dụng và tài nguyên phụ thuộc của chúng.)
- Understanding the operation of applications and alerts helps fix problems before they occur. (Hiểu về hoạt động của các ứng dụng và cảnh báo giúp khắc phục các vấn đề trước khi chúng xảy ra.)

### Azure Monitoring Services (Dịch vụ Giám sát Azure)
#### Application Monitoring (Giám sát ứng dụng):
- Application Insights

#### Deep Infrastructure Monitoring (Giám sát cơ sở hạ tầng sâu):
- Log Analytics
- Management Solutions
- Network Monitoring
- Service Map

#### Core Monitoring (Giám sát cốt lõi):
- Azure Monitor
- Advisor
- Service Health
- Activity Log

#### Shared Capabilities (Khả năng chia sẻ):
- Alerts
- Dashboards
- Metrics Explorer

### Azure Monitoring Costs (Chi phí Giám sát Azure)
- Use Pricing Calculator for a specific resource. (Sử dụng Bộ tính giá cho một tài nguyên cụ thể.)
- Review estimated costs when creating a resource. (Xem xét các chi phí ước tính khi tạo một tài nguyên.)
- See spent costs through the Subscription blade. (Xem chi phí đã tiêu qua lưỡi cắt Đăng ký.)
  - You can tag resources for cost analysis, e.g. costCenter: marketing. (Bạn có thể gắn thẻ tài nguyên để phân tích chi phí, ví dụ: costCenter: marketing.)
- View your bill in "Invoices," opt-in for PDF invoices & download. (Xem hóa đơn của bạn trong "Hóa đơn," chọn tham gia cho hóa đơn PDF & tải về.)
- External services billed separately. (Các dịch vụ bên ngoài được tính phí riêng biệt.)
- Get notifications through Azure Advisor or Azure Cost Management for anomalies and overspending risks. (Nhận thông báo thông qua Azure Advisor hoặc Quản lý Chi phí Azure về các sự cố và rủi ro chi phí vượt quá.)

### Azure Monitor (Giám sát Azure)
- PaaS (Platform as a Service) (Nền tảng dưới dạng Dịch vụ)
- Pipeline for metric log data coming from any Azure resource provider. (Đường ống cho dữ liệu nhật ký số liệu đến từ bất kỳ nhà cung cấp tài nguyên Azure nào.)
- Fastest telemetry pipeline: Faster than Log Analytics. (Đường ống siêu dữ liệu nhanh nhất: Nhanh hơn cả Log Analytics.)
- Collected data is saved in Log Analytics to analyze, monitor, visualize metrics, and query and analyze logs. (Dữ liệu được thu thập được lưu trữ trong Log Analytics để phân tích, giám sát, hiển thị số liệu thống kê và truy vấn cũng như phân tích các nhật ký.)
  - Visualize:
    - Dashboard
    - Views
    - Power BI
    - Workbooks
  - Analyze:
    - Metrics Explorer
    - Log Analytics
