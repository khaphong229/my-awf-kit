# ClaudeKit Development Rules

> Migrated from claudekit-engineer `claude/rules/development-rules.md`
> Áp dụng cho mọi dự án khi làm việc với Antigravity.

## Nguyên tắc cốt lõi (BẮT BUỘC)

**YAGNI** (You Aren't Gonna Need It) — Đừng over-engineer, chỉ làm những gì cần thiết ngay lúc này.  
**KISS** (Keep It Simple, Stupid) — Ưu tiên giải pháp đơn giản, dễ đọc.  
**DRY** (Don't Repeat Yourself) — Không lặp code, extract thành module/function tái sử dụng.

---

## Quy tắc Tổng quát

- **File Naming**: Dùng `kebab-case` cho tên file. Tên phải mô tả rõ mục đích, đủ dài để AI đọc tên file là hiểu ngay mà không cần mở file.
- **File Size**: Giữ mỗi file code dưới **200 dòng** để tối ưu context window.
  - Split file lớn thành các component/module nhỏ hơn, tập trung hơn
  - Dùng composition thay vì inheritance cho widget phức tạp
  - Extract utility function vào module riêng
  - Tách service class cho business logic
- Khi cần tra tài liệu, kích hoạt skill `docs-seeker` để tìm docs mới nhất.
- Khi cần phân tích ảnh/video/document, dùng skill `ai-multimodal`.
- Khi cần sequential reasoning hoặc debug phức tạp, dùng skill `sequential-thinking` và `ck-debug`.
- **[QUAN TRỌNG]** Tuân theo codebase structure và coding standards trong `./docs` khi implement.
- **[QUAN TRỌNG]** Không mock hay simulate implementation — luôn viết code thật.

---

## Code Quality

- Đọc và follow codebase structure và standards trong `./docs`
- Không quá khắt khe về linting, nhưng **đảm bảo không có syntax error và code compile được**
- Ưu tiên functionality và readability hơn strict style enforcement
- Luôn dùng try-catch error handling và cover các security concerns cơ bản

---

## Git & Pre-commit Rules

- Chạy linting trước khi commit
- Chạy tests trước khi push — **KHÔNG được bỏ qua test thất bại**
- Commit message dùng **Conventional Commits** format: `type(scope): description`
  - `feat:` — tính năng mới
  - `fix:` — bug fix
  - `docs:` — tài liệu
  - `refactor:` — tái cấu trúc
  - `test:` — test
- **KHÔNG** commit file `.env`, API keys, database credentials lên git

---

## Code Implementation

- Viết code clean, readable, maintainable
- Follow architectural patterns đã có trong dự án
- Implement theo đúng specification
- Handle edge cases và error scenarios
- **KHÔNG** tạo file "enhanced" mới — sửa trực tiếp vào file hiện có

---

## Khi nào dùng Workflow này?

Workflow này không invoke trực tiếp — đây là **reference document**. Đọc khi:
- Bắt đầu implement một tính năng mới
- Review lại code quality trước khi commit
- Onboarding một dự án mới
