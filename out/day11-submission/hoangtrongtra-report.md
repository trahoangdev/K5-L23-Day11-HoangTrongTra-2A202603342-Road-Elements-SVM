# Báo cáo cá nhân — Ngày 11
Họ tên: Hoàng Trọng Trà             Mã học viên: 2A202603342
Phiên bản CVAT (Help → About): 2.74.1\
Guideline: Road v1.0    Lần nộp (`revision` trong manifest): 3\
Thời điểm export (ngày giờ trên CVAT): 21/11/2026 (UTC+7, theo XML CVAT), front 10:23, front-extra 09:34, fisheye 10:25, fisheye-extra 10:22\
Số lần nộp lại sau Rework: 0 (revision 3 cập nhật sau tự kiểm)

## 1. Kiểm project
| Mục | Đúng như guideline Road v1.0? | Ghi chú |
| --- | --- | --- |
| 6 label, đúng kiểu | Có | `lane`, `road_curb` dùng polyline. `crosswalk`, `drivable` dùng polygon. `traffic_light`, `traffic_sign` dùng rectangle. |
| Thuộc tính và giá trị | Có | Đã đối chiếu Raw Labels của project #39 với `configs/road_v1_labels.json`. |
| 4 tag ảnh | Có | Đủ `camera`, `timeofday`, `weather`, `source` trên 28/28 ảnh. Giá trị `camera` khớp từng ảnh. Mỗi tag có thuộc tính select `value`. |

Cách kết thúc polyline trên bản CVAT này: Bấm **Done** ở thanh trên sau khi đặt điểm cuối, hoặc nhấn `N`.\
Cách đặt tag ảnh trên bản CVAT này: Chọn công cụ **Tag**, chọn nhãn, thêm tag rồi mở **Details** để chọn `value`. Đặt `camera` trước, sau đó đặt ba tag còn lại.

Đã kiểm đủ 5 file theo `SUBMISSION.md` và `docs/delivery_road_v1.0.md`. Bốn job #23–#26 ở trạng thái **Completed**. Mục 5 ghi kết quả kiểm hai ZIP.

## 2. Số lượng đã gán
| Task | Ảnh | lane | road_curb | crosswalk | drivable | traffic_light | traffic_sign |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| front | 12 | 25 | 1 | 2 | 4 | 23 | 19 |
| front-extra (đã làm 4 / 4) | 4 | 11 | 0 | 1 | 2 | 12 | 0 |
| fisheye | 8 | 6 | 2 | 7 | 3 | 6 | 1 |
| fisheye-extra (đã làm 4 / 4) | 4 | 0 | 0 | 3 | 1 | 2 | 0 |

