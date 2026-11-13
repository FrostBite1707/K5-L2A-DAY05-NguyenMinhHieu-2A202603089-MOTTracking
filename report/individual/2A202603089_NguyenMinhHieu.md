# Báo cáo cá nhân — NguyenMinhHieu-2A202603089

Đoạn video: MOT17-09, 150 frame (frame 1–150), nguồn MOTChallenge, giấy phép CC BY-NC-SA 3.0.

## 0. Thông tin học viên

- Họ tên: Nguyen Minh Hieu
- MSSV: 2A202603089
- Mã đề (A/B/C): chưa có thông tin
- Email: chưa có thông tin
- Link repository: https://github.com/FrostBite1707/K5-L2-DAY05-NguyenMinhHieu-2A202603089-MOTTracking
- Giờ bắt đầu: 16h 13/11
- Giờ kết thúc: 18h 13/11

## 1. Xem trước đoạn video (CP0)

| Mã | Frame xuất hiện | Frame cuối thấy được | Rẽ / dừng / đổi tốc độ ở frame | Bị che ở frame | Ghi chú |
|---|---|---|---|---|---|
| P1 |0 |149 |100 |0–59, 100–118 |Bị che bởi người ở khoảng frame 40–59; các frame còn lại bị che bởi bàn ghế|
| P2 |40 |149 |80 |40–109 |Bị che gần hết người ở các frame 40–60 |
| P3 |0 |149 |- |- |Không có sự kiện nào |
| P4 |0 |149 |- |0–69 |Chỉ xuất hiện đầy đủ từ frame 70|
| P5 |0 |148 |30 |109–118, 135–139 |Khuất hẳn ở 119–134 rồi hiện lại; kết thúc ở frame 148|

## 2. Keyframe và thời gian (CP1, CP4)

Số liệu keyframe và số frame có mặt lấy từ `src/check_submission.py`. P1–P5 khớp với CVAT track ID 0–4 theo thứ tự trong báo cáo; frame là chỉ số CVAT, bắt đầu từ 0.

| Mã | Số keyframe | Keyframe ở frame | Số frame có mặt | Keyframe / 100 frame | Thời gian (phút) | Chỗ khó |
|---|---:|---|---:|---:|---|---|
| P1 | 17 | 0, 10, 20, 30, 50, 60, 70, 80, 90, 99, 100, 110, 119, 120, 130, 140, 149 | 150 | 11.3 |20 | - |
| P2 | 12 | 40, 50, 60, 70, 80, 90, 100, 110, 120, 130, 140, 149 | 110 | 10.9 |15 |Thời điểm xuất hiện bị che mất >60% khó ước lượng chiều cao |
| P3 | 16 | 0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100, 110, 120, 130, 140, 149 | 150 | 10.7 |15 | - |
| P4 | 16 | 0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100, 110, 120, 130, 140, 149 | 150 | 10.7 |15 | - |
| P5 | 10 | 0, 10, 20, 30, 40, 50, 109, 110, 135, 140 | 133 | 7.5 |20 |Biến mất rồi xuất hiện lại |
| **Tổng** | **71** | | **693** | **10.2** | 65 | |

Keyframe / 100 frame của cả bài = 71 ÷ 693 × 100 = **10.2**.

Bạn đặt keyframe nhiều nhất ở P1 (17 keyframe). Chưa có ghi chú về lý do chọn các vị trí keyframe.

## 3. Đoạn bị che (CP2)

Đối chiếu annotations.xml: P5 (CVAT track 4) có `occluded` ở frame 109–118 và 135–139, `outside` ở frame 119–134, rồi xuất hiện lại cùng track ở frame 135. Khoảng khuất hẳn là 16 frame (khoảng 0,53 giây ở 30 fps). CP2 trong hướng dẫn yêu cầu theo dõi P1; đoạn khuất hẳn tìm thấy trong file xuất là của P5, nên cần xác nhận với coach liệu có cần làm lại CP2 trên P1. Ảnh chụp màn hình chưa có trong workspace.

Người bị che: `P5`

| Mốc | Frame |
|---|---:|
| Bắt đầu bị che một phần (bật `occluded`) |109 |
| Mất hẳn (bật `outside`) |119 |
| Hiện lại (tắt `outside`) |135 |
| Thấy rõ trở lại (tắt `occluded`) |140 |

