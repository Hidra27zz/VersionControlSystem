# 2. CÁC LỆNH GIT CƠ BẢN

## 1. GIT REPO
- Trong một dự án thực tế, bạn sẽ viết code chung với team của mình. Khi đó việc theo dõi các thay đổi, xem ai đã thực hiện phần code đó và có thể lấy lại phần code trước khi thay đổi là vô cùng quan trọng. Tuyệt vời thay một repository Git là tất cả những gì bạn cần
- Một **Repository Git** là một lưu trữ ảo của dự án của bạn. Nó cho phép bạn lưu các phiên bản code trong dự án của mình và bạn có thể truy cập khi cần. 

how to create a Git repository
- git --version 
=> if it appear a current gate version u can continue
=> if you don't see your current version, if you see an error or anything else, it typically means You don't have it installed. please install it a gain and try one more time.

- git offers a better way of keeping track of the changes by using repositories
- a repository is a place that stores sth, a git repository stores, files and keeps track of any changes.

first: i'm going to use the comment make directory and my directory will be called my cool website. will write it in terminal (" mkdir name_repo "). this struture has been created now the next step is to change the dicrectory and go inside that folder.

second: i use (" cd name_repo") to change directory of the file and go inside that folder.
third: git init file
fourth: git status
fifth: git config --global user.name "NAME in GITHUB"
sixth: git config --global use.email name email create Github
seventh: git commit
eighth: code (vim ten.kieu su dung:x thoat)
nineth: ls -a
tenth: git init
eleventh: git add 
twelfth: git commit -m ""
thirdteenth: git remot ...
forteenth: git push -u origin ... 

git add
this is a secondary stage where we prepare the changes that are about to committed.
so it goes through this changes as follows. First of all, we have made some changes to the folder by default. There are not part of the committed. and then we transition those changes into this stage. and this stage is called the staging area and it's a stage before we actually commit sth and this is the next step. after that we cant commit this and there's a reason for this two step process. which i will explain in one of the upcoming lectures. But for the moment, let's just get this commited ready
![z4423071868561_be37c2b350d01f76206425dfe10d1b36](https://github.com/Nan27Hid/GitHup/assets/135946173/481caa70-ee55-48e7-a541-866fe50c65c0)


- nếu có 2 file bạn chỉ cần git init và git add, git commit -m một file còn file còn lại chỉ cần git add .

## 2. GIT COMMIT
- **Git commit** là cam kết trong trong Git, được dùng để lưu lại những thay đổi trong repository. Có thể hiểu rằng nó như một ảnh chụp nhanh (snapshot). Các ảnh Snapshot đã cam kết (commit) được coi là một phiên bản code "an toàn" của dự án vì Git luôn hỏi mỗi khi có người muốn thay đổi chúng.
- Hãy nhớ rằng, trước khi bắt đầu lệnh Git Commit, lệnh Git Add sẽ được chạy để thục đẩy các thay đổi của dự án mà sau đó nó sẽ được lưu trữ trong một cam kết.
- Tóm lại, Commit là những bức ảnh chụp nhanh của dự án. Mọi Commit đều được ghi lại trong nhánh chính của repository. Hai commit khác nhau sẽ không bao giờ ghi đè vì mỗi commit đều có 1 ID riêng.

câu lệnh mẫu:
- git add readme.md
- git commit -m "first commit"

## 3. GIT STAGING
- Như ta đã biết ở phần trước thì Git đã có 3 khu làm việc chính: trên máy tính cá nhân, trên kho chứa mã nguồn (repository) và khu vực trung gian (staging area). Staging area là khu vực sẽ lưu trữ những thay đổi của bạn trên file để nó có thể commit được, vì muốn commit được thì tệp tin của bạn phải nằm trong Staging area.
- Bạn sẽ dùng 2 lệnh sau để lưu trữ tất cả những thay đổi trên file vào Staging area.
  - git add -all
  - git add

## 4. COMMIT MỘT THƯ MỤC
- Có một trường hợp nữa về các commit mà bạn cần lưu ý là khi bạn tạo một folder mới rồi sau đó kiểm tra bằng lệnh "git status" thì bạn sẽ nhận được thông báo như sau:

    ![3 2 4](https://github.com/Nan27Hid/GitHup/assets/135946173/2b1b36c1-4171-4033-8d12-ff954525b079)

- Và lý do cho thông báo này Git chỉ theo dõi các tệp tin (flile) chứ không theo dõi thư mục  (Folder). Nhưng nó không có nghĩa là bạn không thể thao tác các thư mục và tổ chức dự án của mình, nếu các thư mục (Folder) của bạn có chứa tệp tin hay một nội dung bất kì thì nó vẫn sẽ được Git theo dõi và có thể xem khi cần thiết.
- Tuy nhiên, nếu vì bất kỳ lý do nào đó bạn muốn  Git theo dõi một Folder dù nó không chứa bất kỳ nội dung nào thì bạn có thể sử dụng cách sau: về cơ bản, bạn sẽ chèn một tệp trống và tên của nó sẽ bắt đầu với dấy chấm. (VD: .gitkeep)
          touch temp/.gitkeep

- Bằng cách này thì sau khi bạn kiểm tra bằng git status bạn sẽ thấy Git của bạn đã theo dõi file temp này dù rằng nó không có nội dung.

## 5. XÓA FILE
- Đây là một hành động rất thường xuyên trong quy trình sử dụng Git của các bạn, hãy tưởng tượng một lúc nào đó bạn thấy một file trong project của bạn quá thừa thãi và muốn xóa nó đi. Tuy nhiên, xóa file trên máy tính các nhân bạn thì đơn giản, nhưng nếu bạn đã commit nó lên repository rồi thì sẽ phải làm thế nào ?


## 6. TỆP TIN .GITGNORE
- **gitgnore** là file có tên là .gitgnore do Git quy định. Nhiệm vụ của nó là liệt kê những file tồn tại nhưng bạn không mong muốn cho vào git repository  (repository git) Bạn hãy hiểu nôm na là Git sẽ bỏ qua mà khoogn commit những file đã được ghi trong .gitgnore.

Cách thức hoạt động của Gitgnore:
- Hiểu đơn giản là git sẽ bỏ qua file hoặc một tập các file bạn thấy không cần thiết trong dự án của chúng ta khi commit và push lên repository. VD:
- Các file mà IDE tự sinh ra trong quy trình xây project => điều này tránh gây tốn tài nguyên server lưu trữ project
- các file cấu hình đường dẫn trên máy tính cá nhân người viết code => gây ra việc không build được project khi chạy ở máy ở máy các thành viên khác
- các file cần giữ kín trong nội bộ nếu repository của bạn ở chế độ public (công khai) => bảo mật

- Git quả lý các file mà bạn muốn không commit bằng file .gitgnore được đặt trong thư mục gốc (root). Mỗi khi bạn add 1 file mới vô git, git sẽ kiểm tra danh sách những file nằm trong .gitgnore và không thêm chúng vào git.

## 7. GIT BRANCHES
- Branch là một bản sao của một project Git mà tại đó bạn có thể thay đổi bất cứ khi nào và sau đó kết hợp với project gốc. Các hoạt động trên mỗi branch là riêng biệt, không gây bất kỳ ảnh hưởng nào đến cách branch khác nên có thể tiến hành thay đổi đồng thời trên một repository. Trong bài giảng này bạn sẽ học cách tạo một nhánh mới.
- Bạn sẽ tạo một nhánh (branch) mới với câu lệnh:
- 