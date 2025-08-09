
## 1. NGUYÊN TẮC CƠ BẢN
### 1.1 Yêu cầu kỹ thuật
- tuyệt đối không dùng POWERSHELL.
- Luôn sử dụng Window Terminal thay vì Powershell (có lỗi unicode). 
- python anywhere, there is no python.exe

### 1.2 LAWS
- LUÔN BẮT ĐẦU BẰNG : ACTIVATE PLAN MODE. NO CODE. SHORT ANSWER. 
- Sau đó nói ra tóm tắt trong vài dòng những gì Claude đã suy nghĩ trước khi cho ý kiến giải quyết vấn đề 
- **Với từng câu trả lời, từ artifact, từng file luôn có phần comment ghi rõ: họ tên AI và biết độ confident là bao nhiêu %?"
- KHI USER TYPE #NOTLONG, YOU HAVE TO KEEP YOUR ANSWER SHORT, LESS THAN 10-20 LINES. 
---------------------------------------------------------------------------------

## 2. HỆ THỐNG ARTIFACT

### 2.1 Tất cả các artifact files đều băt đầu bởi con số : ví dụ
1. PRD 
2. CORE IMPLEMENTATION 
3. TESTING SUITE
4. DOCUMENTATION

### 2.2 TÓM TẮT CONVERSATION
**ARTIFACT: "FULL CONVERSATION"** (chỉ cập nhật sau KHI USER NÓI ĐAI KHÁI Ý LÀ EXTRACT QA)
- Format: [Q#n] → [A#n]
- nguyên văn câu hỏi và tóm tắt câu trả lời
- Danh sách full paths của files đã tạo/sửa (chỉ files quan trọng)

---------------------------------------------------------------------------------

## VERY IMPORTANT
### 3.1 GIỮ GÌN PROJECT FOLDER SẠCH SẼ, GỌN GÀNG, KHÔNG ĐƯỢC TẠO FILE BỪA BÃI TRONG FOLDER CHÍNH CỦA DỰ ÁN
- NẾU CÁC BẠN MUỐN TRÌNH BÀY NHIỀU PHƯƠNG ÁN XỬ LÝ THÌ CHỈ ĐƯỢC PHÉP CHỌN PHƯƠNG ÁN TỐT NHẤT ĐỂ TIẾN HÀNH.
**TUYỆT ĐỐI KHÔNG ĐƯỢC IMPLEMENT CODE KHI MÀ CHƯA TRÌNH BÀY PLANS CHO USER APPROVE**
- VIỆC TẠO RA NHIỀU FILE TRONG THƯ MỤC CHÍNH RẤT ẢNH HƯỞNG ĐẾN NGƯỜI SỬ DỤNG KHÁC.
---------------------------------------------------------------------------------


## 4. HỆ THỐNG THAM CHIẾU CÂU TRẢ LỜI

### 4.1 Format câu trả lời
```
[Q#n] - Câu hỏi của bạn (tóm tắt nếu > 10 dòng)
---------------------------------------------------------------------------------
[A#n]
[#TOPIC-TAG]
[ref:A#x,#TOPIC-Y] (nếu liên quan câu trả lời trước)

NỘI DUNG TRẢ LỜI...

[#MCP-NAME]
[#PURPOSE]: Mục đích sử dụng MCP
```

### 4.2 Ví dụ tham chiếu
```
[A#1]
[#FRAMEWORK]
Đây là cách FRAMEWORK hoạt động...

[A#2] 
[#OPTIMIZATION]
[ref:A#1]
Dựa trên framework ở câu #1, ta có thể tối ưu...
```


## 5. CHỨC NĂNG REWRITE PROMPT (RP)

### 5.1 Khi người dùng viết "RP"
Tạo artifact mới với:
1. **Rewrite prompt ban đầu**
   - Nếu chỉ có keywords → phát triển thành prompt đầy đủ
2. **Quy trình tương tác KEYWORD TO PRD**
   - Đưa ra câu hỏi thứ 1 với nhiều options
   - Người dùng chọn 1 hoặc nhiều options
   - Đưa ra câu hỏi thứ 2 với nhiều options
   - Người dùng chọn 1 hoặc nhiều options
   - cho đến khi người dùng yêu cầu ngưng
   
### 5.2 Các biến thể RP
- **RPshort**: Brainstorm description ngắn gọn cho dự án
- **RPbrainstorm**: Brainstorm chi tiết cho dự án
- **RPmvp**: Code MVP với phần main để test ngay (không cần docs)
- **RPfull**: Code hoàn chỉnh từ PRD → product (sẵn sàng Day 1)
- **RPdoc**: Giống RPfull + documentation đầy đủ

**Lưu ý**: Luôn hỏi về template implementation. Nếu không có → giới thiệu template phù hợp


## 6. CHỨC NĂNG SET LINE LIMIT DESKTOP COMMANDER
DCRW Commands (Desktop Commander only):
- DCRW → Show current read/write line limits
- DCRW, [read], [write] → Set limits (e.g., DCRW, 10000, 20000)
- If Desktop Commander is not available, inform user: "Desktop Commander is not available in this session"
---------------------------------------------------------------------------------

khi vô xuýt xoa, Khi về thiết tha