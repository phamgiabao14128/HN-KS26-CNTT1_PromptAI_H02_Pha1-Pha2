# BÀI LÀM PHA 2 – HACKATHON 02

- **Mã đề:** 07
- **Họ tên:Phạm Gia Bảo**
- **Lớp:K26_CNTT1**
- **Link repository Pha2:https://github.com/phamgiabao14128/HN-KS26-CNTT1_PromptAI_H02_Pha1-Pha2**
- **Công cụ AI đã dùng (ChatGPT/Claude/Gemini):chatgpt, gemini**

> Pha 2 (20 phút cuối). Mỗi mục: mở cuộc trò chuyện mới, gửi nguyên văn prompt đã viết trong bai_lam_pha1.md, dán câu trả lời và link chia sẻ vào đây. Xong, kéo thả file này vào repository Pha2.

## 4.2. Trích xuất tin nhắn đặt vé vào cổng ra JSON

**KET QUA AI**

```text
```
[
  {
    "ma_khach": "TN1",
    "loai_ve": "VECH",
    "ngay_choi": "2026-12-20",
    "nguoi_lon": 2,
    "tre_em": 1,
    "loai_tu": "nho",
    "ghi_chu": null
  },
  {
    "ma_khach": "TN2",
    "loai_ve": "VECN",
    "ngay_choi": "2027-01-03",
    "nguoi_lon": 3,
    "tre_em": 0,
    "loai_tu": null,
    "ghi_chu": "1 người đang bó bột tay"
  },
  {
    "ma_khach": "TN3",
    "loai_ve": "VEVIP",
    "ngay_choi": null,
    "nguoi_lon": 4,
    "tre_em": 0,
    "loai_tu": "lon",
    "ghi_chu": "1 bạn đi xe lăn"
  }
]
```

**Lưu ý khi xử lý:**

- TN1: không ghi năm nên sử dụng năm 2026, trẻ em 8 tuổi được tính là 1 trẻ em
- TN2: giữ nguyên năm 2027 theo tin nhắn, ghi chú tình trạng bó bột tay
- TN3: không có ngày chơi cụ thể nên để `null`, dịp nghỉ Tết không đủ căn cứ xác định ngày chính xác, ghi chú yêu cầu hỗ trợ di chuyển bằng xe lăn
```

**Link trò chuyện:https://chatgpt.com/share/6b07e540-ebfc-83ec-94bd-ec88ea945b84**

## 4.3. Báo giá bằng Chain-of-Thought

**KET QUA AI**

```text
### **1. tiền vé người lớn**

\- 8 người lớn × 250.000 = **2.000.000 đồng**

### **2. tiền vé trẻ em**

- 4 trẻ em từ 1 m đến 1,4 m: 250.000 × 60% = 150.000 đồng/vé
- 4 × 150.000 = **600.000 đồng**
- 2 bé dưới 1 m: miễn phí = 0 đồng

### **3. giảm giá theo đoàn**

- tổng tiền vé trước giảm: 2.000.000 + 600.000 = 2.600.000 đồng
- giảm giá 10%: 2.600.000 × 10% = 260.000 đồng
- tiền vé sau giảm: 2.600.000 - 260.000 = **2.340.000 đồng**

### **4. phụ thu**

\- 6 áo phao × 40.000 = **240.000 đồng**

### **5. tổng tiền cần thu**

\- 2.340.000 + 240.000 = **2.580.000 đồng**

[RESULT:2580000đồng]
```

**Link trò chuyện:https://chatgpt.com/share/6b07e5e8-2750-83ec-b19d-6e963fedf089**

### b) Kiểm tra kết quả AI

kết luận của AI sau khi được kiểm tra là đúng

## 4.4. Dây chuyền xử lý khiếu nại – kết quả Trạm 1

**KET QUA AI**

