# Phase 1 — Individual Scan: tìm 5+ problems (25')

## Bảng scan

| # | Lăng kính | Problem quan sát được | Ai chịu ảnh hưởng? | Dấu hiệu thật |
|---|---|---|---|---|
| 1 | Lặp lại / Tốn thời gian | Tổng hợp và gán nhãn thủ công tập dữ liệu hình ảnh | Team AI, Team NCKH | Cả team phải mất 1-2 tuần/đợt để tự tổng hợp các hình ảnh, phân loại và gán nhãn từng ảnh thủ công. |
| 2 | Lặp lại / Pain từ người khác | Nhắc nhở thành viên nộp daily task hằng ngày | Team Lead, Thành viên nhóm | Mỗi ngày Team Lead phải nhắn từng người qua Messenger để nhắc nộp daily task trên Discord (xảy ra 5 lần/tuần). |
| 3 | Tốn thời gian / AI có thể tốt hơn | Tổng hợp tin nhắn & Q&A trên Discord khóa học AI thực chiến mỗi ngày | Học viên AI thực chiến | Tốn 30-60 phút mỗi ngày lội tin nhắn Discord để tự lọc thông báo, kiến thức hay và câu trả lời trùng nhau. |
| 4 | Tốn thời gian | Ôn lại kiến thức và chuẩn bị bài trước buổi học | Học viên AI thực chiến | Mất 1-2 tiếng trước mỗi buổi học đọc lại slide, bài lab và tài liệu rải rác để chuẩn bị kiến thức. |
| 5 | Tốn thời gian / AI có thể tốt hơn | Onboarding người mới vào codebase/dự án lớn | Newbie/Fresher, Mentor/Senior | Người mới tốn 1-2 tuần đọc docs/codebase để hiểu luồng, Senior tốn 5-10 tiếng/đợt để giải thích lại quy trình cũ. |



# Phase 2 — Top 3 Problem Cards + draft workflow (35')

## Chọn top 3

| Rank | Problem | Vì sao chọn | Điều còn chưa chắc
|---|---|---|---|
| 1 | Tổng hợp và gán nhãn thủ công tập dữ liệu hình ảnh | Workflow cực kỳ rõ ràng, quy trình lặp lại, tốn 1–2 tuần/đợt; đo lường impact rất dễ bằng thời gian giảm bớt và số lượng ảnh xử lý được.  | Tiêu chuẩn đánh giá độ chính xác của nhãn do AI gợi ý/gán nhãn tự động như thế nào để team tin tưởng.  
| 2 | Onboarding người mới vào codebase/dự án lớn | Pain point rất nặng (mất 1–2 tuần), ảnh hưởng lớn tới tiến độ team và tốn nguồn lực của senior/mentor.  | Phạm vi dữ liệu (scope) codebase quá rộng; rủi ro về độ bảo mật/privacy code khi đưa vào AI.  
| 3 | Tổng hợp tin nhắn & Q&A trên Discord khóa học | Tốn 30–60 phút mỗi ngày; dữ liệu tin nhắn Discord rời rạc, lặp đi lặp lại nhiều câu hỏi trùng nhau.  | Khả năng truy cập dữ liệu (Discord API/Bot) và việc AI bỏ sót các thông báo quan trọng trong kênh. 

## Problem Card #1 — Tổng hợp và gán nhãn tập dữ liệu hình ảnh

**Problem 1 câu:**  
Mỗi khi khởi tạo hoặc mở rộng dự án, team phải mất 1–2 tuần thao tác thủ công để thu thập, phân loại và gán nhãn tập dữ liệu hình ảnh, gây nghẽn tiến độ huấn luyện mô hình.

**Actor:**  
Thành viên team AI / Team Nghiên cứu khoa học chịu trách nhiệm chuẩn bị dữ liệu.

**Thời điểm / bối cảnh:**  
Giai đoạn đầu của dự án AI/NCKH hoặc khi cần thu thập thêm dữ liệu thực tế cho các lớp mới.

**Current workflow 3-7 bước:**
1. Thu thập hình ảnh thô từ nhiều nguồn (chụp thực tế, crawl, đóng góp từ thành viên).
2. Lọc bỏ hình ảnh lỗi, mờ, hỏng hoặc trùng lặp bằng mắt.
3. Phân chia thư mục và xác định danh sách các lớp.
4. Thực hiện khoanh vùng (bounding box) hoặc gán nhãn từng ảnh bằng công cụ thủ công (như LabelImg, Roboflow).
5. Kiểm tra chéo (cross-check) giữa các thành viên để giảm sai sót.
6. Export dữ liệu sang định dạng yêu cầu (YOLO, Pascal VOC, COCO) và phân chia tập Train/Val/Test.

