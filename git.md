# Rikkei Soft Git Training [![GitHub release](http://rikkeisoft.com/wp-content/themes/rikkei/images/common/fbimg_new.png)](http://rikkeisoft.com/)
*Learn how to use Git*

Nắm được những cú pháp cơ bản của git, có thể tương tác source code với git. Tạo 1 source và thao tác cơ bản như thêm file, xóa, cách commit làm sao, làm thế nào tạo branch, tương tác trên branch, merge code, etc...

## Tạo 1 repository mới 

Trang chủ -> `new repository`

## Tạo một kho chứa git

```bash
$ git init
```

## Thêm một remote

```bash
$ git remote add origin https://github.com/luqu0501/rkdnGitTraining.git
```

## Clone (nhân bản về máy)

```bash
$ git clone https://github.com/daneden/animate.css.git
```

## Kiểm tra trạng thái các file

```bash
$ git status
```

## Để Git theo dõi

```bash
$ git add [file_name]
```
Hoặc để theo dõi toàn bộ:

```bash
$ git add * || git add . -A || git add .
```

## Xác nhận - (lưu trữ vào kho chứa local - thêm comment với lần commit)

```bash
$ git commit -m"Awesome comment here!!!"
```

## Đồng bộ lên server

```bash
$ git push <Remote_name> <Branch_name>
```

Ví dụ:

```bash
$ git push origin master
```

## Nhánh (Branch)

Tạo một nhánh ở máy local và chọn nhánh đó:

```bash
$ git checkout -b [branch_name]
```

Chuyển nhánh:

```bash
$ git checkout [branch_name]
```

Xem tất cả các nhánh:

```bash
$ git branch
```

## Pull

Cập nhật giữa github xuống local.
(Về bản chất khi chạy câu lệnh git pull origin master thực sự là bạn đang sử dụng hai câu lệnh phía sau:)
`git fetch origin master` và `git merge origin master`

```bash
$ git pull
```

Pull request là một yêu cầu gửi tới quản trị viên kho chứa từ xa gộp commit.

## Merge

Gộp nhánh mong muốn với nhánh hiện tại

```bash
$ git merge [Tên_nhánh_muốn_gộp]
```
