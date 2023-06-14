# 3. GIT MERGE AND GIT DIFF

## GIT MERGE
- Git Merge là một lệnh dùng để hợp nhất các chi nhánh độc lập thành một nhánh duy nhất trong Git. Khi sd lệnh hợp nhất trong Git, chỉ có nhánh hiện tại được cập nhật để phản ánh sự hợp nhất, còn nhánh đích sẽ không bị ảnh hưởng. Điều này đồng nghĩa với việc, Git Merge thường được sd kết hợp với Git Checkout để chọn nhánh hiện tại và Git Branch để xóa nhánh nguồn đã lỗi thời.

1. Cách thức hoạt động của Git Merge
- Công dụng chính của lệnh Git Merge là hợp nhất 2 nhánh. Hơn thế, nó còn được dùng để hợp nhất chuỗi commit (cam kết) thành một lịch sử thống nhất.
- Trong hình minh họa dưới, ta có một mẫu hợp nhất nhánh, Git Merge sẽ lấy hai nhánh và tìm thấy một commit cơ sở chung, nó sẽ tạo một cam kết hợp nhất (merge commit) mới và hợp nhất các thay đổi theo trình tự của mỗi cam kết hợp nhất. Ở đây, chúng ta sẽ có 2 nhánh: nhánh master và nhánh stage, và nhánh stage sẽ được hợp nhất với nhánh master.

