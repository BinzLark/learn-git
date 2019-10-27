#Git basic  
git --version để xem version
git -v để xem gợi ý các lệnh
git init để tạo 1 project mới WORKING DIR

CONFIG FOR GIT: trước khi commit chúng ta cần phải config email và name  
git config --global user.email "you@example.com"  
git config --global user.name "Your Name"

I. CÁC LỆNH THƯỜNG DÙNG

1. git init: tạo project với git

2. git status: để kiểm tra tình trạng

- các file có chữ modify: là đã sửa trên file trước đó
- các file untracked là các file mới tạo

3. git add <tenfile>: để thêm file vào STAGING AREA (track) và xóa nó khỏi untrack

- Add nhiều file:

* cach 1: git add . (để thêm tất cả)
* cach 2: git add <tenfile1> <tenfile2> ... <tenfileN>

4. git commit: đóng gói các file track lại thành 1 object có mã id để quản lý trong GIT REPOSYTORY
   ex: git commit -m 'Add README file'

- -m : (message) để thêm mô tả

5. git log: xem lại những gì đã commit

- git log -p : để xem show tất cả các log 1 lần
- git log -2 : để xem log 2 file mới nhất

6. git show <idCommit>: Xem lại nội dung thay đổi nằm trong các file tương ứng đã commit

7. git diff : Xem lại nội dung thay đổi của các file chưa add với các file đã commit tương ứng trước đó

8. git checkout:

- git checkout -- <tenfile>: Hủy thay đổi trong file chưa add ở WORKING DIR
- git checkout <tenBranch>: Chuyển đến tên nhánh đấy để hoạt động
- git checkout -b <tenBranch>: tạo nhánh mới có tên đấy

9. git reset:

- git reset HEAD HEAD <tenfile>: Đưa file trong STAGING AREA ra trở lại WORKING DIR (trạng thái chưa add)

- git reset --soft <idCommit>:

* Đưa master về vị trí commit của <idCommit>
* Các commit sau của <idCommit> sẽ bị đưa vào STAGING AREA (trạng thái đã add nhưng chưa commit)

- git reset --mixed <idCommit>:

* Đưa master về vị trí commit của <idCommit>
* Các commit sau của <idCommit> sẽ bị đưa vào WORKING DIR (trạng thái chưa add)

- git reset --hard <idCommit>: (cẩn thận khi dùng)

* Đưa master về vị trí commit của <idCommit>
* Các commit sau của <idCommit> sẽ bị xóa hẳng khỏi REPOSYTORY, STAGING AREA và WORKING DIR

10. git branch: Xem mình đang có nhánh nào (Màu xanh là đang ở đấy)

- Nhánh master: Là nhánh chính, lưu các phiên bản code sẽ deploy lên server
- Nhánh thường tạo khi làm 1 chức năng mới (Trang)
- git checkout <tenBranch>: Chuyển đến tên nhánh đấy để hoạt động
- git checkout -b <tenBranch>: tạo nhánh mới có tên đấy
- git branch -D <tenBranch>: xóa nhánh có tên đấy

- NOTE:

* khi đang ở nhánh master thì các nhánh chưa merge sẽ không hiện, các thư mục của các nhánh đấy cũng không hiện

11. git merge: sát nhập các nhánh con đã hoàn chỉnh vào nhánh chính master
    Bước 1: git checkout master
    Bước 2: git merge <tenBrachCanSatNhap>

- NOTE:

* Mặc định của việc so sánh sự khác nhau trong git là so sánh các hàng, ta có thể sử dụng
  tham số --word-diff để git chỉ so sánh những sự khác nhau của từ
  Ex: git log -p -3 --word-diff
* Ấn q đê thoát chế độ show

13. git revert:


II. Git
1. .gitignore: File chứa các tên file (mỗi tên file là 1 dòng) mà git sẽ không xét đến

2. github:
- git remote add origin <linkReposytory>:
ex: git remote add origin https://github.com/BinzLark/learn-git.git 
tạo git REPOSYTORY trên github sau đó dùng lệnh này để Kết nối github với project của mình

- git remote -v:
Xem kết nối project với github

- git push -u origin master:
Up code lên github (chạy lần đầu push code lên) sau đó ta đăng nhập tài khoản và code sẽ up lên github
* NOTE: Nếu push code lần thứ 2 trở đi ta chỉ cần dùng:
git push



