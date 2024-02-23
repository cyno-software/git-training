# Git - Nâng cao

Sau khi hoàn thành Git Cơ bản, ta sẽ tới những tình huống thường gặp và cách xử lý.

## Revert (Hoàn tác) một commit

Trường hợp gặp phải:

Bạn có đẩy một commit lên nhánh, ví dụ:

```
#2115 Fix button background color on homepage FAQ
```

Sau đó, khi bạn kiểm tra lại, trường hợp này đã được một ai đó đã fix trước và đẩy lên nhánh chính `develop` rồi. Như vậy, commit của bạn không cần phải cho lên `develop` nữa.
Nhưng nhánh bạn đang làm thì vẫn chứa commit này, và bạn muốn gỡ nó ra khỏi nhánh trước khi merge lên develop.

```
------*----------develop
------*
       \
        \
         *--(commit cần revert)---(feature/fix-homepage)
```

Bạn sẽ cần thao tác 'revert', hiểu nôm na là 'Undo' những gì đang làm trên nhánh hiện tại. Khác với cách bạn hiểu Undo là không còn dấu vết gì, thực tế Git sẽ luôn ghi nhận mọi commit bất kể bạn muốn Undo nó ra.

Nên khi bạn chạy thao tác revert, thực tế bạn sẽ thấy 2 commit như sau trong nhánh hiện tại:

```
#215 Fix button background color on homepage FAQ
Revert "#215 Fix button background color on homepage FAQ"
```

Để chạy lệnh Git Revert, bạn cần biết commit ID của nhánh (xem [câu hỏi thường gặp về Git nâng cao - mục 1](git-nangcao-faq.md)).

Sau đó, chạy lệnh sau:

```
git revert <commit_id>
```

Ví dụ: `git revert 29bba608508458352f2f0f22f6a8717d5d13f7c8`

Màn hình sẽ hiện ra xác nhận bằng công cụ soạn thảo, bạn chỉ cần lưu lại là xong (nếu dùng Git Bash).

Nếu bạn dùng SourceTree, bạn có thể chọn commit cần revert, ấn menu chuột phải chọn 'Revert...' để tiến hành thao tác tương tự.

Cuối cùng, đừng quên `git push` lên nhánh của mình nhé.

## Lùi 1 commit gần nhất

Trong một số tình huống, commit gần nhất của bạn có thể đã thêm nhầm file hoặc chưa thêm đủ file cần thiết. Trường hợp này, ta có thể xử lý như sau:

**Nếu commit chưa được cho lên GitHub**

(Tức là chưa chạy lệnh `git push ...`)

Bạn có thể lùi trực tiếp một commit bằng câu lệnh:

```
git reset HEAD~1
```

Sau đó, chạy tiếp `git status` sẽ ra kết quả là hoàn lại trạng thái trước khi commit:
- Các file đã commit gần nhất đã trở lại trạng thái chưa thêm vào Git (màu đỏ)

Và kiểm tra `git log` (nhật ký nhánh hiện tại) cũng cho kết quả:
- Commit gần nhất không phải commit bạn vừa lùi

**Nếu commit đã được cho lên GitHub**

Nếu bạn đủ quyền, chạy câu lệnh `git push origin HEAD:<tên nhánh> --force` để ghi đè lên. Áp dụng cho các nhánh phụ hay nhánh của bạn mà thôi.
