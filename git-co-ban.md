# Hướng dẫn tìm hiểu Git cơ bản cho người mới bắt đầu

Lộ trình học Git cơ bản (trên GitHub)

## 1. Git là gì?

- Công cụ giúp tạo phiên bản cho mỗi cập nhật trên code.

## 2. Tại sao cần làm việc trên môi trường Git?

- Teamwork
- Review code standard
- Làm việc qua Git command thuận tiện và nhanh chóng
- Đảm bảo code có thể khôi phục (restore)

## 3. Tạo tài khoản GitHub miễn phí
- Tạo và xác minh email

## 4. Sử dụng SSH key để đồng bộ code lên/xuống trên GitHub
- Tạo SSH key trên máy tính (Windows và Mac)
- Copy key vào tài khoản GitHub

## 5. Cấu hình config name + email mặc định
```
git config --global user.name "Nguyen Ban A"
git config --global user.email "nguyenvana@gmail.com"
```
## 6. Lấy code dự án về (Clone)

```
git clone git@github.com:cyno-software/git-training.git
```

## 7. Chuyển nhánh (Branch)
- Chuyển từ nhánh mặc định (master) về nhánh develop

```
git checkout origin/develop
git checkout -b develop
```

> Khi chuyển nhánh, bạn không nhất thiết phải đặt tên trùng nhánh muốn chuyển.

## 7. Tạo nhánh (Checkout)
- Từ nhánh develop, tạo nhánh mới theo quy tắc đặt tên (vd: `feature/slider`, `bugfix/header`)

```
git checkout -b feature/slider
```

- Quy tắc đặt tên Git Flow cơ bản

```
Nhánh môi trường live: production
Nhánh môi trường staging: master
Nhánh môi trường phát triển: develop
Các nhánh tính năng mới: feature/<name>
Các nhánh bugfix: bugfix/<name>
Các nhánh hotfix: hotfix/<name>
```

## 8. Tạo commit (Commit)

```
git add <file_name_1> <file_name_2> <folder>
git commit -m "Add new commit"
```

- Quy tắc đặt tên commit

```
Commit_ID + Verb (thì hiện tại) + object + where
```

Các động từ phổ biến:

```
- Fix something
- Update something
- Change something
- Deploy something
- Move something
```

Ví dụ:

```
#1705 Fix button style on slider block
#1236 Update css class for re-render section all pages
```

## 9. Đẩy code lên nhánh GitHub (Push)

Nếu tên cùng nhánh:

```
# Ví dụ nhánh trên máy cũng là `develop`
git push -u origin develop
```

Nếu tên khác nhánh:

```
# Ví dụ nhánh trên máy tên là `local`
git push origin HEAD:develop
```

- Phân biệt nhánh (branch) trên máy (local) và nhánh online (remote origin)
- Mẹo: luôn có thể từ nhánh ảo trên máy đẩy lên nhánh khác tên trên online remote

## 10. Tạo pull request trong GitHub

- Căn cứ theo Git Flow ở mục (7), khi đẩy lên nhánh feature/xxx, bugfix/xxx, hotfix/xxx, ta cần tạo pull request tương ứng vào nhánh chính (develop/master)

```
feature/xxx => develop
bugfix/xxx => develop
hotfix/xxx => master
```