## 3. Bảng ca khó
| Ảnh | Nhãn | Phân vân giữa | Đã chọn | Lý do |
| --- | --- | --- | --- | --- |
| A03 | `lane` R1 | Dừng trước xe che hoặc nối qua đoạn bị che | Nối đoạn ngắn, bật `occluded` | Các đoạn sơn hai bên chỗ che nằm trên cùng một vạch đứt. |
| A04 | `lane` L1 | Vẽ hai nét riêng hoặc một polyline ở giữa | Một polyline `solid / yellow / double` | Hai dải sơn tạo thành vạch vàng đôi. |
| A05 | `lane` L1 | Mép dải đỗ và biên làn xe | Chốt không gán theo tự kiểm QC1-02 | Phía trái là dải xe đỗ. Trên phần mặt đường nhìn thấy không nhận diện được vệt sơn phân làn. |
| A05 | `lane` R1 | Mép dải đỗ và biên làn xe | Chốt không gán theo tự kiểm QC1-02 | Phía phải là dải xe đỗ và mép vỉa đã gán road_curb. Không thấy vệt sơn riêng làm biên làn. |
| A06 | `lane` R1 | Vạch có thể thuộc làn đang đi hoặc đường cắt ngang | Chốt không gán theo tự kiểm QC1-02 | Các nét trắng qua giao lộ là vạch sang đường. Nét trắng sát mép phải chạy theo nhánh đường cắt ngang, không xác định được R1 của làn đang đi. |
| A07 | `lane` L1 | Vệt sơn hoặc dải lề sáng cạnh rào bê tông | Chốt không gán theo tự kiểm QC1-02 | Dải sáng bám theo chân rào bê tông. Không thấy vệt sơn tách riêng để đặt tim L1. |
| A07 | `traffic_light` | Xanh hoặc không xác định được màu | `unknown` cho cụm nhỏ phía xa | Thấy vỏ đèn nhưng phần phát sáng quá mờ để xác định màu. |
| A08 | `lane` L1 | Vạch sơn mờ hoặc đường nối mặt đường | Chốt không gán theo tự kiểm QC1-02 | Nét mờ qua giao lộ từ gần (253, 423) đến khoảng (482, 325) chưa phân biệt được với đường nối mặt đường. Vạch trắng rõ phía xa bên trái nằm ngoài làn đang đi. |
| A09 | `lane` R1 | Vạch mờ hoặc bóng và phản chiếu kính | Chốt không gán theo tự kiểm QC1-02 | Khu vực bên phải có bóng đổ và phản chiếu kính. Không nhận diện được vệt sơn xác định biên phải của làn đang đi. |
| A09 | `traffic_sign` (2 biển bên phải) | Nhóm biển theo chức năng hoặc `other` | Giữ `group=other` cho cả hai | Thấy mép tấm biển, nhưng phần chữ và ký hiệu bị mờ. Chưa đủ căn cứ để xác định chức năng. |
| B03 | `lane` L1 | Nối qua khoảng trống dài hoặc chỉ lấy đoạn xa | Bản xuất hiện tại có 4 điểm ở đoạn xa | Cần đối chiếu đoạn sơn gần xe trước khi kết luận vạch đã đủ từ gần đến xa. |
| B09 | `traffic_light`, `traffic_sign`, `lane` | Cụm đèn nhìn nghiêng hoặc từ sau, biển và vạch sát mép | Gán hai vỏ đèn nhận diện được với `color=unknown` | Phần biển và vạch làn chưa đủ rõ để xác định. |
| B11 | `lane` | Vạch dọc của làn hay biên ô đỗ | Giữ bốn thẻ ảnh | Các nét nhìn rõ là vạch ô đỗ và vạch kẻ vùng đệm của ô đỗ. |
| B02 | `traffic_sign` trên đảo giao thông | Mặt sau của biển, chưa thấy ký hiệu | `group=other`, `facing=back` | Thấy vỏ và cột biển. Hướng camera chỉ thấy mặt sau. |

## 4. Phiếu QC 1 nhận được
Bạn kiểm lô của tôi: Nguyễn Quốc Hưng.  Quyết định nhận được: **Rework** (phiếu ngày 21/11/2026, ghi revision 1).

| Mã lỗi | Số lỗi | Đồng ý? | Đã sửa? |
| --- | ---: | --- | --- |
| QC1-02 | 1 | A08 L1 — Tự đối chiếu chưa xác định được vệt sơn trên nét mờ qua giao lộ. Cần chỉ rõ tim vạch trên ảnh nếu người kiểm xác định đây là L1. | Chốt không gán theo tự kiểm |
| QC1-06 | 2 | A01 L2 — Giữ `kind=double` vì ảnh thấy hai dải sơn trắng song song bên trái. A01 R2 — Giữ `color=yellow` vì vạch sát lề phải có màu vàng trên ảnh gốc. | Không đổi hai thuộc tính |
| QC1-01 | 1 | A07 — Giữ `weather=rain` vì mặt đường ướt rõ và phản chiếu ánh sáng. Road v1.0 dùng `rain` khi mặt đường ướt rõ do mưa. | Không đổi tag |

Phiếu ghi 1 lỗi nặng, 2 lỗi chính và 1 lỗi nhẹ. Phiếu tính 2/64 nhãn là 3,125%. Hai ZIP lưu từ revision 1 có 62 nhãn trên đúng 6 ảnh được nêu. Cần đối chiếu bản ZIP Hưng đã dùng để làm rõ chênh lệch. Phiếu ghi A07 L1 được miễn vì chỉ có mép đường. Chưa có xác nhận trực tiếp từ coach về miễn trừ.

