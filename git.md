
### 1. **Giới thiệu về Git**
   - **Git là gì?**: Git là hệ thống quản lý phiên bản phân tán (Distributed Version Control System - DVCS) giúp theo dõi các thay đổi trong mã nguồn và cho phép nhiều người cộng tác trên cùng một dự án một cách hiệu quả.
   - **Lợi ích của Git**: Hỗ trợ làm việc nhóm, quản lý lịch sử thay đổi của mã nguồn, và giúp khôi phục lại trạng thái mã ở bất kỳ thời điểm nào.

### 2. **Cấu trúc của Git Repository**
   - **Repository (Repo)**: Là thư mục gốc chứa toàn bộ mã nguồn và dữ liệu của dự án. Mỗi repo có hai loại:
     - **Local Repository**: Repo trên máy tính của bạn.
     - **Remote Repository**: Repo nằm trên server để chia sẻ với các thành viên khác (ví dụ: trên GitHub, GitLab, Bitbucket).
   - **Working Directory**: Thư mục mà bạn thực hiện các thay đổi mã nguồn.
   - **Staging Area**: Khu vực lưu trữ tạm thời các thay đổi trước khi commit vào repo.
   - **Git Directory (.git)**: Thư mục ẩn chứa toàn bộ dữ liệu về lịch sử commit, các nhánh, cấu hình, và các metadata của repo.

### 3. **Các thao tác cơ bản trong Git**

   - **git init**: Khởi tạo một repository mới trong thư mục hiện tại.
   - **git clone**: Sao chép một remote repository về máy tính của bạn, tạo bản sao của toàn bộ repo.
   - **git add**: Thêm các thay đổi từ working directory vào staging area.
   - **git commit**: Đưa các thay đổi trong staging area vào repository với một thông điệp miêu tả.
   - **git status**: Kiểm tra trạng thái hiện tại của repo (các thay đổi chưa staged, chưa commit, v.v.).
   - **git log**: Hiển thị lịch sử các commit của repo.
   - **git diff**: So sánh sự khác nhau giữa các trạng thái (ví dụ: working directory với staging area, hoặc giữa hai commit).
   - **git config**: Thiết lập cấu hình cho Git (ví dụ: tên người dùng, email).

### 4. **Quy trình làm việc trong Git (Git Workflow)**

   - **Làm việc cục bộ (Local Workflow)**:
     1. Thực hiện thay đổi trong working directory.
     2. Dùng `git add` để đưa các thay đổi vào staging area.
     3. Dùng `git commit` để lưu lại thay đổi trong repo.
   - **Làm việc với repo từ xa (Remote Workflow)**:
     - **git pull**: Lấy và hợp nhất thay đổi từ remote repository vào local repository.
     - **git push**: Đẩy các thay đổi từ local repository lên remote repository.
   - **Làm việc với các nhánh (Branching)**:
     - **git branch**: Quản lý các nhánh trong repo (tạo, xóa, liệt kê các nhánh).
     - **git checkout**: Chuyển đổi giữa các nhánh hoặc commit cụ thể.
     - **git merge**: Hợp nhất hai nhánh với nhau.
     - **git rebase**: Thay đổi điểm gốc của một nhánh, giúp tối ưu hóa lịch sử commit.

### 5. **Quản lý các nhánh (Branching và Merging)**
   - **Nhánh (Branch)**: Cho phép bạn phát triển tính năng mới hoặc sửa lỗi một cách độc lập mà không ảnh hưởng đến mã chính (main branch).
     - **git branch <branch_name>**: Tạo nhánh mới.
     - **git checkout <branch_name>**: Chuyển sang nhánh khác.
     - **git checkout -b <branch_name>**: Tạo và chuyển ngay sang nhánh mới.
   - **Merge**: Hợp nhất thay đổi từ một nhánh vào nhánh khác (ví dụ: từ feature branch vào main branch).
     - **git merge <branch_name>**: Thực hiện merge nhánh chỉ định vào nhánh hiện tại.
     - **Merge conflict**: Xảy ra khi cùng một phần của file được thay đổi trong cả hai nhánh. Git sẽ yêu cầu người dùng giải quyết xung đột trước khi hoàn tất merge.

