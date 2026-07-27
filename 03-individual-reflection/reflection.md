# Phase 7 — Individual Reflection (15')
## Tôi đã tham gia vào phần nào?

| Hoạt động | Tôi đã làm gì? | Kết quả / ảnh hưởng |
|---|---|---|
| Scan cá nhân | Đưa ra 5 problems | Nhóm có nhiều candidate về technical/workflow để xem xét |
| Pitch Problem Card | Pitch Tổng hợp và gán nhãn tập dữ liệu hình ảnh| Bị loại vì cả nhóm nhận thấy nếu dùng ai để gợi ý nhãn thì tính xác không cao, do đó vẫn phải tốn thời gian rà soát lại |
| Challenge bài của bạn khác | Phản biện bài #11 của Minh rằng: "Dev sẽ tự trả lời thay người dùng nên không ai kiểm được, còn bài #6 buộc phải đi hỏi người thật" | Nhóm nhận thấy rủi ro "tự biên tự diễn", nên đã quyết định chọn bài #6 của Dương |
| Gom trùng / cluster | Nhận diện điểm giống nhau giữa các bài toán | Giúp nhóm gom 12 bài về 4 cluster, loại bỏ nhanh cluster B |
| Chọn candidate problem | Bỏ qua bài của mình, ủng hộ chọn bài #6 của Dương | Nhóm chọn bài có baseline đo được và có rủi ro thực tế |
| Validation / research | Cùng nhóm kiểm chứng tool ATS và HireVue | Rút ra bài học: phần parse CV đã có người làm, điểm nghẽn thật sự nằm ở Match Score |
| Workflow nhóm | Cùng vẽ sơ đồ Mermaid, bổ sung bước chặn chủ đề (guardrail) | Ranh giới Human-AI rõ ràng hơn, 14 bước chia theo Rule/Workflow/Agent |
| Problem Statement | Viết lại Boundary và tìm Success Metric phù hợp | Đổi metric 1 chiều thành thêm metric đối trọng (đo false negative và tỉ lệ bỏ ngang) |
| Rule / Workflow / Agent | Giúp nhóm phân tích 14 bước qua ma trận | Làm rõ Workflow giải quyết 13/14 bước, Agent chỉ dành riêng cho B2 |
| Decision | Đồng thuận quyết định Go (Workflow) và Not Yet (Agent) | Hệ thống bớt rủi ro, không tự động hóa mù quáng khi chưa rõ số lượng ứng viên phỏng vấn |

## Bảng dùng AI trong reflection

| Phase | Tôi dùng AI để làm gì? | AI hữu ích ở đâu? | AI sai/hời hợt ở đâu? | Tôi sửa gì bằng nhận định của mình? |
|---|---|---|---|---|
| Scan | Gợi ý cách tìm kiếm ý tưởng | Gợi ý được nhiều use-case về automation | Vài ý quá rộng, không có workflow thật | Chỉ lọc và giữ lại bài toán có số liệu |
| Problem Card | Format lại workflow thành các bước rõ ràng | Dễ hình dung bottleneck | Thường gộp chung AI và người vào 1 bước | Tách rõ Human Boundary và AI Workflow step |
| Workflow | Chuyển mô tả text thành code sơ đồ ASCII | Tiết kiệm nhiều thời gian vẽ | Bỏ sót mũi tên đứt nét (fallback) | Tự thêm lại luồng rẽ nhánh và các note về fallback |
| Research | Tìm case study về ATS và phỏng vấn AI | Đưa ra case HireVue và Amazon 2018. | Đưa ra thông tin chung chung, không có link | Bắt buộc tìm link gốc để verify, bỏ các claim không có nguồn |
| Problem Statement | Prompt AI đóng vai trò phản biện các field | Chỉ ra Success Metric chưa đủ chặt chẽ | Đề xuất giải pháp bằng Agent ngay từ đầu | Nhóm bác bỏ, hạ mức kì vọng về Workflow trước |
| Rule / Workflow / Agent | Đánh giá độ phức tạp qua ma trận | Phân tích tốt yếu tố tái lập của Output | AI mặc định coi bài toán là Mơ hồ cao | Ép AI tách làm 2 (Giai đoạn A mơ hồ thấp, Giai đoạn B mơ hồ cao) |
| Decision | (Không dùng AI, nhóm tự thảo luận chốt) | - | - | Giữ vững quan điểm Not Yet cho Agent |

## Bài học của Hiếu

- **Problem tốt là problem có workflow và metric rõ ràng, không nhất thiết là problem tốn nhiều giờ nhất.**
- **Khi thấy bài CV, phản xạ đầu tiên là dùng AI Resume Parser, nhưng thực tế ATS đã làm việc đó.**
- **Bài học về Boundary: Nếu để các Dev tự làm bài review PR (như bài #11) thì sẽ tự trả lời thay user. Chọn bài HR bắt buộc nhóm phải đối diện với hậu quả thực tế: "loại nhầm một con người".**
- **Agent không phải liều thuốc vạn năng: Phân tách 14 bước ra mới thấy 13 bước chỉ cần Workflow. Việc chỉ định đúng 1 bước (B2) cần Agent làm lập luận vững hơn rất nhiều so với gán Agent cho cả quy trình.**

Nếu làm lại:

```text
Tôi sẽ hỏi lại Dương xác nhận ngay lập tức con số thật sự là 5 ứng viên hay 30-50 ứng viên vòng screening call. Số liệu đó quyết định lý do tồn tại của Agent; nếu có số sớm, nhóm có thể đã tự tin chốt "Go" thay vì phải "Not Yet".
```