- Thời gian khuất hẳn: 16 frame = khoảng 0,53 giây (30 fps).
- Quyết định trong nhãn: giữ cùng ID.
- Lý do: khoảng vắng dưới 60 frame; track tiếp tục với cùng ID ở frame 135. Cần xác nhận ngoại hình và hướng/tốc độ khi hiện lại bằng cách xem video.

## 4. Tự review ID (CP3)

Chưa có ghi chú tự review hai lượt trong các file hiện có.

| Frame | Mã người | Loại lỗi | Mô tả một câu | Phát hiện ở lượt | Đã sửa? |
|---:|---|---|---|---|---|
| | | | | | |
| | | | | | |
| | | | | | |

| `id_switch` | `fragmentation` | `lost` | `merge` | `false_track` | `drift` | `flag` |
|---:|---:|---:|---:|---:|---:|---:|
| | | | | | | |

## 5. File xuất và kết quả tự kiểm (CP4)

| Kiểm tra | Kết quả |
|---|---|
| Tên file MOT 1.1 | `NguyenMinhHieu_mot.zip` |
| Tên file CVAT for video 1.1 | `NguyenMinhHieu_cvat_video.zip` |
| Số track ID khác nhau trong `gt/gt.txt` | 5 |
| Frame `outside` không có dòng trong `gt.txt` | Đúng theo kiểm tra của script |
| Job đã completed trên CVAT máy cá nhân | Yes |

Dán phần tóm tắt in ra từ `src/check_submission.py`:

```text
Số frame in theo CVAT (bắt đầu từ 0). Trong gt.txt, frame_id = frame CVAT + 1.

=== File MOT 1.1: NguyenMinhHieu_mot.zip ===
  Số track ID: 5   |   Tổng số box: 693
  [OK]        Đúng 5 track ID.

  Track | Frame có mặt | Số frame | Đoạn vắng (outside)
      1 |   0–149      |      150 | -
      2 |   0–149      |      150 | -
      3 |   0–149      |      150 | -
      4 |   0–148      |      133 | 119–134
      5 |  40–149      |      110 | -

=== File CVAT for video 1.1: NguyenMinhHieu_cvat_video.zip ===

  Track | Nhãn   | Frame thấy | Keyframe | KF/100 frame | Frame occluded | Lần bật outside
      0 | person |        150 |       17 |         11.3 |             79 |               0
      1 | person |        110 |       12 |         10.9 |             70 |               0
      2 | person |        150 |       16 |         10.7 |              0 |               0
      3 | person |        150 |       16 |         10.7 |             70 |               0
      4 | person |        133 |       10 |          7.5 |             15 |               2
              Track 4: keyframe ở frame [0, 10, 20, 30, 40, 50, 109, 110, 135, 140]

  Tổng: 71 keyframe / 693 frame có mặt = 10.2 keyframe / 100 frame
  [OK]        Đọc được 5 track từ annotations.xml.

=== Tóm tắt ===
  Lỗi: 0   |   Cảnh báo: 0
  Đạt. Dán phần tóm tắt này vào báo cáo mục 5.
```

## 6. Ba câu kết

1. Nếu làm lại, bạn sẽ đặt keyframe ở đâu khác? Vì sao?
Ví dụ: “Tôi sẽ thêm keyframe quanh frame 80 vì người đổi hướng và box bắt đầu trôi.”

2. Có đoạn nào bạn phân vân giữ ID cũ hay tạo ID mới? Bạn quyết định thế nào?
Ví dụ: “P5 khuất 16 frame rồi hiện lại. Tôi giữ ID cũ vì thời gian khuất dưới 60 frame và người hiện lại đúng hướng.”

3. Một lỗi ID có thể ảnh hưởng thế nào đến xe tự lái? Lỗi đó ảnh hưởng MOTA hay IDF1 nhiều hơn?
Ví dụ: “Nếu ID của người đi bộ bị đổi, xe có thể dự đoán sai quỹ đạo của họ. Lỗi đổi ID มัก ảnh hưởng IDF1 nhiều hơn vì IDF1 đánh giá việc duy trì đúng danh tính qua các frame.”

## Bonus (nếu làm)

Chưa có thông tin về bonus.

## 7. Tài liệu tham khảo và công cụ AI đã dùng

Chưa có thông tin về tài liệu tham khảo hoặc công cụ AI đã dùng.
