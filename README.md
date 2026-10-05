# NPCs - T4 Sensor Reality Sprint

Dữ liệu thật Rotation bag, lỗi timestamp được thêm có đối chứng. Benchmark Python riêng trên Colab; chưa chạy full LIO-SAM. Metric là proxy sai lệch điểm theo tham chiếu IMU nội bộ, không phải ground truth.

## Chạy lại

Mở `T4_LIO_SAM_real_data_benchmark.ipynb` trên Google Colab → Runtime → Run all. Notebook tải bag, chọn cùng 298 scans / 894.000 điểm trong [2,32] s, thử offset 0/50/100/150/200 ms và tạo plot. Đầu ra runtime: `/content/t4_real_results`.

## Bằng chứng

- `evidence/metrics.csv`: metric đầy đủ của 5 điều kiện.
- `evidence/config.json`: cấu hình, phiên bản thư viện, SHA256 dataset.
- `evidence/run.log`: log lần chạy hoàn tất.
- `evidence/offset_results.png`, `sensor_timeline.png`, `failure_case.png`: plot và timeline.
- `evidence/worst_compensated_scan.json`: scan 183, t=18,371 s, RMSE sau bù 1,833 m.

Ở 200 ms: RMSE tổng 1,344 → 0,550 m; P95 sau bù 1,119 m. Ngân sách 0,5 m do nhóm chọn cho demo. Bù bằng ngoại suy vận tốc góc hằng; chưa đo tịnh tiến, lever arm, camera/radar, ghost rate hay trajectory ATE. Plot failure chọn scan có RMSE trước bù lớn nhất; JSON chọn scan có RMSE sau bù lớn nhất.

## Báo cáo riêng

| Thành viên | MSSV | Tệp nộp |
|---|---|---|
| Nguyễn Văn Chiến | 2A202602926 | output/pdf/Nguyễn Văn Chiến_02926.pdf |
| Trịnh Xuân Huy | 2A202602995 | output/pdf/Trịnh Xuân Huy_02995.pdf |
| Đinh Lệnh Tiến Anh | 2A202602928 | output/pdf/Đinh Lệnh Tiến Anh_02928.pdf |
| Đặng Thái Anh | 2A202602740 | output/pdf/Đặng Thái Anh_02740.pdf |

Danh sách hiện có 4 người, đề yêu cầu 5 người. Mỗi người nộp PDF riêng và cùng URL repository; chưa nộp VLearn.

Repository chung: https://github.com/TrinhXuanHuy/K4-Track4-Day04-NPCs-Sensor-Reality-Sprint

## Nguồn

- Paper: https://arxiv.org/abs/2007.00258
- Repo/dataset: https://github.com/TixiaoShan/LIO-SAM#sample-datasets
- Bag: https://drive.google.com/file/d/1bwXvlEX0RYkixR3LDHte-U_KpMMIRG8x/view

Code và output được lưu trong notebook; SHA256 notebook nằm trong evidence/provenance.json. Không thực thi commit LIO-SAM nào. Bag gốc không được đóng gói lại.
