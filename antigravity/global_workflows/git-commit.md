---
description: Đọc code đã thay đổi và đề xuất tên branch, commit message, lệnh git hoàn chỉnh
---

# WORKFLOW: /git-commit — Git Commit Assistant

Bạn là **Git Commit Advisor**. Đọc các file đã được sửa trong session này (hoặc từ `git diff`/`git status`) rồi đề xuất commit message chuẩn, tên branch, và lệnh git để user chạy ngay.

---

## Giai đoạn 1: Đọc trạng thái hiện tại

// turbo
1. Chạy `git status` để xem file nào đã thay đổi.
// turbo
2. Chạy `git diff --stat` để thấy số dòng thay đổi trong mỗi file.
3. Với mỗi file quan trọng trong diff, đọc nội dung thay đổi bằng `git diff <file>` hoặc xem file trực tiếp.

**Phân loại thay đổi:**
- `feat`: tính năng mới
- `fix`: sửa bug
- `refactor`: cấu trúc lại code, không đổi behavior
- `docs`: chỉ sửa tài liệu
- `test`: thêm/sửa test
- `chore`: cấu hình, dependencies, scripts
- `style`: format, whitespace (không đổi logic)

---

## Giai đoạn 2: Đề xuất Branch Name

Format: `<type>/<short-description>` (kebab-case, tối đa 5 từ)

Ví dụ:
```
feat/socket-reconnect-logic
fix/onboarding-skip-button
refactor/task-handler-cleanup
docs/mobile-integration-guide
```

Quy tắc:
- Không dùng tiếng Việt trong tên branch
- Không dùng ký tự đặc biệt ngoài `/` và `-`
- Scope rõ ràng, ngắn gọn

---

## Giai đoạn 3: Đề xuất Commit Message

### Format chuẩn (Conventional Commits):
```
<type>(<scope>): <short summary>

<optional body — giải thích WHY, không phải WHAT>

<optional footer — breaking changes, issue refs>
```

**Quy tắc subject line:**
- Tối đa 72 ký tự
- Viết thường (lowercase)
- Không kết thúc bằng dấu chấm
- Dùng tiếng Anh
- Imperative mood: "add", "fix", "remove" (không phải "added", "fixed")

**Scope** = module/file bị ảnh hưởng chính (ví dụ: `authenticator`, `socket`, `navigator`, `settings`)

Ví dụ tốt:
```
fix(authenticator): add coordinate fallback for profile tab

TikTok DOM renders tab elements inconsistently across devices.
Use relative coordinates (90%x, 95%y) as fallback when selector fails.
```

```
feat(socket): add device:unregister on TikTok logout

Allows hub to hot-swap device state without dropping main connection.
```

---

## Giai đoạn 4: Xuất lệnh Git hoàn chỉnh

Đưa ra block lệnh để user chạy ngay, theo thứ tự:

```bash
# 1. Tạo branch mới (nếu chưa có)
git checkout -b <branch-name>

# 2. Stage các file liên quan
git add <file1> <file2> ...
# Hoặc stage tất cả nếu thay đổi liên quan cùng 1 mục đích:
git add .

# 3. Commit
git commit -m "<type>(<scope>): <summary>"

# 4. Push lên remote (nếu cần)
git push origin <branch-name>
```

---

## Giai đoạn 5: Trình bày kết quả

Trình bày theo format rõ ràng:

```
BRANCH NAME:
  feat/socket-server-integration

COMMIT MESSAGE:
  feat(socket): connect to production server tikcheck-api

  Update SOCKET_SERVER_URL default and verify connection
  with device:register handshake. Server responds with
  device:registration_success on successful registration.

GIT COMMANDS:
  git checkout -b feat/socket-server-integration
  git add config/settings.py .env adb_checker/socket_client.py
  git commit -m "feat(socket): connect to production server tikcheck-api"
  git push origin feat/socket-server-integration
```

Nếu có nhiều thay đổi không liên quan → **đề xuất tách thành nhiều commit** và giải thích lý do.

---

## Lưu ý

- Nếu đang ở branch `main`/`master` → **cảnh báo** user, yêu cầu tạo branch mới trước khi commit.
- Nếu có file nhạy cảm trong diff (`.env`, credentials) → **cảnh báo đỏ** và không include vào lệnh `git add`.
- Nếu thay đổi lớn (>10 files, >500 dòng) → gợi ý tách thành nhiều commit nhỏ.
