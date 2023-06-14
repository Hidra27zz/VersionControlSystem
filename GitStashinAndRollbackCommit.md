# 4. GIT STASHING AND ROLLBACK COMMIT
## GIT STASHING
- Đây là một câu lệnh khá thú vị trong Git. Hãy tưởng tượng nhé, khi bạn đang thực hiện code trên Git, đột nhiên xuất hiện một vấn đề ở phần Workload cũ khiến bạn phải tạm dừng công việc hiện tại để quay lại sửa gấp. Bạn có thể tạo một branch mới để bắt tay vào việc sửa chữa vấn đề ở workload cũ. Với phần việc còn đang dang dở của mình, bạn sẽ có 2 lựa chọn.
  - Chạy git reset --hard để loại bỏ những thay đổi đã được commit của bạn.
  - Ghi lại công việc chưa hoàn tất của bạn như một commit mới. 
- Cả 2 giải pháp có vẻ điều không được chu toàn lắm. Cái đầu tiên làm mất tất cả những thứ bạn đã làm, trong khi cái sau lại tạo ra một commit vô nghĩa.
- Đây là lúc mà lệnh Git stash phát huy tác dụng. Hãy nghĩ thế này, Git stash sẽ có tác dụng giống câu lệnh git reset --hard, nó cho bạn một branch sạch sẽ, nhưng cũng sẽ ghi lại các thay đổi về code, file mà bạn vừa làm việc. Sau đó, khi bạn muốn bắt đầu công việc, bạn có thể tái áp dụng những thay đổi này và tiếp tục công việc còn dang dở. Git stash giống như một nút "tạm dừng" cho tiến trình công việc của bạn.
![image](https://github.com/Nan27Hid/VersionControlSystem/assets/135946173/0453d784-07de-4b40-9f0c-1b15ea9a9c39)
- Dưới đây là một vài lệnh git stash mà bạn cần biết:

### 1. Git Stash save
- Cả Git stash hay Git stash save đều có cùng một cơ chế. Git sẽ tạo ra một commit khi bạn sử dụng 1 trong 2 lệnh nó được lưu trữ lại trong repo của bạn.
- Git Stash cùng với một tin nhắn đi kèm.
    >git stash save "Toi dang Code cai gi the nay"
- Git Stash loại bỏ những files không được theo dõi.
    >git stash save -u
     or
     git stash save --include-untracked

### 2. Git stash list
- Lệnh này giúp bạn có thể xem danh sách stash đã tạo.
    >git stash list
- Ta sẽ được kết quả:
    >stash@{0}: WIP on master: 4e22905 abc 1865891265912
     stash@{1}: On master: Toi dang Code cai gi the nay
     (END)
- Đây là danh sách các stashes mà bạn tạo ra, và cái gần nhất bạn tạo sẽ ở trên đầu.

### 3. Git stash apply
- Lệnh này cơ bản là sẽ lấy stash cuối cùng để apply vào code vào code của bạn.
    >git stash apply
- Bạn cũng có thể apply một stash khác bằng cách thêm ID vào sau câu lệnh trên.
    >git stash apply stash@{1}


### 4. Git stash pop
- Về cơ bản thì câu lệnh này có tác dụng y hệt câu lệnh Git apply. Có điều là sau khi apply vào code thì sẽ xóa stash đó khỏi danh sách stash của bạn luôn. Cũng tương tự nếu bạn không muốn apply stash gần nhất mà một stash trước đó thì bạn chỉ cần thêm ID của nó vào sau câu lệnh.

    >git stash pop stash@{1}          

### 5. Git stash show
- Lệnh này sẽ hiển thị ngắn gọn những thay đổi của stash cuối cùng.
    >git stash show           

- Nếu bạn muốn xem toàn bộ những thay đổi thì chỉ cần thêm -p vào sau câu lệnh.
    >git stash show -p

Tương tự nếu bạn muốn xem thay đổi của các stash trước thì chỉ cần thêm ID vào sau câu lệnh.
    >git stash show stash@{1}    

### 6. Git stash branch `<name>`
- Tạo một branch mới với những thay đổi tương ứng trong stash gần nhất. Câu lệnh này đồng thời cũng xóa nó khỏi stash list như Git stash pop.
    >git stash branch branch-draff      

Tương tự, nếu bạn muốn một stash cụ thể thì thêm ID vào sau câu lệnh.
    >git stash branch branch -draff stash@{1}

### 7. Git stash clear
- Xóa toàn bộ stash bạn lưu trữ trong repo. Lưu ý rằng bạn không thể revert (quay trở lại) lúc chưa xóa nên hãy cẩn thận nhé.
    >git stash clear

### 8. Git stash drop
- Câu lệnh này giúp bạn xóa stash mà bạn thấy không cần thiết.
    >git stash drop

- Xóa stash cụ thể:                   
    >git stash drop stash@{1}

## Rollback Commit 
- Lịch sử commit của Git được thiết kế để không thay đổi và theo dõi mọi sự thay đổi trong dự án mà bạn đang làm. Tuy nhiên, có những lúc bạn sẽ nhận ra rằng mình vừa viết những dòng code sai và ngớ ngẩn. Trong quá trình phát triển phần mềm, việc phải rollback một số commit bị lỗi là không thể tránh khỏi. Vậy có cách nào để có thể hoàn tác các thay đổi như đưa file trở về commit trước đó, chuyển đổi giữa các nhánh trong kho lưu trữ….Ở phần này chúng ta sẽ tìm hiểu về các câu lệnh Git hỗ trợ ta làm những điều đó nhé.
- Câu lệnh git checkout được sinh ra nhằm giúp người dùng di chuyển giữa các branch hoặc để phục hồi file trong thư mục làm việc từ một commit trước đây.

### 1. Chuyển nhánh
- Giả sử bạn đang ở một branch nào đó và muốn di chuyển sang nhánh master thì câu lệnh mà bạn cần thực hiện là:
    >git checkout master

- Lúc này nhánh master hoạt động, các thư mục làm việc của bạn sẽ là các file tương ứng với branch này (câu lệnh này có tác dụng y hệt câu git switch).

### 2. Phục hồi phiên bản commit cũ
- Tưởng tượng bạn có một file index.html bạn muốn phục hồi nó về phiên bản ở commit có ID là HASH, thì câu lệnh bạn cần thực hiện là:
    >git checkout HASH index.html

- Hay nếu bạn đơm giản chỉ muốn phục hồi nội dung file ở commit trước đó thì là:
    >git checkout index.html

- Vậy nếu bạn muốn thực hiện trở về phiên bản commit cũ với tất cả các file thì sao? Câu lệnh bạn cần sẽ là:
    >git checkout HASH

### 3. Git reset
- Git Reset được dùng để quay về một điểm commit nào đó, đồng thời xóa lịch sử của các commit trước nó.
- Hãy theo dõi ví dụ dưới đây: 
![image](https://github.com/Nan27Hid/VersionControlSystem/assets/135946173/abd1c70d-7352-4e76-9b56-e99600fcee10)

- Giả sử, lịch sử commit của bạn có các điểm commit như trong ảnh (A,B,C,D) tương ứng với các commit_id phía trên. A, B là các commit bình thường; C, D là các commit gặp vấn đề (viết code sai, xóa nhầm file, …). Lúc này bạn hoàn toàn có thể quay trở lại commit B bằng câu lệnh:
    >Git reset --hard a0fvf8
- Sau khi chạy xong câu lệnh trên, ta có kết quả sau:
![image](https://github.com/Nan27Hid/VersionControlSystem/assets/135946173/28b5563a-5c10-45c2-820a-02a46ab37837)

- Như bạn đang thấy, con trỏ HEAD đang trỏ đến vị trí của commit B, đồng thời lịch sử commit C và D cũng biến mất, giống như bạn chưa từng thực hiện 2 commit đó vậy. Lịch sử commit của bạn cũng trông sạch sẽ và gọn gàng hơn nhiều. Tuy nhiên, các thay đổi này mới chỉ đang diễn ra trên local repository, để cập nhật thay đổi này lên remote repository bạn cần thực hiện lệnh:
    >Git push -f

**3 hình thức của Git reset:**
- Tùy thuộc vào hoàn cảnh cũng như mục đích mà chúng ta cần reset với các chế độ khác nhau, do vậy git cung cấp cho ta 3 lựa chọn đi kèm là:** --soft, --hard, --mixed**
  - **Git reset `<commit_id>`** di chuyển con trỏ **HEAD** về vị trí commit reset và vẫn giữ nguyên tất cả các thay đổi của file, nhưng sẽ loại bỏ các thay đổi khỏng staging area.
  - **Git reset –soft `<commit_id>`** chỉ di chuyển **HEAD** về vị trí commit. **Trạng thái của staging area và tất cả các thay đổi của file được giữ nguyên.**
  - **Git reset –hard`<commit_id>`** di chuyển con trỏ HEAD về vị trí commit reset **và loại bỏ tất cả các thay đổi của file.**

### 4. Git revert
- **Git revert** cũng giúp cho bạn có thể quay trở lại commit trước. Tuy nhiên **Git revert** không làm mất các commit, thay vào đó sẽ tạo thêm commit mới có nội dung giống hệt với commit bạn muốn quay trở về.
![image](https://github.com/Nan27Hid/VersionControlSystem/assets/135946173/fb741aad-f8f9-4bac-a0ea-3f38540919c2)

- Tương tự như với **Git Reset**, điều chúng ta cần thực hiện là **revert về commit D**, rồi tiếp tục **revert về commit C**.
    >git revert 5lk4er
     git revert 76sdeb

- Kết quả sau khi chạy 2 lệnh trên là:
![image](https://github.com/Nan27Hid/VersionControlSystem/assets/135946173/8684325a-558d-4e0b-87e8-9c23f1c7ec33)

- Ở đây, ta sẽ thấy rằng có thêm 2 commit mới D’ và C’ được tạo ra.
- Tóm lại, git reset thì xóa lịch sử commit giúp lịch sử trông gọn gàng hơn, còn git revert sẽ tạo ra thêm commit mới đồng thời giữ lại lịch sử commit trước đó.
