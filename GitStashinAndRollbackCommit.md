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
    >or
    >git stash save --include-untracked
