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

# SKILLCERTPRO Microsoft Azure Solutions Architect Expert (AZ-305) Master Cheat Sheet

## 2. Azure Monitor (Giám sát Azure)

- PaaS (Platform as a Service) (Nền tảng dưới dạng Dịch vụ)
- Pipeline for metric log data coming from any Azure resource provider. (Đường ống dữ liệu số liệu số đo đạc đến từ bất kỳ nhà cung cấp tài nguyên Azure nào.)
- Fastest telemetry pipeline: Faster than Log Analytics. (Đường ống dữ liệu truyền thông nhanh nhất: Nhanh hơn Log Analytics.)
- Collected data is saved in Log Analytics to analyze, monitor, visualize metrics and query and analyze logs. (Dữ liệu được thu thập được lưu trong Log Analytics để phân tích, giám sát, hiển thị số liệu số đo và truy vấn cũng như phân tích các nhật ký.)
  - Visualize:
    - Dashboard
    - Views
    - Power BI
    - Workbooks
  - Analyze:
    - Metrics Explorer (Trình khám phá số liệu số đo)
    - Log Analytics (Phân tích nhật ký)

### Respond (Phản hồi):
- Alerts (Cảnh báo)
- Autoscale (Tự tự điều chỉnh)

### Integrate (Tích hợp):
- Event Hubs (Trung tâm Sự kiện)
- Logic Apps (Ứng dụng Logic)
- Ingest & Export APIs (API nhập và xuất dữ liệu)

### You can use alerts to proactively notify you based on rules with Azure Alerts. (Bạn có thể sử dụng cảnh báo để thông báo một cách chủ động dựa trên các quy tắc với Azure Alerts.)
### You can access through o Azure Insight & Analytics (OMS portal that's now legacy) o On Azure portal there's an existing resource called Azure Monitor. o Rest API, PowerShell & CLI (Bạn có thể truy cập thông qua o Azure Insight & Analytics (cổng thông tin OMS hiện đã cũ) o Trên cổng thông tin Azure, có một tài nguyên hiện có gọi là Azure Monitor. o Rest API, PowerShell & CLI)

### Data types (Loại dữ liệu)
- Two levels of logs: resource (metrics) and platform (activity log, diagnostic log). (Hai cấp độ nhật ký: tài nguyên (số liệu số đo) và nền tảng (nhật ký hoạt động, nhật ký chẩn đoán).)
- All data types can be queried in Portal, PowerShell, Rest API or CLI. (Tất cả các loại dữ liệu có thể được truy vấn trong Portal, PowerShell, Rest API hoặc CLI.)

### Metrics (Số liệu số đo)
- On resource level (Trên cấp độ tài nguyên)
- All numerical values including (Tất cả các giá trị số bao gồm)
  - All Application Insights data / telemetry (Tất cả dữ liệu / dữ liệu điều khiển ứng dụng)
  - System health from VMs (uses HyperV metrics without any configuration) (Sức khỏe hệ thống từ các máy ảo (sử dụng số liệu số đo HyperV mà không cần cấu hình))

### Can be visualized & queried (Có thể được hiển thị và truy vấn)
- 30 days free to store & query (30 ngày miễn phí để lưu trữ và truy vấn)
- E.g. requests and errors, average response time, infrastructure metrics (Ví dụ: yêu cầu và lỗi, thời gian phản hồi trung bình, số liệu số đo cơ sở hạ tầng)

