---
description: Render md to Neo-Cyberpunk HTML (Tensorship style)
---

# WORKFLOW: /render-neo — Markdown → Neo-Cyberpunk HTML 🔥

Bạn là **Antigravity Renderer (Neo Edition)**. Nhiệm vụ: chuyển file Markdown thành trang HTML phong cách **Neo-Cyberpunk** (nền đen, accent cam, blue glow) lấy cảm hứng từ tensorship.tech. **Giữ nguyên 100% nội dung gốc**.

**Triết lý:** "Nội dung là vua. Design gây WOW."

---

## 🎯 Khi Nào Dùng

- User muốn render `.md` sang HTML phong cách **Tensorship / Neo-Cyberpunk**
- User muốn dark-mode only, premium UI
- User muốn trang tài liệu đẹp như course.tensorship.tech

---

## Giai Đoạn 1: Nhận Input

### 1.1. Xác định file markdown

```
Ưu tiên:
1. User chỉ rõ path: /render-neo docs/learn/day-00.md
2. User @mention file
3. File đang mở (active document)
4. Hỏi user nếu không rõ
```

### 1.2. Validate

```
if file_extension != ".md":
    → "File này không phải Markdown (.md). Bạn kiểm tra lại nhé!"
    → Dừng

if file_not_found:
    → "Không tìm thấy file. Kiểm tra lại đường dẫn?"
    → Dừng
```

---

## Giai Đoạn 2: Đọc Skill & Convert

### 2.1. Load Skill

```
→ Đọc skill: md-to-html-neo/SKILL.md
→ Nắm design system: Be Vietnam Pro, orange accent, blue glow, dark-only
→ Nắm quy tắc: KHÔNG thay đổi nội dung
```

### 2.2. Đọc file Markdown

```
→ Đọc toàn bộ file .md
→ Xác định title (h1 đầu tiên hoặc tên file)
→ Đếm sections, tables, code blocks
```

### 2.3. Convert Markdown → HTML

```
Theo hướng dẫn trong SKILL.md:
1. Parse markdown → HTML elements
2. Tạo Table of Contents từ h2/h3
3. Áp dụng Neo-Cyberpunk design system (inline CSS)
4. Thêm JS features (progress bar BOTTOM, scroll-to-top, TOC nav, copy code)
5. Tạo single file HTML hoàn chỉnh
```

### ⚠️ QUY TẮC NỘI DUNG (KHÔNG ĐƯỢC VI PHẠM)

```
❌ KHÔNG: Thêm, bớt, sửa, dịch, tóm tắt bất kỳ nội dung nào
✅ CHỈ: Chuyển format hiển thị (markdown syntax → HTML + CSS)
```

---

## Giai Đoạn 3: Output & Deliver

### 3.1. Tạo file HTML

```
Output path: cùng thư mục, cùng tên, thêm .neo.html
VD: docs/learn/day-00-warmup.md → docs/learn/day-00-warmup.neo.html
```

### 3.2. Mở trong browser

```
→ Dùng browser_subagent hoặc run_command mở file HTML
→ Hoặc thông báo đường dẫn cho user tự mở
```

### 3.3. Thông báo

```
"✅ Đã tạo HTML Neo-Cyberpunk thành công!

📄 File: {output_path}
🎨 Theme: Dark only (Neo-Cyberpunk)
🔵 Glow: Blue border glow effect
🟠 Accent: Deep Orange (#ff5722)
📑 Mục lục: {toc_count} mục

💡 Tính năng:
• Mục lục sidebar bên trái (desktop) / nút ☰ (mobile)
• Thanh tiến độ đọc ở DƯỚI CÙNG (cam)
• Nút Copy trên mỗi code block
• Nút ↑ để về đầu trang
• Hiệu ứng fade-in khi scroll"
```

---

## ⚠️ NEXT STEPS:
```
1️⃣ Render thêm file khác? /render-neo <path>
2️⃣ Render kiểu cũ (có light mode)? /render <path>
3️⃣ Quay lại học? /study
```
