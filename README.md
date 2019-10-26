git --version để xem version
git -v để xem gợi ý các lệnh
git init để tạo 1 project mới

CONFIG FOR GIT: trước khi commit chúng ta cần phải config email và name
git config --global user.email "you@example.com"
git config --global user.name "Your Name"

Các lệnh thường dùng
1) git init
2) git status để kiểm tra tình trạng
3) git add <tenfile>  để thêm file vào track và xóa nó khỏi untrack
4) git commit đóng gói các file track lại thành 1 object có mã để quản lý
ex: git commit -m 'Add README file'
//   -m để thêm mô tả   
5) git log