## Tổng quan về Bareos

### 1. Khái niệm

**Bareos** (viết tắt của cụm từ **B**ackup, **A**rchive, **RE**covery **O**pen **S**ourced) là một tập hợp chương trình máy tính cho phép quản lý sao lưu, phục hồi dữ liệu giữa các máy tính với nhau thông qua hệ thống mạng. Bareos có thể được cài đặt trên một máy chủ và sao lưu được nhiều dữ liệu khác nhau bao gồm cả disk và tape.

Về mặt kỹ thuật, Bareos là một chương trình sao lưu dữ liệu dựa theo mô hình client/server. Vì thế, nó tương đối dễ sử dụng và hiệu quả, đồng thời còn cung cấp thêm nhiều tính năng phục vụ cho việc quản lý lưu trữ, dễ dàng tìm kiếm và khôi phục các file bị hỏng. Bằng cách thiết kế chia thành các module, Bareos có thể được mở rộng từ một hệ thống nhỏ thành một hệ thống lớn lên đến hàng trăm máy tính thông qua mạng.

### 2. Thành phần của Bareos

Bareos bao gồm các thành phần, dịch vụ sau:  Director, Console, File, Storage, và Monitor services.

#### 2.1 Bareos Director

**Director** là một chương trình điều khiển trung tâm cho tất cả các daemon khác của Bareos. Nhiệm vụ của nó là lập lịch và giám sát các tác vụ sao lưu, phục hồi, kiểm soát và lưu trữ. Director là một dịch vụ chạy ngầm (daemon) trong hệ thống Linux. 

#### 2.2 Bareos Console

**bconsole** là một chương trình giúp người dùng giao tiếp với Bareos Director thông qua cửa sổ các câu lệnh. 

#### 2.3 Bareos File Daemon

**Bareos File Daemon** là một chương trình được cài đặt trên mỗi máy khách (client) để thực hiện việc sao lưu dữ liệu. Khi có yêu cầu từ phía Director, nó sẽ tìm kiếm các file đã được định sẵn cho quá trình sao lưu (backup) và gửi chúng về Bareos Storage Daemon.

Tùy thuộc vào hệ điều hành mà máy khách sử dụng, nó sẽ lấy và cung cấp thông tin của dữ liệu khi có yêu cầu từ Director.

Nó cũng đảm nhận quá trình khôi phục dữ liệu trên client.

#### 2.3 Bareos Storage Daemon

Đảm nhận nhiệm vụ lưu trữ dữ liệu trong hệ thống. Khi có yêu cầu từ Director, dữ liệu và các thông tin (attributes) được gửi về từ File Daemon được đưa vào phương tiện lưu trữ vật lý hoặc các volume. Trong trường hợp nhận được yêu cầu phục hồi dữ liệu (restore), nó có trách nhiệm tìm file, dữ liệu và gửi tới File Daemon.

Một hệ thống Bareos có thể có nhiều Storage Daemon và được quản lý bởi Director. Và được chạy ngầm (background) trên các máy chủ phục vụ việc lưu trữ dữ liệu.

#### 2.4 Catalog

Các dịch vụ Catalog bao gồm các chương trình có nhiệm vụ lưu trữ các thông tin chỉ mục (index) của file và thông tin volume của các file đã được backup về hệ thống. Nó giúp chúng ta xác định vị trí và phục hồi dữ liệu một cách nhanh chóng. Nó lưu trữ thông tin của các Volume đang được sử dụng, các Job đang chạy, và các file đã được lưu trữ.
Hiện tại, Bareos hỗ trợ 3 loại database là PortgreSQL, MySQL, và SQLite. Một trong số chúng phải được chọn trước khi cài đặt Bareos.


### 3. Tài liệu tham khảo

- https://docs.bareos.org/IntroductionAndTutorial.html
