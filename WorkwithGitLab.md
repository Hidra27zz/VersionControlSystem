# 5. LÀM VIỆC CÙNG VỚI GITLAB
## 1. Làm việc với Remote Repository
- Đầu tiên bạn phải hiểu kỹ về Remote Repository là gì ?
- như bạn đã biết thì một trong những mục tiêu chính của sự ra đời Git là giúp cho những lập trình viên làm chung trong một dự án có thể làm việc chung với nhau một cách dễ dàng, tránh xung đột về code, thư mục một cách tối đa nhất. Ở phần này, ta sẽ đi sâu vào các thao tác mà bạn phải thực hiện khi làm việc chung với các lập trình viên khác. Khi bạn làm việc với Git thì hầu hết các thao tác làm việc là ở local (ở máy client) với Local Repository như commit, xem lịch sử,... Khi có như cầu chia sẻ, hoặc làm việc nhóm, hoặc đơn giản hơn là làm việc ở nhiều máy (ở văn phòng, ở nhà,...) thì lúc đó bạn sẽ sử dụng đến Remote Repository - một Repository lưu ở phía Server. Git Server là máy chủ Git cho phép tạo các Repository, GitLab chính là một máy chủ Git, có thể tạo một Repository thì đó chính là Remote Repository. Bạn có thể sao chép (clone) Remote Repository về máy thành Local Repository để làm việc và cập nhật phiên bản mới lên Remote Repository,...
- Dưới đây là sơ đồ mô tả cách mà Local Repository trên máy bạn làm việc với Remote Repository.
![image](https://github.com/Nan27Hid/VersionControlSystem/assets/135946173/0c370f07-5287-478d-a7d6-99a3c6182788)

- Bài giảng này sẽ hướng dẫn bạn những thao tác đơn giản để có thể sử dụng Remote Repository.

## 2. Cài đặt SSH Key cho GitLab với Window
- SSH là một chương trình tương tác giữa máy chủ và máy khách có sử dụng cơ chế mã hóa đủ mạnh nhằm ngăn các hiện tượng nhìn trộm, ăn cắp thông tin. Sử dụng SSH là biện pháp hữu hiệu để bảo mật dữ liệu trên đường truyền từ hệ thống này đến hệ thống khác.

**Ưu điểm:**
- Bảo mật các kết nối của máy tính với Server
- Không phải nhập mật khẩu GitLab mỗi lần Pull hoặc Push Code

**Cơ chế hoạt động:**
- Bạn sẽ có 2 key: Public Key (khóa công khai) và Private Key (khóa riêng tư). Bạn sẽ gửi Public Key của mình cho Git Server (GitLab) của bạn. Sau đó ssh-agent sẽ làm tất cả những việc còn lại. Mỗi lần bạn Push hay Pull code thì ssh-agent sẽ tự động gửi những thông tin chứng thực. Từ đó GitLab sẽ nhận diện được bạn và sẽ bỏ qua bước bắt bạn nhập mặt khẩu.

## 3. Làm quen giao diện Web của GitLab
- Chúng ta sẽ dành một chút thời gian để khám phá giao diện web của GitLab vì đó là cách dễ dàng nhất để xem code, thư mục trong một dự án mà không cần clone một bản sao hoàn chỉnh của dự án về máy (Local repository). Có khá nhiều điều mà bạn có thể làm thông qua giao diện web của Gitlab. Đây không phải một hướng dẫn đầy đủ về những gì bạn có thể sử dụng ở giao diện web GitLab nhưng sẽ cho bạn một số ý tưởng về những gì có thể và không thể làm tại đó.

## 4. Thực hiện commit thông qua giao diện web GitLab
- Ở phần trước bạn đã biết cách sử dụng git commit để có thể commit một phiên bản dự án mới với Terminal rồi. Tuy nhiên nếu bạn muốn sửa code của mình ngay trên Remote Repository thì có được không? Câu trả lời là có.
- Bài giảng này sẽ hướng dẫn bạn cách tạo một commit hoàn toàn mới thông qua giao diện web Gitlab.
- Video: Thực hiện commit thông qua giao diện web Gitlab

## 5. Lấy các thay đổi từ Remote Repository
- Git pull là lệnh dùng để tải xuống dữ liệu code, thư mục từ một Remote repository và cập nhật Local repository phù hợp với dữ liệu đó. Nói cách khác, Git pull là lệnh kết hợp các thay đổi từ Remote repository vào Local repository.
- Về bản chất, Git pull chính là sự kết hợp của 2 lệnh Git fetch và Git merge. Giai đoạn đầu, Git pull sẽ thực thi lệnh Git fetch ở phạm vi nhánh cục bộ mà HEAD được trỏ đến. Khi dữ liệu được tải xuống, Git pull sẽ bắt đầu quy trình hợp nhất như Git merge. Một merge commit mới sẽ được tạo và HEAD cũng được cập nhập để trỏ đến merge commit đó.
![image](https://github.com/Nan27Hid/VersionControlSystem/assets/135946173/88024b3a-5149-495c-97dc-5d4454e04fcf)

## 6. Giải quyết xung đột với Remote Repository
- Như đã học ở bài học trước, khi thực hiện merge, Git sẽ tích hợp tự động những chỗ thay đổi. Tuy nhiên, cũng có những trường hợp không thể tích hợp tự động được. Đó là những trường hợp đã thay đổi ở nơi giống nhau trong file trên Remote Repository và Local Repository. Trường hợp này, vì nó không thể tự phán đoán được lấy thay đổi từ bên nào nên sẽ phát sinh lỗi.
- Bạn đã được học cách giải quyết xung đột với Local Repository, bài giảng dưới đây sẽ chỉ cho bạn cách giải quyết xung đột này với Remote Repository.

## 7. Rebasing khi lấy các thay đổi
- Rebasing là một quy trình để áp dụng lại các commit trên một nhánh nào đó. Nó được sử dụng để áp dụng một chuỗi các commit từ các nhánh khác nhau thành một commit cuối cùng. Về cơ bản, nó là một thay thế của lệnh hợp nhất git, một quá trình hợp nhất tuyến tính. Vậy sẽ thế nào nếu bạn Rebasing khi sử dụng lệnh Pull để lấy các thay đổi từ Remote Repository.

## 8. Clone một bản sao dự án từ Remote Repository
- Một khái niệm quan trọng khác mà bạn cần biết là Clone sao chép. Lệnh Git clone được dùng để sao chép, copy một Git Repository về máy tính cá nhân (Local Repository).
- Một số trường hợp sử dụng git clone như:
- Sao chép một dự án từ Remote Repository về Local Repository
- Sao chép một dự án từ một Url (https) (ví dụ: Github, Gitlab)
- Lưu ý: Khi sao chép Repo bình thường thì nó tự động tạo ra kết nối đến remote Repo, để có Push, keyes nối này có tên mặc định origin.

## 9. Merge Request
- Trong khi bạn làm việc với Git, việc tạo các branch tách ra để thực hiện công việc, sau đó gộp vào nhánh chính (master) thay vì nhặt từng commit chính là Merge. Trong bài giảng này bạn sẽ học về việc gộp nhánh bằng cách tạo Merge Request.
**Ưu điểm:**
- Giao diện UI của chức năng Merge Request trên GitLab rất dễ dàng thao tác hơn so với màn hình viết câu lệnh của Terminal.
![image](https://github.com/Nan27Hid/VersionControlSystem/assets/135946173/8dfaf7ac-4b9b-4499-8da4-edde891ea962)
- Hơn nữa khi một tính năng, code được thêm vào thông qua Merge Request bạn sẽ nhìn thấy các phần code đã chỉnh sửa. Điều này là vô cùng quan trọng. Nếu bạn quan sát từng commit riêng lẻ thì rất khó để nắm được tổng thể những gì đã cập nhật cho một tính năng. Với Merge Request thì bạn nhìn thấy rất rõ ràng và có thể dễ dàng ra quyết định phần nào là cần thiết hay không cần thiết.