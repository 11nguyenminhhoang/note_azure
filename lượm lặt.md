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
  - Services with geo-redundant storage use the paired region automatically. (Các dịch vụ có lưu trữ đa vùng địa lý sử dụ