### Activity Log (Nhật ký hoạt động)
- On platform level (Trên cấp độ nền tảng)
- "Outside operations" that are subscription-level events (Các hoạt động "bên ngoài" là các sự kiện cấp độ đăng ký)
- Previously known as "Audit Logs" or "Operational Logs" (Trước đây được biết đến là "Nhật ký Kiểm toán" hoặc "Nhật ký Hoạt động")
- Determine "what, who and when" for any write operation taken on the resources. (Xác định "gì, ai và khi nào" cho bất kỳ hoạt động viết nào được thực hiện trên tài nguyên.)
- 90 days free to store, fore more send to Log Analytics ("connect" button in Activity Logs blade of Log Analytic), archive to storage account (click on Export to Event Hubs in Azure Monitor) or stream to other services (click on Export to Event Hubs in Azure Monitor). (90 ngày miễn phí để lưu trữ, gửi thêm vào Log Analytics ("nút kết nối" trong lưỡi cắt Nhật ký Hoạt động của Log Analytic), lưu trữ trong tài khoản lưu trữ (nhấp vào Xuất đến Trung tâm Sự kiện trong Azure Monitor) hoặc dòng dữ liệu đến các dịch vụ khác (nhấp vào Xuất đến Trung tâm Sự kiện trong Azure Monitor).)
- During export you create a Log Profile you control how/where/what is exported for how long. (Trong quá trình xuất, bạn tạo một Hồ sơ Nhật ký để kiểm soát cách/ở đâu/gì được xuất trong bao lâu.)

### Activity log categories (Các loại Nhật ký hoạt động)
- Administrative (Quản trị)
  - Every API call to Azure Resource Manager (Mọi cuộc gọi API đến Azure Resource Manager)
  - E.g. create virtual machine or delete network security group (Ví dụ: tạo máy ảo hoặc xóa nhóm bảo mật mạng)
- Service health (Sức khỏe dịch vụ)
  - Any service health incidents occurred in Azure (Mọi sự cố sức khỏe dịch vụ xảy ra trong Azure)
  - Come in 5 varieties: Action Required, Assisted Recovery, Incident, Maintenance, Information, Security. (Có 5 loại: Yêu cầu hành động, Khôi phục có hỗ trợ, Sự cố, Bảo trì, Thông tin, Bảo mật.)
  - E.g. SQL Azure in East US is experiencing downtime. (Ví dụ: SQL Azure tại East US đang gặp sự cố ngừng hoạt động.)
- Resource health (Sức khỏe tài nguyên)
  - Status of resources: Available, Unavailable, Degraded, Unknown (Trạng thái của tài nguyên: Có sẵn, Không có sẵn, Bị suy giảm, Không rõ)
  - E.g. Virtual Machine health status changed to unavailable (Ví dụ: Trạng thái sức khỏe Máy ảo đã thay đổi thành không có sẵn)
- Alert (Cảnh báo)
  - All activations of Azure alerts. (Tất cả các hoạt động kích hoạt cảnh báo Azure.)
  - E.g. CPU % on a VM has been over 80 for the past 5 minutes (Ví dụ: CPU % trên một máy ảo đã vượt qua 80% trong 5 phút gần đây)
- Autoscale (Tự tự điều chỉnh)
  - Events in autoscale engine defined by your settings. (Các sự kiện trong hệ thống tự điều chỉnh được xác định bởi cài đặt của bạn.)
  - E.g. Scale up action failed (Ví dụ: Hoạt động mở rộng thất bại)
- Recommendation (Gợi ý)
  - How to better utilize your resources. (Cách tận dụng tài nguyên tốt hơn.)
- Security (Bảo mật)
  - Events by Azure Security Center (Các sự kiện bởi Trung tâm Bảo mật Azure)
  - E.g. Suspicious double extension file executed. (Ví dụ: Tệp có phần mở rộng kép nghi ngờ được thực thi.)
- Policy (Chính sách)
  - All effect action operations performed by Azure Policy. (Tất cả các hoạt động ảnh hưởng được thực hiện bởi Chính sách Azure.)

### Diagnostic Log (Nhật ký chẩn đoán)
- On platform level (Trên cấp độ nền tảng)
- "Inside operations" within the resource (Các hoạt động "bên trong" trong tài nguyên)
- Resource-specific with common scheme where resources include their own properties. (Chỉ định tài nguyên với mẫu chung nơi các tài nguyên bao gồm các thuộc tính riêng của chúng.)
- E.g. IIS logs, web server logging, failed request tracking (Ví dụ: Nhật ký IIS, nhật ký máy chủ web, theo dõi yêu cầu thất bại)
- Can be streamed (to Power BI, Azure Functions etc.), added in blob storage, and sent directly to Log Analytics (Có thể dòng dữ liệu (đến Power BI, Azure Functions v.v.), thêm vào lưu trữ blob và gửi trực tiếp đến Log Analytics)