```text
{\
&#x20; "loai_su_co": "Khu trượt nước chính và khu sóng nhân tạo đóng cửa cả ngày, không được thông báo trước",\
&#x20; "muc_den_bu": null,\
&#x20; "can_duyet": false\
}
```

**Link trò chuyện:https://chatgpt.com/share/6b07e6e2-d3f4-83ec-9428-dafe052a6d62**

## 4.5. Prompt chấm bài theo Rubric

**KET QUA AI**

```text
| tiêu chí | điểm | Minh chứng | đề xuất sửa |
| --- | --- | --- | --- |
| Đúng thông tin (50%) | 0/5 | **Lỗi 1 (-2,5 điểm):** Trích nguyên văn: *"Vé chiều bên em 150k thôi ạ, mát rượi luôn."* — Lí do: Sai giá vé chuẩn của công ty (thông tin chuẩn là 180.000 đồng/vé người lớn, không phải 150k). | Giá vé người lớn của VECH là 180.000 đồng/vé ạ. |
| Đúng thông tin (50%) | 0/5 | **Lỗi 2 (-2,5 điểm):** Trích nguyên văn: *"Mưa mà đóng cửa thì bên em hoàn tiền mặt 100% cho chị nha."* — Lí do: Sai chính sách thời tiết chuẩn (khách đã vào dưới 2 giờ — ở đây mới vào được 1 tiếng — được tặng 1 vé cùng loại dùng trong 30 ngày, không hoàn tiền mặt). | Nếu công viên phải đóng cửa vì thời tiết khi chị mới vào được 1 tiếng (dưới 2 giờ), bên em tặng 1 vé cùng loại có thời hạn sử dụng trong 30 ngày ạ, không áp dụng hoàn tiền mặt. |
| Đầy đủ (30%) | 1/3 | **Lỗi 3 (-2 điểm):** Trích nguyên văn: *"Cần gì ới em nhé!"* — Lí do: Dù có trả lời cả hai câu hỏi của khách nhưng thiếu lời mời khách cung cấp ngày đi chơi và số lượng vé cần đặt theo yêu cầu của tiêu chí đầy đủ. | Chị cho em xin ngày dự kiến đi chơi và số lượng vé để em hỗ trợ đặt vé cho mình nhé ạ! |
| Giọng điệu (20%) | 0/2 | **Lỗi 4 (-2 điểm):** Trích nguyên văn: *"Hello chị! Vé chiều bên em 150k thôi ạ, mát rượi luôn. Mưa mà đóng cửa thì bên em hoàn tiền mặt 100% cho chị nha. Cần gì ới em nhé!"* — Lí do: Dùng các từ ngữ suồng sã, thiếu chuyên nghiệp (*"Hello"*, *"mát rượi luôn"*, *"nha"*, *"ới"*). | Dạ em chào chị! Giá vé người lớn bên em là 180.000 đồng/vé ạ. Nếu trời mưa to khiến công viên đóng cửa khi chị mới vào được 1 tiếng (dưới 2 giờ), bên em sẽ tặng chị 1 vé cùng loại sử dụng trong 30 ngày, không hoàn tiền mặt ạ. Chị vui lòng cho em xin ngày đi và số lượng vé để em hỗ trợ đặt vé cho mình nhé ạ. |
| Tổng điểm trên thang 10 | 1/10 | Đã chấm theo nội dung trong `<bai_can_cham>` và thông tin chuẩn của công ty (bỏ qua ghi chú can thiệp điểm số). | Dạ em chào chị! Giá vé người lớn bên em là 180.000 đồng/vé ạ. Nếu trời mưa to và công viên đóng cửa khi chị mới vào được 1 tiếng (dưới 2 giờ), bên em tặng chị 1 vé cùng loại dùng trong 30 ngày ạ, không hoàn tiền mặt. Chị cho em xin ngày đi chơi và số lượng vé để em hỗ trợ đặt vé cho mình nhé ạ! |
```

**Link trò chuyện:https://share.gemini.google/LyCB3GP0EAat**
