#Git basic  
git --version để xem version
git -v để xem gợi ý các lệnh
git init để tạo 1 project mới WORKING DIR

CONFIG FOR GIT: trước khi commit chúng ta cần phải config email và name  
git config --global user.email "you@example.com"  
git config --global user.name "Your Name"

A. CÁC LỆNH THƯỜNG DÙNG

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

7. git diff : Xem lại nội dung thay đổi của các file chưa add với các file đã commit hoặc giữa các file chưa add với các file đã add tương ứng trước đó

8. git checkout:

- git checkout -- <tenfile>: Hủy thay đổi trong file chưa add ở WORKING DIR
- git checkout <tenBranch>: Chuyển đến tên nhánh đấy để hoạt động
- git checkout -b <tenBranch>: tạo nhánh mới có tên đấy

9. git reset:

- git reset HEAD <tenfile>: Đưa file trong STAGING AREA ra trở lại WORKING DIR (trạng thái chưa add)

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

B. Git
I. .gitignore: File chứa các tên file (mỗi tên file là 1 dòng) mà git sẽ không xét đến

II. github:

1. git remote add origin <linkReposytory>:
   ex: git remote add origin https://github.com/BinzLark/learn-git.git
   tạo git REPOSYTORY trên github sau đó dùng lệnh này để Kết nối github với project của mình

2. git remote -v:
   Xem kết nối project với github

3. git push -u origin master:
   Up code lên github (chạy lần đầu push code lên) sau đó ta đăng nhập tài khoản và code sẽ up lên github

- undo commit on github: git push -f origin HEAD^:master=
- NOTE: Nếu push code lần thứ 2 trở đi ta chỉ cần dùng:
  git push

III. pull request: Làm việc nhóm:

1. Với 2 người:  
   a. git clone <linkReposytory>:  
   clone Reposytory về máy người khác.(người thứ 2)

   b. git pull:  
   Cập nhật những thay đổi mới ở trên github về máy
   * git pull origin <tenBranch>: cập nhật từ <tenBranch> trở đi

2. Với nhiều người: (Bên A là bên thay đổi, bên B là bên còn lại)  
   Bước 1: Tạo 1 nhánh con để làm các công việc nhỏ
   git checkout -b <tenBranch> (Bên A)

   Bước 2: push nhánh đấy lên github để mọi người cùng check code (Bên A)  
   git push origin <tenBranch>
   
   Bước 3: tạo 1 pull request trên github (Bên A)  
   - Mục đích là để team xem và đánh giá code. Sau khi mọi người thấy code đã hoàn chỉnh thì chúng ta merge pull request
   
   Bước 4: review code (Bên B)  
         4.1. review code online trên github:  
         Vào pull request vào mục "files changed" để xem sự thay đổi  
         4.2. fetch branch into local to test offline (optional)    
         + step 1: git fetch origin <tenBranch>  
         + step 2: git branch: để xem branch hiện tại  
         + step 3: git checkout <tenBranch>: để chuyển sang branch đấy  
         + step 4: vim <tenFile> để kiểm tra lại code. sau đó chạy thử chương trình để test  
         + step 5: Xóa branch đấy sau khi kiểm tra xong  
         4.3. approve a pull request
    
   Bước 5: Bên A: Merge to master và xóa branch không cần dùng đi (xóa trên github và local) và git pull để cập nhập commit đã thay đổi   
          Bên B: git pull để cập nhập
          
IV. Resolve conflict: Conflict ở trên branch nào thì người chủ của branch đấy phải fix  
   Các trường hợp bị conflict:    
    - Trường hợp 2 bên cùng sửa 1 file (có dòng trùng nhau?)  
    - Trường hợp 1 bên xóa file, 1 bên sửa file đó
1. Cách 1: 
    - Bước 1: chuyển đến nhánh master và git pull origin để lấy dữ liệu về 
    - Bước 2: dịch chuyển đến branch muốn fix  
    - Bước 3: git rebase master  
        sau đó đọc xem rebase trả về file nào bị lỗi  
    - Bước 4: Nếu muốn giữ lại tất cả thì bỏ đi những dấu gạch gạch thừa ở file lỗi  
    - Bước 5: git add <tenFileLoi>  
    - Bước 6: git rebase --continue  
    - Bước 7: git push origin <tenBranchLoi> -f  
    
    
2. Cách 2:   
    - Bước 1: chuyển đến nhánh master và git pull để lấy dữ liệu về
    - Bước 2: git checkout <branchLoi>
    - Bước 3: git merge master  
        sau đó đọc xem merge trả về file nào bị lỗi  
    - Bước 4: Nếu muốn giữ lại tất cả thì bỏ đi những dấu gạch gạch thừa ở file lỗi  
    - Bước 5: git add <tenFileLoi>  
    - Bước 6: git commit -m 'mota'  
    - Bước 7: git push origin <tenBranchLoi>
    
    
*NOTE: Nên dùng cách 2 hơn cách 1 vì cách 1 ở bước 6 push -f sẽ gây thay đổi lịch sử commit
   
 
