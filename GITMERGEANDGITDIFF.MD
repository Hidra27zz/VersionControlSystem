# 3. GIT MERGE AND GIT DIFF

## GIT MERGE
- Git Merge là một lệnh dùng để hợp nhất các chi nhánh độc lập thành một nhánh duy nhất trong Git. Khi sd lệnh hợp nhất trong Git, chỉ có nhánh hiện tại được cập nhật để phản ánh sự hợp nhất, còn nhánh đích sẽ không bị ảnh hưởng. Điều này đồng nghĩa với việc, Git Merge thường được sd kết hợp với Git Checkout để chọn nhánh hiện tại và Git Branch để xóa nhánh nguồn đã lỗi thời.

1. Cách thức hoạt động của Git Merge
- Công dụng chính của lệnh Git Merge là hợp nhất 2 nhánh. Hơn thế, nó còn được dùng để hợp nhất chuỗi commit (cam kết) thành một lịch sử thống nhất.
- Trong hình minh họa dưới, ta có một mẫu hợp nhất nhánh, Git Merge sẽ lấy hai nhánh và tìm thấy một commit cơ sở chung, nó sẽ tạo một cam kết hợp nhất (merge commit) mới và hợp nhất các thay đổi theo trình tự của mỗi cam kết hợp nhất. Ở đây, chúng ta sẽ có 2 nhánh: nhánh master và nhánh stage, và nhánh stage sẽ được hợp nhất với nhánh master.

![image](https://github.com/Nan27Hid/VersionControlSystem/assets/135946173/2df57f61-728d-4f7d-a66b-578359a4b7f4)

2. Rebasing commit
- Rebasing là một quy trình để áp dụng lại các commit trên một nhánh nào đó. Nó được sử dụng để áp dụng một chuỗi các commit từ các nhánh khác nhau thành một commit cuối cùng. Về cơ bản, nó là một thay thế của lệnh hợp nhất. Hợp nhất luôn là một bản ghi thay đổi về phía trước.
- 
