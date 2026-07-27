# Phase 7 — Individual Reflection (15')
## Tôi đã tham gia vào phần nào?

| Hoạt động | Tôi đã làm gì? | Kết quả / ảnh hưởng |
|---|---|---|
| Scan cá nhân | Đưa ra 5 problems | Nhóm có nhiều candidate về technical/workflow để xem xét. |
| Pitch Problem Card | Pitch bài "Tổng hợp và gán nhãn tập dữ liệu hình ảnh". | Bị loại vì cả nhóm nhận ra đã có nhiều công cụ giải quyết bài này (Label Studio, Roboflow). |
| Challenge bài của bạn khác | Phản biện bài #11 (Review PR) của Minh rằng: "Dev sẽ tự trả lời thay người dùng nên không ai kiểm được, còn bài #6 buộc phải đi hỏi người thật". | Nhóm nhận ra rủi ro "tự biên tự diễn", quyết định chuyển sang chốt bài #6 của Dương. |
| Gom trùng / cluster | Nhận diện điểm giống nhau giữa các bài toán . | Giúp nhóm gom 12 bài về 4 cluster, loại bỏ nhanh cluster B. |
| Chọn candidate problem | Bỏ qua bài của mình, ủng hộ chọn bài #6 của Dương. | Nhóm chọn bài có baseline đo được và có rủi ro thực tế. |
| Validation / research | Cùng nhóm kiểm chứng tool ATS và HireVue. | Rút ra bài học: phần parse CV đã có người làm, điểm nghẽn thật sự nằm ở Match Score.|
| Workflow nhóm | Cùng vẽ sơ đồ Mermaid, bổ sung bước chặn chủ đề (guardrail). | Ranh giới Human-AI rõ ràng hơn, 14 bước chia theo Rule/Workflow/Agent. |
| Problem Statement | Viết lại Boundary và tìm Success Metric phù hợp. | Đổi metric 1 chiều thành thêm metric đối trọng (đo false negative và tỉ lệ bỏ ngang). |
| Rule / Workflow / Agent | Giúp nhóm phân tích 14 bước qua ma trận. | Làm rõ Workflow giải quyết 13/14 bước, Agent chỉ dành riêng cho B2. |
| Decision | Đồng thuận quyết định Go (Workflow) và Not Yet (Agent). | Hệ thống bớt rủi ro, không tự động hóa mù quáng khi chưa rõ số lượng ứng viên phỏng vấn. |

## Bảng dùng AI trong reflection

| Phase | Tôi dùng AI để làm gì? | AI hữu ích ở đâu? | AI sai/hời hợt ở đâu? | Tôi sửa gì bằng nhận định của mình? |
|---|---|---|---|---|
| Scan | Mở rộng ý tưởng từ các pain point của Dev. | Gợi ý được nhiều use-case về automation. | Vài ý quá rộng, không có workflow thật. | Chỉ lọc và giữ lại bài toán có số liệu như "gán nhãn dữ liệu". |
| Problem Card | Format lại workflow thành các bước rõ ràng. | Dễ hình dung bottleneck. | Thường gộp chung AI và người vào 1 bước. | Tách rõ Human Boundary và AI Workflow step. |
| Workflow | Chuyển mô tả text thành code sơ đồ Mermaid. | Tiết kiệm nhiều thời gian vẽ. | Bỏ quên mũi tên đứt nét (fallback). | Tự thêm lại luồng rẽ nhánh và các note về fallback. |
| Research | Tìm case study về ATS và phỏng vấn AI. | Đưa ra case HireVue và Amazon 2018. | Đưa ra thông tin chung chung, không có link. | Bắt buộc tìm link gốc để verify, bỏ các claim không có nguồn. |
| Problem Statement | Prompt AI đóng vai trò phản biện các field. | Chỉ ra Success Metric chưa đủ chặt chẽ. | Đề xuất giải pháp bằng Agent ngay từ đầu. | Nhóm bác bỏ, hạ mức kì vọng về Workflow trước. |
| Rule / Workflow / Agent | Đánh giá độ mơ hồ/phức tạp qua ma trận. | Phân tích tốt yếu tố tái lập của Output. | AI mặc định coi bài toán là Mơ hồ cao. | Ép AI tách làm 2 (Giai đoạn A mơ hồ thấp, B mơ hồ cao). |
| Decision | (Không dùng AI, nhóm tự thảo luận chốt). | - | - | Giữ vững quan điểm Not Yet cho Agent. |

## Reflection câu hỏi mở

- **Tôi học được gì khi nghe top 3 problems của các bạn khác?**
  Tôi học được sự khác biệt giữa nghẽn "giờ" và nghẽn "chất lượng". Trước đây tôi nghĩ cái tốn nhiều thời gian nhất là cái cần giải quyết nhất (như bài đọc CV hay gán nhãn ảnh). Nhưng bài của Dương (HR) cho thấy chỗ đáng giải quyết nhất là khâu "Match Score" – vì nó không tái lập được và phụ thuộc vào cảm tính.

- **Nhóm có lúc nào bị solution-first không?**
  Rất nhiều. Ban đầu thấy bài CV là chúng tôi nghĩ ngay đến AI Resume Parser. Nhưng sau đó nhóm nhận ra Parser đã có rất nhiều giải pháp trên thị trường (ATS). Việc đâm đầu vào Parser là solution-first. Khi xoay trục sang việc dùng AI chấm "Match Score theo Rubric" thì nhóm mới thực sự giải quyết đúng điểm đau (problem-first).

- **Tôi có thay đổi ý kiến sau khi bị challenge không?**
  Có. Ban đầu tôi pitch bài gán nhãn ảnh của mình vì impact của nó lên tới 1-2 tuần/đợt. Nhưng nhóm chỉ ra rằng bài này đã có một hệ sinh thái tool (Label Studio, Active Learning). Tôi đồng ý từ bỏ bài của mình để nhóm không "phát minh lại bánh xe".

- **Tôi đóng góp gì thật sự vào artifact cuối?**
  Đóng góp lớn nhất của tôi là câu challenge cứu nhóm khỏi việc đâm đầu vào bài Review PR (#11) của Minh: *"chính vì cả nhóm đều là dev nên sẽ tự trả lời thay người dùng và không ai kiểm được, còn bài #6 buộc phải đi hỏi mới biết."* Lời phản biện này giúp nhóm chuyển hướng chọn bài toán có actor thực tế và kiểm chứng được bằng dữ liệu thật.

- **Điều khó nhất khi viết Problem Statement là gì?**
  Tìm metric đối trọng. Việc tối ưu từ 620' xuống 45' rất dễ làm, nhưng hệ quả là AI có thể loại nhầm người giỏi một cách âm thầm. Việc nghĩ ra và ép vào metric "không có ứng viên nào người tự chọn mà hệ thống xếp ngoài Top 10" (đo False Negative bằng cách bốc 5 CV ngoài Top 10 đọc tay) là công đoạn khó nhất.

- **Nếu làm lại, tôi sẽ challenge nhóm mạnh hơn ở điểm nào?**
  Tôi sẽ yêu cầu Dương gọi điện xác minh ngay lập tức con số 30-50 ứng viên ở vòng phỏng vấn sơ loại (thay vì để nó ở trạng thái giả định gây mâu thuẫn). Sự chần chừ này khiến nhóm phải ra quyết định "Not Yet" cho phần AI Agent thay vì có thể chốt Go ngay tại chỗ.