**Bottleneck:**  
Bước 4 — gán nhãn chi tiết từng ảnh mất rất nhiều thời gian (trung bình 2–5 phút/ảnh), gây mệt mỏi và dễ dẫn đến sai sót khi quy mô dữ liệu lên tới hàng nghìn ảnh.

**Impact:**  
Mất 1–2 tuần làm việc liên tục của cả nhóm (3–4 người) chỉ để chuẩn bị dữ liệu thô. Tiến độ thử nghiệm model bị trễ, tốn chi phí nhân lực lặp đi lặp lại cho việc thao tác tay.

**Success metric:**  
Giảm tổng thời gian chuẩn bị và gán nhãn dataset từ 14 ngày xuống dưới 3 ngày; duy trì độ chính xác của nhãn đạt từ 90% trở lên so với kiểm thử thủ công.

**Non-AI alternative:**  
Xây dựng quy tắc (rule-based) phân loại theo metadata/tên file + sử dụng công cụ gán nhãn hàng loạt bằng phím tắt. Cách này giảm nhẹ thao tác nhấp chuột nhưng không giải quyết được việc nhận diện nội dung ảnh để tự khoanh vùng/gán nhãn.

**AI hypothesis:**  
Dùng mô hình AI (như Segment Anything / Grounding DINO / Zero-shot Vision models) để tự động nhận diện, khoanh vùng và đề xuất nhãn nháp cho hình ảnh. Con người chỉ đóng vai trò rà soát và điều chỉnh.

**Quick gut:**
[ ] No AI / process fix
[ ] Rule
[x] Workflow
[ ] Agent
[ ] Chưa biết

---

### Draft current workflow

```text
CURRENT STATE — 10-14 ngày (Cho 1.000 - 2.000 ảnh)

[1 Thu thập ảnh thô: 1-2 ngày]
→ [2 Lọc ảnh lỗi/trùng bằng mắt: 1 ngày]
→ [3 Phân loại thư mục class: 1 ngày]
→ [4 Gán nhãn/khoanh vùng thủ công từng ảnh: 7-8 ngày]  <-- bottleneck
→ [5 Kiểm tra chéo giữa các thành viên: 2 ngày]
→ [6 Export & Split Train/Val/Test: 0.5 ngày]
```

### Draft future workflow

```text
FUTURE STATE — 2.5 ngày

[1 Thu thập ảnh thô: 1 ngày]
→ [2 Auto-filter ảnh trùng/lỗi bằng script: 1 giờ]  -- Rule/Script
→ [3 AI tự động nhận diện & đề xuất nhãn nháp: 2 giờ] -- AI Workflow step
→ [4 Con người review & chỉnh sửa nhãn lệch: 1 ngày] <-- human boundary
→ [5 Auto-export & Split dataset: 1 giờ]            -- Script

Fallback: AI gán nhãn quá lệch/sai class → Human bấm hủy đề xuất AI và gán nhãn lại thủ công cho lô ảnh đó.
```

# Problem Card #2 — Onboarding người mới vào codebase/dự án lớn

**Problem 1 câu:**  
Thành viên mới gia nhập dự án tốn từ 1–2 tuần chỉ để đọc tài liệu, tìm hiểu luồng dữ liệu và cấu trúc codebase khổng lồ, làm trễ khả năng đóng góp công việc và tốn nhiều thời gian hướng dẫn của thành viên cũ.

**Actor:**  
Thành viên mới (Newbie/fresher) và Mentor/Senior trong team.

**Thời điểm / bối cảnh:**  
Giai đoạn bàn giao (onboarding) khi có thành viên mới tham gia dự án hoặc chuyển giao mô-đun công việc mới.

**Current workflow 3-7 bước:**
1. Người mới nhận quyền truy cập vào repository và tài liệu dự án (nếu có).
2. Tự đọc file Readme, tài liệu kiến trúc (architecture doc) và cấu trúc thư mục code.
3. Chạy thử dự án ở môi trường local, tự mò luồng chạy (data flow) và logic nghiệp vụ chính.
4. Đặt câu hỏi cho Senior/Mentor khi bị kẹt hoặc không hiểu cấu trúc code.
5. Senior dừng việc đang làm để giải thích, vẽ luồng hoặc chỉ nơi chứa file code cần sửa.
6. Người mới thử nhận task nhỏ (good first issue) và tiếp tục dò code để làm.