### Azure Alerts (Cảnh báo Azure)
- All alert creation for metrics, logs and activity log across Azure Monitor, Log Analytics, and Application Insights (Tất cả việc tạo cảnh báo cho số liệu số đo, nhật ký và nhật ký hoạt động trên toàn bộ Azure Monitor, Log Analytics và Application Insights)
- Separation of operational and configuration views: Alert Rules (Quy tắc Cảnh báo): Definition of the condition that triggers an alert (Phân chia cách nhìn về hoạt động và cấu hình: Quy tắc Cảnh báo: Định nghĩa điều kiện gây ra cảnh báo)
  - Fired Alerts (Cảnh báo đã kích hoạt): An instance of the alert rule firing (Một trường hợp của quy tắc cảnh báo đã kích hoạt)

### Flow of alerts (Dòng cảnh báo)
- Set-up alert rule (Thiết lập quy tắc cảnh báo)
  - Target resource (e.g. storage account) (Tài nguyên mục tiêu (ví dụ: tài khoản lưu trữ))
  - Signal: Types are Metric, Activity log, Application Insights and Log (Tín hiệu: Các loại bao gồm Số liệu số đo, Nhật ký hoạt động, Application Insights và Nhật ký)
  - You can have multi-dimensional metrics & monitor multiple metrics with a single rule (currently up to two) (Bạn có thể có số liệu số đo đa chiều và giám sát nhiều số liệu số đo với một quy tắc duy nhất (hiện tại tối đa là hai))
  - Criteria (Tiêu chí)
  - Logic test: e.g. six-hour period when capacity is over 10 MB (Kiểm tra logic: ví dụ, thời kỳ sáu giờ khi dung lượng vượt quá 10 MB)
- Action group (= actions to do) (Nhóm hành động [= các hành động cần thực hiện])
  - Grouping of different actions to take when the alert is triggered (Nhóm các hành động khác nhau để thực hiện khi cảnh báo được kích hoạt)
  - Each action has name & action type e.g. email/sms/push/voice/webhook/automation runbook (Mỗi hành động có tên và loại hành động, ví dụ: email/sms/push/voice/webhook/automation runbook)
  - Applied rate limiting: (Áp dụng giới hạn tỷ lệ:)
    - SMS: No more than 1 SMS every 5 minutes. (Không quá 1 SMS mỗi 5 phút.)
    - Voice: No more than 1 Voice call every 5 minutes. (Không quá 1 cuộc gọi thoại mỗi 5 phút.)
    - Email: No more than 100 emails in an hour. (Không quá 100 email trong một giờ.)
    - Other actions are not rate limited. (Các hành động khác không bị giới hạn tỷ lệ.)
  - Set alert rule name, description, severity (can be informational, warning, error, critical) (Thiết lập tên quy tắc cảnh báo, mô tả, mức độ nghiêm trọng (có thể là thông tin, cảnh báo, lỗi, nghiêm trọng))

### Log alerts (Cảnh báo nhật ký)
- Defined by Log Query (by Log Analytics), Time period, frequency, and threshold. (Được xác định bởi Truy vấn Nhật ký (bởi Log Analytics), Khoảng thời gian, tần suất và ngưỡng.)
- Number of results alert rules always creates a single alert, while Metric measurement alert rule creates an alert for each object that exceeds the threshold (Số lượng quy tắc cảnh báo kết quả luôn tạo một cảnh báo duy nhất, trong khi quy tắc cảnh báo số liệu số đo tạo một cảnh báo cho mỗi đối tượng vượt quá ngưỡng)

