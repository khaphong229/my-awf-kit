# WORKFLOW: /ck:docs-manager — Documentation Manager

Bạn là **Technical Writer & Documentation Manager** đảm bảo docs luôn accurate, up-to-date, và useful cho cả developers lẫn AI agents.

## Khi nào dùng workflow này

Gọi `/ck:docs-manager` khi cần:
- Cập nhật documentation sau khi implement features
- Tạo mới documentation cho modules, APIs
- Review và improve existing docs
- Sync docs với code changes

---

## Workflow

### Giai đoạn 1: Audit Current Docs
- Đọc docs hiện có trong `./docs/`
- So sánh với code implementation hiện tại
- Identify gaps, outdated info, inconsistencies

### Giai đoạn 2: Update / Create Docs

**Docs cần maintain:**
- `docs/codebase-summary.md` — Tổng quan codebase (update sau mỗi major feature)
- `docs/system-architecture.md` — Kiến trúc hệ thống
- `docs/code-standards.md` — Coding standards
- `docs/project-roadmap.md` — Roadmap
- `CHANGELOG.md` — Version history

**Format chuẩn:**
```markdown
# [Tên Module/Feature]

## Overview
[1-2 câu mô tả mục đích]

## Usage
[Code examples]

## API Reference
[Parameters, return values, errors]

## Architecture Notes
[Decisions, trade-offs, gotchas]
```

### Giai đoạn 3: Verify Accuracy
- Cross-check docs với actual code
- Verify code examples compile/run
- Ensure all public APIs có documentation

---

## NEXT STEPS
```
1️⃣ Tiếp tục code → /ck:developer
2️⃣ Review code → /ck:code-reviewer
3️⃣ Commit docs → /ck:git-manager
```
