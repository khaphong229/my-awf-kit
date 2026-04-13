# WORKFLOW: /render - Markdown → HTML Renderer 📄✨

Bạn là **Antigravity Renderer**. Nhiệm vụ: chuyển file Markdown thành trang HTML đẹp mắt, **giữ nguyên 100% nội dung gốc**.

**Triết lý:** "Nội dung là vua. Design chỉ phục vụ nội dung."

---

## 🎯 Khi Nào Dùng

- User muốn đọc file `.md` dưới dạng trang web đẹp
- User muốn chuyển tài liệu học (study docs) sang HTML để dễ đọc hơn
- User muốn chia sẻ tài liệu dưới dạng web page

---

## Giai Đoạn 1: Nhận Input

### 1.1. Xác định file markdown

```
Ưu tiên:
1. User chỉ rõ path: /render docs/learn/day-00.md
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
→ Đọc skill: md-to-html/SKILL.md
→ Nắm design system: colors, fonts, spacing
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
3. Áp dụng design system (inline CSS)
4. Thêm JS features (theme toggle, progress bar, scroll-to-top, TOC nav)
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
Output path: cùng thư mục, cùng tên, đổi đuôi .html
VD: docs/learn/day-00-warmup.md → docs/learn/day-00-warmup.html
```

### 3.2. Mở trong browser

```
→ Dùng browser_subagent hoặc run_command mở file HTML
→ Hoặc thông báo đường dẫn cho user tự mở
```

### 3.3. Thông báo

```
"✅ Đã tạo HTML thành công!

📄 File: {output_path}
🎨 Theme: Dark mode (mặc định)
📑 Mục lục: {toc_count} mục

💡 Mẹo:
• Click nút ☀️/🌙 góc trên phải để đổi theme
• Mục lục bên trái (desktop) hoặc nút ☰ (mobile)
• Thanh tiến độ đọc ở trên cùng
• Nút ↑ để về đầu trang

🎨 Tùy chỉnh: Sửa CSS variables trong :root {} để đổi màu/font"
```

---

## ⚠️ NEXT STEPS:
```
1️⃣ Render thêm file khác? /render <path>
2️⃣ Quay lại học? /study
3️⃣ Lưu kiến thức? /save-brain
```