### 6. **Rebase**
   - **Rebase**: Di chuyển hoặc gán lại chuỗi commit từ nhánh này sang nhánh khác.
     - **git rebase <branch_name>**: Thay đổi điểm gốc của nhánh hiện tại thành nhánh chỉ định.
   - **Interactive Rebase**: Giúp chỉnh sửa, thay đổi thứ tự, hợp nhất, hoặc xóa các commit trước khi tích hợp vào nhánh chính.
     - **git rebase -i <commit_hash>**: Mở interactive rebase, cho phép thực hiện các chỉnh sửa chi tiết.

### 7. **Reset, Revert, Restore**

   - **git reset**: Đưa repo về trạng thái của commit trước. Có 3 chế độ:
     - **--soft**: Chỉ di chuyển con trỏ HEAD, giữ nguyên các thay đổi trong staging area.
     - **--mixed**: Di chuyển HEAD và làm trống staging area, giữ các thay đổi trong working directory.
     - **--hard**: Xóa toàn bộ thay đổi trong staging area và working directory.
   - **git revert**: Tạo một commit đảo ngược lại một commit trước đó, giúp duy trì lịch sử của repo.
   - **git restore**: Khôi phục file trong working directory về trạng thái của một commit trước đó hoặc từ staging area.

### 8. **Tagging**
   - **Tag**: Đánh dấu một commit quan trọng (ví dụ: phiên bản phát hành).
   - **git tag <tag_name>**: Tạo lightweight tag.
   - **git tag -a <tag_name> -m "message"**: Tạo annotated tag với thông tin chi tiết.
   - **git push origin <tag_name>**: Đẩy tag lên remote repository.

### 9. **Các thao tác nâng cao**
   - **Stashing**: Lưu trữ tạm thời các thay đổi chưa commit.
     - **git stash**: Lưu trữ thay đổi hiện tại trong stash và trả lại trạng thái working directory về sạch.
     - **git stash pop**: Khôi phục thay đổi từ stash và xóa stash đó.
     - **git stash apply**: Khôi phục thay đổi từ stash mà không xóa stash đó.
   - **Cherry-pick**: Áp dụng một commit cụ thể vào nhánh hiện tại.
     - **git cherry-pick <commit_hash>**: Sao chép commit cụ thể từ nhánh khác sang nhánh hiện tại.
   - **Bisect**: Giúp xác định commit nào gây ra lỗi bằng cách chia nhỏ các commit và kiểm tra.
     - **git bisect start**: Khởi đầu quá trình bisect.
     - **git bisect good/bad**: Đánh dấu trạng thái của commit (tốt hoặc lỗi).

### 10. **Các lệnh khác**
   - **git blame**: Xem lịch sử sửa đổi của từng dòng trong file.
   - **git clean**: Xóa các file chưa được quản lý (untracked) khỏi working directory.
   - **git show**: Hiển thị chi tiết về commit hoặc đối tượng git khác.

### 11. **Git Workflow phổ biến**
   - **Feature Branch Workflow**: Mỗi tính năng được phát triển trên một nhánh riêng và hợp nhất vào nhánh chính sau khi hoàn tất.
   - **Gitflow Workflow**: Bao gồm các nhánh chính như main, develop, feature, release, và hotfix. Thường được sử dụng trong các dự án lớn.
   - **Forking Workflow**: Người dùng fork repository về repo riêng, thực hiện thay đổi, và tạo pull request để merge vào repo chính.

### 12. **Các khái niệm khác trong Git**
   - **HEAD**: Con trỏ chỉ tới commit hiện tại trong repo.
   - **Origin**: Tên mặc định của remote repository đầu tiên.
   - **Upstream và Downstream**: Upstream là nhánh gốc (thường là remote branch) mà bạn đang theo dõi; Downstream là nhánh mà bạn kéo các thay đổi từ upstream.

### 13. **Công cụ và Nền tảng sử dụng Git**
   - **GitHub, GitLab, Bitbucket**: Các nền tảng lưu trữ mã nguồn, cung cấp tính năng quản lý phiên bản, cộng tác, pull request, review code, CI/CD, và quản lý issue.
   - **Các công cụ GUI cho Git**: GitKraken, Sourcetree, GitHub Desktop giúp quản lý Git qua giao diện đồ họa.