**Bottleneck:**  
Bước 2 & 3 — Tự đọc codebase lớn và mô tả nghiệp vụ rời rạc tốn rất nhiều thời gian (khoảng 30–40 giờ làm việc), dễ bị lạc trong luồng xử lý phức tạp và ngại hỏi Senior liên tục.

**Impact:**  
Mất 1–2 tuần đầu năng suất gần như bằng 0 của người mới; tốn khoảng 5–10 giờ làm việc của Senior chỉ để trả lời các câu hỏi onboarding lặp đi lặp lại.

**Success metric:**  
Giảm thời gian làm quen codebase để nhận task đầu tiên từ 10 ngày xuống dưới 3 ngày; giảm 70% số câu hỏi thắc mắc cơ bản về vị trí/luồng code phải phiền đến Senior.

**Non-AI alternative:**  
Cập nhật tài liệu Readme chi tiết + vẽ sơ đồ kiến trúc (Architecture Diagram) cố định + quy định convention chặt chẽ. Cách này giảm bớt thắc mắc nhưng tài liệu rất nhanh bị cũ (outdated) so với codebase thực tế.

**AI hypothesis:**  
Dùng AI (RAG / Codebase Assistant như RepoQA, Copilot Workspace) index toàn bộ codebase và tài liệu hiện tại để trả lời, giải thích luồng chạy, vị trí file và nghiệp vụ theo ngữ cảnh câu hỏi của người mới.

**Quick gut:**
[ ] No AI / process fix
[ ] Rule
[x] Workflow
[ ] Agent
[ ] Chưa biết

---

### Draft current workflow

```text
CURRENT STATE — 10-14 ngày

[1 Mở quyền Repo/Docs: 0.5 ngày]
→ [2 Tự đọc Readme/Docs rời rạc: 2 ngày]
→ [3 Dò thủ công từng file/folder trong codebase: 4-5 ngày] <-- bottleneck
→ [4 Hỏi Senior khi kẹt (Senior gián đoạn công việc): 2 ngày]
→ [5 Nhận task nhỏ & vừa làm vừa dò code tiếp: 3 ngày]
```

### Draft future workflow

```text
FUTURE STATE — 3 ngày

[1 Mở quyền Repo & AI Indexing Codebase: 2 giờ]   -- Rule/Script
→ [2 AI phân tích & tóm tắt luồng dự án theo yêu cầu: 3 giờ] -- AI Workflow step
→ [3 Newbie hỏi AI về luồng/vị trí code khi làm task: 1 ngày] -- AI Workflow step
→ [4 Senior review câu hỏi phức tạp/nghiệp vụ đặc thù: 4 giờ] <-- human boundary
→ [5 Newbie hoàn thành task đầu tiên: 1 ngày]

Fallback: AI giải thích sai luồng code (Hallucination) → Newbie gắn thẻ (tag) file code liên quan và nhờ Senior xác nhận lại trước khi sửa.
```

# Problem Card #3 — Tổng hợp tin nhắn & Q&A trên Discord khóa học

**Problem 1 câu:**  
Học viên mất từ 30 đến 60 phút mỗi ngày để lội tin nhắn trên Discord nhằm lọc thông tin quan trọng và kiến thức chia sẻ, dẫn đến nguy cơ bỏ sót thông báo quan trọng và phải hỏi lại các câu hỏi đã có sẵn lời giải.

**Actor:**  
Học viên / Người tham gia khóa học AI thực chiến.

**Thời điểm / bối cảnh:**  
Cuối ngày hoặc trước các buổi học, khi lượng tin nhắn thảo luận, hỏi đáp và thông báo trong các kênh Discord tăng cao.

**Current workflow 3-7 bước:**
1. Mở ứng dụng Discord và truy cập vào server của khóa học.
2. Cuộn (scroll) thủ công qua hàng loạt tin nhắn thảo luận rời rạc trong các kênh general, share-knowledge, q-and-a.
3. Đọc và tự lọc ra đâu là thông báo mới, đâu là kiến thức/chia sẻ hay, đâu là câu hỏi - đáp liên quan đến bài học.
4. Ghi chú (note) lại các thông tin quan trọng vào công cụ cá nhân (Notion, Docs, Obsidian).
5. Đặt câu hỏi lên kênh support/q-and-a nếu gặp thắc mắc (dù câu hỏi đó có thể đã được người khác giải đáp trước đó vài giờ).