Coach hướng dẫn: có vạch nhìn thấy thì gán, không thấy thì miễn. Sau khi đối chiếu lại ảnh gốc, mình chốt cả 6 vị trí theo hướng không gán thêm L1/R1. Mục 3 ghi lý do từng vị trí. Riêng A08, xem ảnh đối chiếu đã khoanh vùng ở cuối mục 6. Đây là kết quả tự kiểm theo tiêu chí của coach. Chưa có xác nhận riêng của coach cho từng vị trí. Lint vẫn đếm 6 cảnh báo vì không tự đánh giá được ảnh. Hai job front #23 và fisheye #24 ở trạng thái Completed trước khi xuất revision 1.

**Đợt bổ sung, revision 2.** Gán thủ công A13–A16 và B09–B12 trên CVAT, rồi gộp vào hai ZIP tương ứng. Ở A14, vạch vàng đôi được lưu đúng vị trí `L1`. Ở A16, bổ sung `L1`, `R1`, `L2` và bật `occluded` cho đoạn `R1` bị taxi che. Đã đối chiếu để giữ nguyên nhãn và thẻ của 20 ảnh bắt buộc từ revision 1. Bản gộp có 28 ảnh, 6 cảnh báo QC1-02 đã nêu ở trên và 0 cảnh báo mới.

**Tự kiểm theo Road v1.0, revision 3.** Gán bổ sung thủ công và xuất lại nhãn trên CVAT.

- A10 và A12 bổ sung 3 biển, gồm biển chỉ dẫn nhỏ ở A10, biển tròn và biển phụ ở A12.
- B02 bổ sung mặt sau biển trên đảo giao thông và sửa hộp đèn đang sáng xanh thành `type=pedestrian`.
- B10 và B12 căn lại biên polygon `crosswalk` để bao các đầu vạch sơn.

Đã đối chiếu lô 28 ảnh với revision 2. Lint vẫn ghi 6 cảnh báo QC1-02 ở các vị trí đã giải thích tại mục 3. Không có cảnh báo mới.

## 5. Kiểm file export
| File | Mở lại được? | Số shape ảnh 1 (job / file) | Số shape ảnh 2 (job / file) | Tag camera có trong XML? |
| --- | --- | --- | --- | --- |
| [hoangtrongtra-front.zip](hoangtrongtra-front.zip) | Có | A01: 4 / 4, A13: 5 / 5 | A02: 3 / 3, A14: 9 / 9 | Có, `front` trên cả 16 ảnh |
| [hoangtrongtra-fisheye.zip](hoangtrongtra-fisheye.zip) | Có | B01: 1 / 1, B09: 2 / 2 | B02: 7 / 7, B10: 1 / 1 | Có, khớp hậu tố trên cả 12 ảnh |

Hai ZIP dùng **CVAT for images 1.1**, mỗi file chỉ chứa `annotations.xml`. Manifest revision 3 ghi số ảnh và SHA-256 của từng ZIP sau khi gộp.

## 6. Ảnh chụp màn hình