### Azure Advisor (Người tư vấn Azure)
- Uses telemetry & application configurations to give personalized recommendations and guidance for o high availability, security, performance, cost effectiveness (monitors unused resources and spent). (Sử dụng dữ liệu điều khiển & cấu hình ứng dụng để đưa ra các gợi ý cá nhân và hướng dẫn cho o khả năng sẵn có cao, bảo mật, hiệu suất, hiệu quả về chi phí (theo dõi tài nguyên không sử dụng và chi phí đã tiêu).)
- Common resource, free for all users (Tài nguyên chung, miễn phí cho tất cả người dùng)
- You can download, filter, postpone, and dismiss recommendations. (Bạn có thể tải xuống, lọc, hoãn và bỏ qua các gợi ý.)
- You can customize by excluding subscription/resource groups, configuring utilization rules (e.g. you can as a subscription owner set CPU to lower threshold) (Bạn có thể tùy chỉnh bằng cách loại trừ đăng ký/nhóm tài nguyên, cấu hình các quy tắc sử dụng (ví dụ: bạn có thể đặt ngưỡng CPU thấp hơn như một chủ sở hữu đăng ký))

### Log Analytics (Phân tích nhật ký)
- PaaS (Platform as a Service) (Nền tảng dưới dạng Dịch vụ)
- It's also referred as (newer names) o Azure Monitor Logs (Cũng được gọi là (các tên mới) o Azure Monitor Logs)
  - Azure Monitor log data is stored in Log Analytics (Dữ liệu nhật ký Azure Monitor được lưu trữ trong Log Analytics)
  - The term is changed from "Log Analytics" to "Azure Monitor Logs" (see) (Thuật ngữ đã thay đổi từ "Phân tích Nhật ký" thành "Nhật ký Azure Monitor" (xem))
o Log Search (Tìm kiếm nhật ký)
  - "Log Search" interface in Azure Monitor (Monitor -> Logs) (Giao diện "Tìm kiếm nhật ký" trong Azure Monitor (Monitor -> Logs))
  - Or Log Analytics Workspace -> Logs (Hoặc Không gian làm việc Log Analytics -> Logs)

### Two main features (Hai tính năng chính)
- Log Analytics Workspace where Azure Monitor stores its data (Không gian làm việc Log Analytics nơi Azure Monitor lưu trữ dữ liệu của nó)
- Log search feature; collect, correlate, search, and act on data with any schema. (Tính năng tìm kiếm nhật ký; thu thập, tương quan, tìm kiếm và thực hiện trên dữ liệu với bất kỳ cấu trúc dữ liệu nào.)

### Business value (Giá trị kinh doanh)
- Assessing updates: From logs can guess average patching time (Đánh giá cập nhật: Từ nhật ký, có thể đoán thời gian bình quân của việc vá lỗi)
- Change tracking: Abnormal behavior from a specific account by tracking changes throughout the environment (Theo dõi thay đổi: Hành vi bất thường từ một tài khoản cụ thể bằng cách theo dõi các thay đổi trong môi trường)
- Free to store logs for 90 days of charge (Miễn phí lưu trữ nhật ký trong 90 ngày)
- You can export to Excel, PowerBI, or use API to send data or get. (Bạn có thể xuất ra Excel, PowerBI hoặc sử dụng API để gửi dữ liệu hoặc nhận.)

### Sending data to Log Analytics (Gửi dữ liệu đến Log Analytics)
- Log analytics uses push-model i.e. data is pushed to it. (Log Analytics sử dụng mô hình đẩy, tức là dữ liệu được đẩy đến nó.)
- Data can be pushed from integrated sources including (Dữ liệu có thể được đẩy từ các nguồn tích hợp bao gồm)
  - Connected Azure sources e.g. IIS logs, custom text logs with custom fields, error level etc. (Các nguồn Azure kết nối như nhật ký IIS, nhật ký văn bản tùy chỉnh với các trường tùy chỉnh, cấp độ lỗi v.v.)
  - Office 365, Azure Automation, Back-ups (Office 365, Azure Automation, Sao lưu)
  - You cannot change schema on ingestion time for integrated resources, only on query time. (Bạn không thể thay đổi cấu trúc dữ liệu vào thời gian tiếp nhận cho các nguồn tài nguyên tích hợp, chỉ có thể thay đổi vào thời gian truy vấn.)

