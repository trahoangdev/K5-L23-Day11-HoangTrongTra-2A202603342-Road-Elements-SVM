# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): Nguyễn Quốc Hưng        Người kiểm (học viên): Hoàng Trọng Trà
Ngày: 21/11/2026                          Phiên bản guideline: Road v1.0
File được kiểm (tên + `revision` trong manifest): `NguyenQuocHung-front.zip` (task #31), `NguyenQuocHung-fisheye.zip` (task #33). Chưa nhận manifest nên chưa xác minh `revision`.
Số ảnh kiểm: 6 (+ 0 ảnh thêm)   Số nhãn đã kiểm (shape + tag): 78 (54 shape + 24 tag).


Mẫu kiểm gồm A01, A03, A07 và B02, B04, B07. Chọn 3 ảnh front và 3 ảnh fisheye để kiểm làn, vùng lái, đèn, biển và biến dạng rìa. Số mục kiểm tính theo đối tượng hoặc vị trí áp dụng từng mã. Một đối tượng có thể xuất hiện ở nhiều mã. QC1-07 tính 11 vùng lái, 4 vạch sang đường và 4 mép lề front. Mép lề fisheye kiểm ở QC1-11.

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 24 | 0 | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 6 | 0 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 13 | 0 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 10 | 1 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 13 | 1 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 13 | 0 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 19 | 1 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 16 | 6 | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 16 | 1 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 7 | 1 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 9 | 1 | chính |
| QC1-12 file | lỗi file | 2 | 0 | nhẹ / nặng |

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-05 | A03 | `lane` R1 (L1) | chính | Vạch đứt dừng trước đoạn bị che nhẹ ở phía xa và cờ `occluded=0`. Đối chiếu điểm sơn còn thấy gần xe phía trước, nối qua phần che ngắn và bật `occluded` theo checkpoint A03. |
| 2 | QC1-09 | A03 | `traffic_sign` S2 | chính | Biển hình thoi màu cam ở khoảng (812, 329) đang là `other`. Đây là biển cảnh báo công trường, dùng `warning` theo bảng nhóm biển của guideline. |
| 3 | QC1-10 | A03 | `traffic_sign` chưa gán | chính | Thiếu biển cảnh báo màu vàng huỳnh quang có hình người, ngay trên xe tải trắng bên phải, khoảng (1020, 305). Tấm biển cao rõ ràng hơn 8 px. |
| 4 | QC1-04 | A07 | `lane` R1 (L1) | chính | Đầu xa dừng gần (694, 273) dù vệt sơn trắng còn nhìn thấy phía trên điểm dừng. Kéo tới phần sơn xa nhất còn nhận diện được. |
| 5 | QC1-07 | A07 | `drivable` direct (D2) | chính | Polygon khoét theo đuôi và hai bên xe bạc ngay trước camera. Vẽ lại mặt đường đi được nếu đường trống, giữ biên làn và rào bê tông. |
| 6 | QC1-08 | B02 | `traffic_light` chưa gán | chính | Thiếu vỏ cụm đèn lớn trên cột bên trái, khoảng (131, 165). Nằm ở rìa ảnh, cần kiểm `edge_zone`. |
| 7 | QC1-08 | B02 | `traffic_light` chưa gán | chính | Thiếu cụm đèn nhỏ sáng đỏ ở mép trái, khoảng (54, 377). Cụm cao hơn 8 px, cần kiểm `edge_zone`. |
| 8 | QC1-08 | B02 | `traffic_light` chưa gán | chính | Thiếu cụm đèn nhìn từ phía sau bên trái, khoảng (268, 357). Vỏ tối nhưng tách rõ khỏi nền trời. |
| 9 | QC1-08 | B02 | `traffic_light` chưa gán | chính | Thiếu cụm đèn ở phía bên kia giao lộ, gần mặt tiền tòa nhà, khoảng (884, 293). |
| 10 | QC1-08 | B02 | `traffic_light` chưa gán | chính | Thiếu vỏ cụm đèn ngay phía trên đầu người đi bộ bên phải, khoảng (1113, 121). Cần kiểm `edge_zone`. |
| 11 | QC1-08 | B02 | `traffic_light` chưa gán | chính | Thiếu cụm đèn thứ hai sát rìa phía trên bên phải, khoảng (1145, 103). Tách hộp theo từng vỏ, kiểm `edge_zone`. |
| 12 | QC1-11 | B07 | `road_curb` C1 | chính | Đoạn cạnh giá xe đạp gấp khúc lên phần lát hè rồi quay xuống đường, thấy rõ trong vùng x≈100–170, y≈350–490. Căn lại theo cung của biên tiếp giáp mặt đường. |

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| A07 | Vùng sát rào bê tông bên trái có vạch sơn L1 riêng hay chỉ là mép lề sáng? Lint báo thiếu L1. | Chờ coach xem ảnh. Chưa tính lỗi nặng từ cảnh báo này. |
| A07 | Tag hiện là `weather=clear`. Mặt đường có vẻ ướt và phản chiếu. Coach xác nhận có nên đổi sang `rain`. | Chưa xác nhận. |
| A03, A07, B02, B04, B07 | Bảng kế hoạch theo ảnh có bao gồm những nhóm nhãn ngoài trọng tâm của slot không? | Chưa có bảng đã chốt. Chưa tính lỗi phạm vi nhóm nhãn ngoài các lỗi quan sát được. |

## Quyết định
Lỗi nặng: 0 xác nhận   Lỗi chính: 12 / 78 nhãn = 15,38 %   Lỗi nhẹ: 0   Ca chờ lead: 3
Quyết định (Release / Hold / Rework): **Rework**
Lý do (theo luật của phiếu): 15,38 % lỗi chính trên 78 nhãn đã kiểm, vượt ngưỡng 5 %. Ưu tiên bổ sung các cụm đèn B02, chỉnh vùng lái A07 và kiểm lại A03, B07. Hai ZIP đều mở được, định dạng CVAT for images 1.1, chỉ có XML. Các cảnh báo lint về hộp dưới 8 px được ghi nhận khi đọc file và không tính thành lỗi trong phiếu.

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](../../docs/qc_severity_road_v1.0.md).
