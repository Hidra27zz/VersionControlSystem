# 1. Giới thiệu về Version Control System (VCS) and Git

## VSC

- Khi code, sẽ có lúc lỡ tay xóa một đoạn code vì nghĩ rằng nó không phù hợp nữa, nhưng sau đó phát hiện là đoạn code đó vẫn cần sd. bạn nghĩ rằng mình có thể nhớ chính xác những gì mình đã viết ko ? thật sự rất khó. nhưng nếu bạn có dùng phần mềm quản lý phiên mã nguồn (VERSion CONTROL SYSTEM) thì mội việc sẽ trở nên đơn giản hơn rất nhiều vì phần mềm quản lí phiên bản mã nguồn sữ cho phép bạn dễ dàng quay lại một phiên bản trước của tập tin đó.

- Hình ảnh dưới đây là một vài nhà lập trình quản lý phiên bản bằng cách copy các file sang một thư mục khác (thư mục được cài đặt theo thời gian hoặc lượt Backup). Đây là pp rất phổ biến ở thời kỳ trước bởi vì nó đơn giản, tuy nhiên cũng rất dễ gây ra lỗi trong quá trình hoàng thành dự án. Bạn sẽ rất dễ quên rằng mình đang viết code ở thư mục nào hay vô tình sửa, sao chép nhầm file mà bạn không mong muốn. Cuối cùng, trước mắt bạn sẽ là một mớ hỗn độn và bạn không biết phải bắt đầu từ đâu.
![3 1 1](https://github.com/Nan27Hid/VersionControlSystem/assets/135946173/0debc98a-bc78-4ded-b0ee-dde5183e34ac)

- Để giải quyết vấn đề này thì các phiên bản VCS đã ra đời. Với VCS bạn sẽ dễ dàng quản lí thư mục, code của mình và sửa lỗi khi có sự cố.**VERSION CONTROL SYSTEM** là hệ thống kiểm soát các phiên bản phân tán mã nguồn mở. VCS sẽ lưu trữ tất cả cả file trong toàn bộ dự án và ghi lại toàn bộ lịch sử thay đổi của file. Mỗi sự thay đổi sẽ được lưu thành một version (phiên bản) hoàn toàn mới. Một trong số những VCS thông dụng nhất là Git.

TÁC DỤNG CỦA VCS:

- Lưu lại lịch sử các version của bất kỳ thay đổi nào của dự án, giúp xem lại các sự thay đổi hoặc khôi phục (revert) lại sau này.
- việc chia sẻ code trở nên dễ dàng hơn, lập trình viên public cho bất kì ai, hoặc private chỉ cho một số người có thẩm quyền có thể truy cập và lấy code về.

## GIT

- GIT  là một hệ thống quản lý phiên bản phân tán (Distributed Version Control System - DVCS) ra đời vào năm 2005 và hiện được dùng rất phổ biến. So với các hệ thống quản lý phiên bản tập trung khi tất cả mã nguồn và lịch sử thay đổi chỉ được lưu một nơi là máy chủ thì trong hệ thống phân tán, các máy khách không chỉ "checkout" phiên bản mới nhất của các tập tin mà là sao chép (mirror) toàn bộ kho mã nguồn (repository). Như vậy, nếu như máy chủ ngừng hoạt động, thì bạn hoàn toàn có thể lấy kho chứa từ bất kỳ máy khách nào để sao chép ngược lại máy chủ để khôi phục lại toàn bộ hệ thống. Mỗi checkout thực sự là một bản sao đẩy đủ của tất cả dữ liệu của kho chứa từ máy chủ.

![3 1 2 1](https://github.com/Nan27Hid/VersionControlSystem/assets/135946173/a603f04b-b85b-4eec-a5b3-3544435e1181)

- Sự khác nhau cơ bản giữa Git với bất kỳ VCS khác về cơ bản là Git coi dữ liệu của nó như một tập hợp các "ảnh" (snapshot) của một hệ thống tập tin. Mỗi lần bạn thực hiện hành động "commit", hoặc lưu lại trạng thái hiện tại của dự án trong GIT. Về cơ bản, Git "chụp một bức ảnh" ghi lại nội dung của toàn bộ tập tin tại thời điểm đó và tạo ra một tham chiếu. Thậm chí, để không lãng phí tài nguyên, nếu tập tin của bạn không có sự thay đổi nào, GIT sẽ không lưu trữ tập tin đó lại một lần nữa mà chỉ tạo một liên kết với tập tin gốc đã tồn tại trước đó.
- Hình ảnh bên dưới là cách mà GIT thao tác với dữ liệu:

![3 1 2 2](https://github.com/Nan27Hid/GitHup/assets/135946173/b1af20eb-7093-4f63-b7d8-c883322a4bf0)

- MỘT SỐ ƯU ĐIỂM CỦA GIT SO VỚI CÁC VCS KHÁC:
  - Nhanh
  - Thiết kế đơn giản
  - Hỗ trợ "phát triển phi tuyến tính"
  - Phân tán toàn diện
  - Có khả năng xử lý các dự án hiệu quả

- Hơn nữa phần lớn các **thao tác của GIT diễn ra cục bộ.** Bạn hoàn toàn có thể làm việc với Git khi không có kết nối Internet. Bất kể bạn có ngồi trên máy bay hay tàu, bạn hoàn toàn có thể xem lịch sử, viết code, commit bình thường cho tới khi có kết nối Internet để đồng bộ hóa. Trong rất nhiều hệ thống khác, việc này gần như không thể hoặc khó khăn.

## GIT FLOW

- **Ba trạng thái -** Đây là điều vô cùng quan trọng về Git nếu bạn muốn sử dụng một cách thành thạo sau này. Mỗi tập tin trong Git được quản lý dựa trên ba trạng thái: Modified, Stager, Committed.

  - **Modified:** Đây là trạng thái khi bạn đã thay đổi code, tập tin nhưng chưa commit vào cơ sở dữ liệu. Ở trạng thái này, các tệp của bạn được sửa đổi. Bạn tạo tệp, viết mã, sửa tệp, xóa tệp nhưng các thay đổi không được lưu, bạn vẫn chưa để Git giám sát các tệp này. VD: Bạn chụp một số hình ảnh để đưa vào album ảnh của mình nhưng bạn chưa dán nó vào album của mình, bạn vần còn quyền lọc, sửa các bức ảnh.
  - **Stager:** Trạng thái này là khi bạn đã đánh dấu sẽ commit phiên bản hiện tại của một tập tin đã chỉnh sửa trong lần commit sắp tới. Ở trạng thái này, các tệp của bạn được chuẩn bị để được cam kết trong kho lưu trữ git (.git repository). Các tệp này chưa được cam kết (commit) nhưng đã ủy quyền cho git để commit phiên bản này trong lần commit tiếp theo. VD: Bạn đã lọc ra những hình ảnh mà bạn muốn đưa vào album và đã in chúng ảnh cứng. Về cơ bản, bạn đang chuẩn bị những bức ảnh này để dán vào album nhưng bạn chưa dán chúng vào.
  - **Committed:** Đây là trạng thái khi dữ liệu đã được lưu trữ một cách an toàn trong cơ sở dữ liệu. Trong giai đoạn cuối cùng này, bạn đã lưu thành công các tệp trong kho lưu trữ git (repository) và cam kết (commit) cho chúng. Bạn có thể đặt tên cho commit ok để bạn hoặc những người trong team có thể hiểu rằng lần commit đó là về vấn đề gì, xử lí việc gì. VD: lúc này bạn đã có những bức ảnh mà bạn ưng ý, bạn dán những bức ảnh đó vào album và thêm một số thông điệp, tiêu đề mô tả thời điểm của sự kiện liên quan đến bức ảnh.

Điều này tạo ra 3 phần riêng biệt của một dự án sử dụng Git: thư mục làm việc (Working directory), khu vực tổ chức (Staging area), Git directory (Repository):

![3 1 3](https://github.com/Nan27Hid/GitHup/assets/135946173/47fedd85-73c9-437d-886a-98c7cc31f5b8)

**File Locations:**  đối với các trạng thái khác nhau, vị trí lưu trữ của chúng sẽ khác nhau. Ở phần này, ta sẽ thảo luận về quy trình làm việc hoàn chỉnh dựa trên các trạng thái và vị trí tệp lưu trữ chúng.

- **Working directory:** là bản sao một phiên bản của dự án. Những tập tin này được kéo về (pulled) từ cơ sở dữ liệu được nén lại trong thư mục Git và lưu trên ổ cứng cho bạn sử dụng hoặc chỉnh sửa. Hoặc khi bạn tạo bất kỳ thư mục nào trong dự án của mình, thư mục đó sẽ nằm trong thư mục làm việc (Working Directory) hoặc trong thư mục cục bộ. Về cơ bản Working Directory là thư mục cục bộ trên máy tính cá nhân cho các tệp dự án của bạn.
- **Staging area**: là một tập tin chứa trong thư mục Git, nó chứa thông tin về những gì sẽ được commit trong lần commit sắp tới.
- **Git directoty (repository):**  Đây là nơi mà các tệp đã ở trạng thái commit nằm. Nó lưu trữ các “siêu dữ kiện” (metadata) và cơ sở dữ liệu cho dự án của bạn. Đồng thời nó là phần được sao lưu về khi bạn tạo một bản sao (clone) của một repository.

## Tiến hành công việc (Workflow) cơ bản của Git mà bạn thực hiện được sẽ là

- Bạn thay đổi các tập tin trong Working Directory.
- Bạn tổ chức các tập tin, tạo mới một ảnh (snapshot) vào Staging area.
- Bạn commit, ảnh (Snapshot) của các tập tin trong Staging area sẽ được vĩnh viễn vào Git Directory (repository).

![3 1 3 2](https://github.com/Nan27Hid/GitHup/assets/135946173/d6dea994-ee92-486a-bb82-724b1c8eee63)

Dưới đây là liệt kê các câu lệnh ứng với quy trình. Tuy nhiên bạn sẽ được học các câu lệnh ứng với các quy trình kỹ hơn ở các bài giảng tiếp theo.

- **Git add:** đưa code, thư mục hiện tại vào Staging area, xác định phiên bản sẽ được commit trong lần commit tiếp theo.
- **Git commit:** Cam kết phiên bản trong Staging Area.
- **Git push:** đưa code, thư mục từ Git Directory (repository) đến repository từ xa (remote repository).
- **Git fetch:** Nhận các tệp từ repository từ xa (remote repository) đến kho lưu trữ cục bộ (local repository) nhưng chưa đến working directory của bạn.
- **Git merge**: Tải tệp được cập nhật từ kho lưu trữ cục bộ (local repository) đến working directory của bạn.
- **Git pull**: Đây là sự kết hợp và rút ngắn của 2 câu lệnh trên. Nó sẽ đưa trực tiếp đến các tẹp từ repository từ xa (remote repository) đến working area của bạn.
=> git fetch + git merge = git pull
- **Git diff HEAD:** nếu bạn thắc mắc tại sao phải sử dụng 2 lệnh git fetch, git merge trong khi có thể rút gọn thời gian bằng git pull, thì đó là ví có những lúc ta sẽ cần sử dụng git diff HEAD để kiểm tra sự khác biệt giữa các tệp tồn tại trong Working Directory và các tệp nằm trong kho lưu trữ cục bộ (local repository).
- **Git diff:** So sánh cho bạn biết sự khác biệt giữa các tệp trong Working Directory và các tệp nằm trong Staging Area chuẩn bị được commit.