Nếu nhận riêng file Markdown, mở [mục ảnh minh chứng trên GitHub](https://github.com/trahoangdev/K5-L23-Day11-HoangTrongTra-2A202603342-Road-Elements-SVM/blob/main/out/day11-submission/hoangtrongtra-report.md#6-ảnh-chụp-màn-hình) để xem ảnh.

1. Tab Labels của project.

   ![Labels của project #39][minh-chung-labels]

2. Một ảnh camera trước đã gán đủ (làn, vùng lái, đèn/biển).

   ![CVAT A12 sau khi bổ sung biển chỉ dẫn và biển phụ][minh-chung-a12]

3. Đường mép lề trên ảnh fisheye B05, vẽ lại từ tọa độ polyline đã xuất trong CVAT.

   ![B05, vị trí và hình phóng to của đường mép lề đã gán][minh-chung-b05]

4. Một đoạn XML có `<polyline label="lane">`.

   ```xml
   <polyline label="lane" source="manual" occluded="0" points="106.95,719.00;154.30,679.28;180.27,659.43;264.80,585.80;279.30,572.40;310.20,549.50;331.48,531.12;354.40,512.79;368.14,505.15" z_order="0">
     <attribute name="position">L1</attribute>
     <attribute name="style">dashed</attribute>
     <attribute name="color">white</attribute>
     <attribute name="kind">single</attribute>
   </polyline>
   ```

Ảnh đối chiếu A08 dùng trong mục 4. Hai vòng vàng đánh dấu nét mờ cần kiểm.

![A08, đoạn đối chiếu giữa hai mốc (253, 423) và (482, 325)][minh-chung-a08]

CVAT xác nhận xuất nhãn hoàn tất cho hai task bổ sung.

![Hai lượt export nhãn bổ sung đã hoàn tất trên CVAT][minh-chung-export-extra]

B02, B10 và B12 ở revision 3. Hình dưới được vẽ từ tọa độ nhãn trong hai bản xuất CVAT.

![Các hộp ở B02 và biên crosswalk trước và sau khi chỉnh ở B10, B12][minh-chung-fisheye-r3]

Dữ liệu BDD100K © 2018 The Regents of the University of California, theo BDD100K License.

## 7. Tự đánh giá
Lỗi bạn mắc nhiều nhất hôm nay (theo mã QC1-xx), và cách tránh ở Ngày 20: Lỗi mình thấy lặp lại khi tự rà là QC1-04 ở front và QC1-11 ở fisheye. Vạch có đoạn lệch tim sơn hoặc thiếu điểm ở chỗ cong. Ngày 20 mình sẽ phóng to để đặt điểm đầu trên tim sơn, thêm điểm ở đoạn cong và bật/tắt lớp nhãn để so với ảnh gốc trước khi lưu.\
Nhãn của bạn đi vào model ở đâu? Chọn một lỗi đã sửa và nói nó làm model học sai thế nào: Polyline là nhãn đích khi huấn luyện model phát hiện làn. Chẳng hạn, nếu R1 ở A02 đặt ở mép sơn, tọa độ đích tại các hàng ảnh qua đoạn đó cũng bị lệch. Model có thể học dự đoán lệch về một phía của vạch.

## 8. (Tùy chọn, buffer) Từ polyline đến đích row-anchor

Đối chiếu vạch L1 ở cùng ảnh A01 của Hoàng Trọng Trà và Nguyễn Quốc Hưng. Tọa độ x tính bằng pixel.

| y | 720 | 680 | 640 | 600 | 560 |
| --- | ---: | ---: | ---: | ---: | ---: |
| x của chúng tôi | không có làn | 153,4 | 202,6 | 248,5 | 296,0 |
| x của bạn kia | 111,7 | 157,1 | 203,5 | 250,9 | 297,2 |

Trả lời 3 câu:

1. Năm số x đó chính là đích mà một model row-anchor học cho vạch này. Nếu bạn dừng polyline sớm 40 px, hàng nào đổi thành "không có làn"?
   Với L1 ở A01, nếu cắt đầu gần xe 40 px theo trục y thì điểm bắt đầu chuyển từ y=719 lên y=679. Hàng 680 đổi thành “không có làn”. Hàng 720 đã nằm ngoài polyline ngay từ đầu.
2. So với bạn được kiểm (cùng ảnh): ở hàng 720 và hàng 560, hai bạn lệch nhau bao nhiêu pixel? Lệch ở hàng nào ảnh hưởng LKA nhiều hơn (slide 25)?
   Ở y=720, mình không có giao điểm vì polyline dừng ở y=719, còn Hưng có x=111,7 px. Vì vậy chưa tính được độ lệch ngang ở hàng 720. Ở y=560, hai bài lệch khoảng 1,2 px (x của mình là 296,0, x của Hưng là 297,2). Sai lệch ở hàng 720 thường ảnh hưởng LKA trực tiếp hơn vì hàng này gần xe hơn.
3. Nếu polyline vẽ từ xa về gần (ngược quy tắc 2), cách tính trên có đổi không? Script nào sẽ gặp khó?
   Giao điểm tại mỗi hàng giữ nguyên khi đảo thứ tự điểm. `road_check.py` sẽ báo QC1-04 ở ảnh front vì polyline sai chiều gần → xa.

[minh-chung-labels]: ../../docs/images/submission-evidence/cvat-labels.jpg
[minh-chung-a12]: ../../docs/images/submission-evidence/front-a12.jpg
[minh-chung-b05]: ../../docs/images/submission-evidence/fisheye-b05-road-curb.png
[minh-chung-a08]: ../../docs/images/submission-evidence/front-a08-doi-chieu.jpg
[minh-chung-export-extra]: ../../docs/images/submission-evidence/cvat-export-extra.jpg
[minh-chung-fisheye-r3]: ../../docs/images/submission-evidence/fisheye-revision-3.png