**Bottleneck:**  
Bước 2 & 3 — Lội tin nhắn và lọc thủ công giữa hàng trăm tin nhắn tán tán, thảo luận lộn xộn mỗi ngày cực kỳ tốn thời gian (30–60 phút/ngày) và dễ gây tâm lý "ngợp thông tin" (information overload).

**Impact:**  
Mất 3.5 – 7 giờ mỗi tuần cho 1 học viên. Tốn công sức của Mentor/TA khi phải trả lời lại các câu hỏi trùng lặp nhiều lần do học viên không tìm thấy câu trả lời cũ.

**Success metric:**  
Giảm thời gian cập nhật thông tin hằng ngày từ 45 phút xuống dưới 10 phút; giảm 60% số câu hỏi trùng lặp gửi về cho Mentor/TA trên Discord.

**Non-AI alternative:**  
Tạo kênh Discord riêng chỉ dành cho thông báo (read-only) + tạo file FAQ/Notion tổng hợp câu hỏi thường gặp. Cách này giảm nhẹ tin nhắn rác nhưng đòi hỏi Ban tổ chức/TA phải cập nhật thủ công liên tục và học viên vẫn phải tự đi tìm trong file FAQ.

**AI hypothesis:**  
Dùng AI Bot (tích hợp Discord API + RAG/LLM Summary) tự động tóm tắt tin nhắn theo ngày, phân loại theo chủ đề (Thông báo, Bài học/Chia sẻ, FAQ) và cung cấp tính năng hỏi-đáp tra cứu câu trả lời cũ ngay trong Discord.

**Quick gut:**
[ ] No AI / process fix
[ ] Rule
[x] Workflow
[ ] Agent
[ ] Chưa biết

---

### Draft current workflow

```text
CURRENT STATE — 45 phút/ngày

[1 Mở Discord server: 1']
→ [2 Cuộn lội hàng trăm tin nhắn rời rạc: 20']  <-- bottleneck
→ [3 Tự đọc và lọc thông tin quan trọng: 15']
→ [4 Ghi chú lại kiến thức/thông báo vào sổ tay: 5']
→ [5 Đặt câu hỏi mới lên kênh support (dễ trùng): 4']
```

### Draft future workflow

```text
FUTURE STATE — 8 phút/ngày

[1 Auto-fetch tin nhắn Discord theo ngày/kênh: 2']        -- Rule/Script
→ [2 AI phân loại & tạo digest tóm tắt theo chủ đề: 1']   -- AI Workflow step
→ [3 Học viên đọc bản tóm tắt digest 5 phút: 5']          -- Human review
→ [4 Học viên dùng AI Q&A Bot tra cứu nhanh lời giải cũ: 1'] -- AI Workflow step

Fallback: AI tóm tắt thiếu/bỏ sót thông báo quan trọng → Học viên bấm vào link đính kèm (message link) trong bản digest để nhảy trực tiếp đến tin nhắn gốc trên Discord.
```

## Chọn card muốn pitch nhất

Card tôi muốn pitch nhất:

```text
Problem Card #1 — Tổng hợp và gán nhãn tập dữ liệu hình ảnh
```

Vì sao:

```text
1. Pain point rõ ràng & tần suất lặp lại cao: Việc các team phải gắn nhãn dữ liệu bằng tay khi gặp một bài toán mới và không có sẵn dataset phù hợp làm nó tốn rất nhiều thời gian.
2. Dễ đo lường Impact & Success metric: Có thể tính toán chính xác thời gian giảm của việc thu thập data và tính toán độ chính xác của việc AI gán nhãn tự động.
3. Ranh giới Human-AI rõ ràng: AI tự động phân loại và đề xuất nhãn nháp (Vision model), con người chỉ review và tinh chỉnh nhãn sai, đảm bảo tính khả thi cao khi triển khai thực tế.
```

Câu hỏi tôi muốn nhóm challenge:

```text
1. Làm sao để đảm bảo AI đề xuất nhãn với độ chính xác cao khi gặp tập dữ liệu có các class mới/hiếm (Out-Of-Distribution)?
2. Threshold nào của AI là phù hợp để chuyển sang cho con người review mà không gây quá tải cho người kiểm thử?
```