![image](https://github.com/Nan27Hid/VersionControlSystem/assets/135946173/2df57f61-728d-4f7d-a66b-578359a4b7f4)

2. Rebasing commit
- Rebasing là một quy trình để áp dụng lại các commit trên một nhánh nào đó. Nó được sử dụng để áp dụng một chuỗi các commit từ các nhánh khác nhau thành một commit cuối cùng. Về cơ bản, nó là một thay thế của lệnh hợp nhất Git, một quá trình hợp nhất tuyến tính.
- Có thể hiểu rằng lệnh Rebase là một thay thế của lệnh hợp nhất. Hợp nhất luôn là một bản ghi thay đổi về phía trước.

![image](https://github.com/Nan27Hid/VersionControlSystem/assets/135946173/8601e9db-bc9c-4509-addb-0ca006f19109)

- Hình ảnh trên mô tả cách hoạt động của Git Rebase. Ba commit của nhánh chính được hợp nhất tuyến tính, chứ không bị đè lên nhau với các commit của nhánh phụ (nhánh Test).
- Giả sử bạn đã thực hiện 3 lần commit trong nhánh chính (Master) và 3 lần trong nhánh phụ (nhánh Test). Nếu bạn hợp nhất bằng lệnh merge thì nó sẽ hợp nhất tất cả commit đó trong một thời gian. Nhưng nếu bạn rebase lại nó, thì nó sẽ được hợp nhất theo cách tuyến tính.

# 3. Xử lý xung đột khi Git Merge
- Trước hết ta cần hiểu xung đột khi Git Merge là gì và khi nào thì xung đột này xảy ra.
- Khi bạn muốn hợp nhất hai nhánh và phần giống nhau của cùng một tệp bị thay đổi, xung đột hợp nhất xảy ra. Nguyên nhân là do Git không tìm ra phiên nào sẽ được sử dụng. Khi điều này xảy ra, Git sẽ dừng trước khi commit hợp nhất nhằm giải quyết xung đột đó.
- Lưu ý rằng xung đột Git Merge chỉ xảy ra trong trường hợp nhất 3 chiều. Thông thường, Git sử dụng quy trình edit/stage/commit để giải quyết xung đột này. Việc chạy Git status sẽ giải quyết việc này bằng cách hiển thị các tệp cần được giải quyết.

![image](https://github.com/Nan27Hid/VersionControlSystem/assets/135946173/efb63717-8cb3-44f9-90c6-e090db4cdd96)

- Trong trường hợp có xung đột xảy ra, Git sẽ chỉnh sửa nội dung của các tệp bị ảnh hưởng bằng cách đánh dấu cả 2 mặt của một nội dung xung đột. Các điểm đánh dấu trực tiếp này là
  - <<<<<<<<<- đánh dấu xung đột, xung đột bắt đầu sau dòng này.
  - =========- phân chia những thay đổi của bạn với những thay đổi trong nhánh khác
  - ">>>>>>>>>" - kết thúc các dòng mâu thuẫn


# GIT DIFF
## 1. Xem các thay đổi với câu lệnh Git Diff
- Git diff là lệnh kiểm tra sự thay đổi giữa thư mục làm việc và commit cuối, giữa index và commit cuối, giữa các nhánh.
- khi nó được thực thi, nó sẽ chạy một chức năng khác trên các nguồn dữ liệu Git. Các nguồn sữ liệu này có thể là file, branch, commit và hơn thế. Nó được sử dụng để hiển thị các thay đổi giữa các commit, commit và cây làm việc,...
- Câu lệnh mẫu: git diff --`<lệnh tương ứng>`

## 2. Các trường hợp sử dụng Git Diff.
**Trường hợp 1: theo dõi những thay đổi chua được đưa vào staging area**
- Việc sử dụng thông thường của lệnh Git diff mà chúng ta cso thể theo dõi các thay đổi chưa được đưa vào staging area.
- Giả sử chúng ta đã chỉnh sửa file newfile1.txt. Bây giờ, chúng ta muốn theo dõi những thay đổi nào chưa được thực hiện. Sau đó, chúng ta có thể làm như vậy từ lệnh Git diff, hãy quan sát đầu ra dưới đây:

![image](https://github.com/Nan27Hid/VersionControlSystem/assets/135946173/3e5915e8-3d35-4b2a-b679-d50802c0d56a)

- Từ kết quả trên, ta có thể thấy rằng các thay đổi thực hiện trên newfile1.txt được hiển thị bằng lệnh git diff. Như chúng ta đã chỉnh sửa nó là "các thay đổi được thực". Vì vậy, đầu ra đang hiển thị những thay đổi với nội dung của nó. Phần được đánh dấu của kết quả ở ảnh trên là những thay đổi trong file được cập nhật. Bây giờ, chúng ta có thể quyết định xem chúng ta có muốn phân loại đoạn file đó hay không bằng cách xem trước các thay đổi.

**Trường hợp 2: Theo dõi những thay đổi đã diễn ra nhưng không được commit**
- Lệnh Git Diff cho phép chúng ta theo dõi các thay đổi được thực hiện nhưng không được commit. Chúng ta có thể theo dõi nhưng thay đổi trong staging area. Hãy sử dụng tùy chọn -staged cùng lệnh Git diff.
- Để kiểm tra file chưa được theo dõi, hãy chạy lệnh git status như sau:
    - git status

- Lệnh trên sẽ hiển thị file chưa được theo dõi từ kho lưu trữ. Bây giờ, chúng ta sẽ thêm nso vào staging area. Để thêm file vào staging area, hãy chạy lệnh git add dưới dạng;
   - git add `<ten file>`

- Lệnh trên sẽ thêm file vào staging area
![image](https://github.com/Nan27Hid/VersionControlSystem/assets/135946173/3a06b1cd-abe0-4440-9505-c3e588225f25)

- Bây giờ, file đã được thêm vào staging area, nhưng nó vẫn chưa được commit. Vì thế, chúng ta cũng có thể theo dõi những thay đổi trong staging area. Để kiểm tra thay đổi theo các giai đoạn, hãy chạy lệnh Git diff cũng với tùy chọn -staged.
  - >git diff --staged

- Lệnh trên sẽ hiển thị các thay đổi của các file đã đưa vào staging area.

![image](https://github.com/Nan27Hid/VersionControlSystem/assets/135946173/c93964e3-68a0-44a6-9737-d6071d949407)

- đầu ra trên hiển thị các thay đổi của newfile1.txt đã được đưa vào staging area.

**Trường hợp 3: Theo dõi các thay đổi sau khi commit một file**
- Lệnh Git Diff cũng cho phép chúng ta theo dõi những thay đổi sau khi commit một file. Giả sử chúng ta đã commit một file trên repository và thực hiện một số thay đổi về code sau khi commit. Chúng ta hoàn toàn có thể theo dõi file trong giai đoạn này.
- Trong đầu ra bên dưới, ta đã commit những thay đổi mà chúng ta đã thực hiện trên newfile1.txt của mình.
![image](https://github.com/Nan27Hid/VersionControlSystem/assets/135946173/379457a2-50ab-4626-81cc-f2ae08f60d44)

- Sau đó, ta sẽ thay đổi một số thứ ở file newfile1.txt. Để theo dõi các thay đổi của file này, hãy chạy git diff với đối với số HEAD.
    >git diff HEAD
- lệnh trên sẽ hiển thị các phần thay đổi, cập nhật của file newfile1.txt trên các phần được đánh dấu.

**Trường hợp 4: Theo dõi những thay đổi hai lần commit**
- Chúng ta có thể theo dõi những thay đổi giữa hai commit khác nhau, dù cho đó là lần commit mới nhất hay lần commit cũ. Nhưng điều bắt buộc cho việc này là chúng ta phải có một danh sách các commit để chúng ta commit để chúng ta so sánh. Lệnh để bạn có thể quan sát liệt kê tất cả các commit gần đây là git log.
    >git log   
- Ví dụ bạn muốn theo dõi thay đổi của một commit trước đó. Ta sẽ cần các commit của file được chỉ định đó. Để làm được điều đó bạn cần chạy lệnh Git log như sau:
    >git log -p --follow - ten file
- Như vậy là bạn đã có tất cả commit của file newfile1.txt, bạn muốn theo dõi giữa 2 commit, lệnh Git diff cho phép theo dõi những thay đổi giữa 2 lần commit sẽ là:
    >git diff `<commit1-sha>` `<commit2-sha>`
- Lệnh trên sẽ hiển thị các thay đổi giữa 2 lần commit:
![image](https://github.com/Nan27Hid/VersionControlSystem/assets/135946173/39c2a025-0b00-42cd-80f8-966655b225a6)

**Trường hợp 5: Theo dõi sự khác biệt giữa 2 branch**
- Giống với theo dõi sự thay đổi giữa 2 lần commit bên trên. Để có thể xem xét sự khác biệt, thay đổi giữa 2 branch, bạn sẽ sử dụng câu lệnh:
    >git diff branch1 branch2
    