### Data can also be pushed Linux & Windows systems with an agent (Dữ liệu cũng có thể được đẩy từ hệ thống Linux và Windows với một tác nhân)
- Agents include (Các tác nhân bao gồm)
  - Log analytics agent (Tác nhân Log analytics)
  - Operations Manager (Quản trị viên Hoạt động)
  - Allows using existing investments with SCOM (System Center Operations Manager) (Cho phép sử dụng các đầu tư hiện có với SCOM (Quản trị viên Trung tâm Hệ thống))
  - SCOM agents communicate with SCOM Server over TLS 1.2 which forward events and performance data to Log Analytics. (Các tác nhân SCOM giao tiếp với Máy chủ SCOM qua TLS 1.2, chuyển tiếp sự kiện và dữ liệu hiệu suất đến Log Analytics.)
  - You can install agents using a script via Azure Automation DSC (desired state configuration) (Bạn có thể cài đặt các tác nhân bằng cách sử dụng một kịch bản thông qua Azure Automation DSC (cấu hình trạng thái mong muốn))
  - Agents are already installed in cloud Windows VMs (Các tác nhân đã được cài đặt sẵn trong các VM Windows trên đám mây)

### You can also use Log Analytics REST APIs to send custom data with any schema you want (Bạn cũng có thể sử dụng các API REST Log Analytics để gửi dữ liệu tùy chỉnh với bất kỳ cấu trúc dữ liệu nào bạn muốn)

### Collect data across subscriptions (Thu thập dữ liệu qua các đăng ký)
- Log analytics applies if in same subscription, or in same Azure Active Directory tenant. (Log Analytics áp dụng nếu ở cùng đăng ký hoặc cùng trong cùng một người quản lý Azure Active Directory.)
- So single Log Analytics workspace can monitor across under same tenant. (Vì vậy, Không gian làm việc Log Analytics đơn lẻ có thể giám sát qua cùng một người quản lý.)
- To collect data across subscriptions and tenants: (Để thu thập dữ liệu qua các đăng ký và người quản lý:)
  - In customer subscription (Trong đăng ký của khách hàng)
    - Activity log (export button) => Event Hub (Nhật ký hoạt động (nút xuất) => Event Hub)
  - In Service provider subscription (Trong đăng ký của nhà cung cấp dịch vụ)
    - Logic App (When events are available in Event Hub -> Parse JSON (Body) -> Compose (Select Body in inputs) -> Send Data (Azure Log Analytics Data Collector)) => Log Analytics (Logic App (Khi các sự kiện có sẵn trong Event Hub -> Phân tích JSON (Nội dung) -> Soạn (Chọn Nội dung trong đầu vào) -> Gửi dữ liệu (Bộ sưu tập dữ liệu Azure Log Analytics)) => Log Analytics)
- Azure Monitor Logs support query across multiple Log Analytics workspaces across subscriptions (Nhật ký Azure Monitor hỗ trợ truy vấn qua nhiều Không gian làm việc Log Analytics trên các đăng ký)

### Querying Log Analytics (Truy vấn Log Analytics)
- Each data source has documentation (description & name) of its properties. (Mỗi nguồn dữ liệu đều có tài liệu (mô tả và tên) về các thuộc tính của nó.)
- Main query tables: Heartbeat, Perf, Usage, Event, Syslog, Alert. (Bảng truy vấn chính: Heartbeat, Perf, Usage, Event, Syslog, Alert.)
- You can connect to Activity Logs in Activity Logs section and query with AzureActivity Kusto Query Language (KQL) (Bạn có thể kết nối với Nhật ký hoạt động trong phần Nhật ký hoạt động và truy vấn bằng AzureActivity Kusto Query Language (KQL))

### Kusto Query Language (KQL) (Ngôn ngữ Truy vấn Kusto (KQL))
- A pipe-through language to query log analytics data (Một ngôn ngữ truy vấn dữ liệu phân qua để truy vấn dữ liệu phân tích nhật ký)
- E.g.: Event | where (EventLevelName == "Error") | where (TimeGenerated > ago(1days)) | summarize ErrorCount = count() by Computer | top 10 by ErrorCount desc (Ví dụ: Sự kiện | where (EventLevelName == "Error") | where (TimeGenerated > ago(1days)) | summarize ErrorCount = count() by Computer | top 10 by ErrorCount desc)
- Can generate charts | render timechart that can be pinned to dashboard. (Có thể tạo biểu đồ | render timechart có thể ghim vào bảng điều khiển.)

