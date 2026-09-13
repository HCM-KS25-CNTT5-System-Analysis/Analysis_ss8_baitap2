# Bước 1: Soi lỗi thiết kế
Thuộc tính bị trùng lặp

Các thuộc tính xuất hiện ở cả BacSi và YTa:

maNhanVien
hoTen
soDienThoai
Hậu quả

Khi cần thay đổi cấu trúc thuộc tính hoTen, phải sửa ở nhiều lớp, làm tăng công sức bảo trì và dễ gây không đồng nhất dữ liệu.

Bước 2: Tái cấu trúc bằng Inheritance
Lớp cha (Superclass)	Lớp con (Subclass)	Thuộc tính dùng chung	Thuộc tính riêng biệt
NhanVienYTe	BacSi	maNhanVien, hoTen, soDienThoai	chuyenKhoa
NhanVienYTe	YTa	maNhanVien, hoTen, soDienThoai	khuVucTruc

Phương thức riêng vẫn giữ:

BacSi → + kham(benhNhan): void
YTa → + tiemThuoc(benhNhan): void

Lớp cha NhanVienYTe chứa các thuộc tính chung:

- maNhanVien: String
- hoTen: String
- soDienThoai: String
Bước 3: Aggregation
Loại quan hệ: Aggregation (Tổng hợp)
Ký hiệu: hình thoi rỗng ◇
KhoaKham → NhanVienYTe
Multiplicity: 1 → 1..*

Ý nghĩa: Một KhoaKham có một hoặc nhiều nhân viên y tế; nhân viên vẫn tồn tại độc lập nếu khoa bị giải thể.

Bước 4: Class Diagram

<img width="943" height="997" alt="mermaid-diagram (1)" src="https://github.com/user-attachments/assets/bfa97341-2e03-43f0-bc8d-5364731ed653" />


Quan hệ trong sơ đồ
                 NhanVienYTe
                /           \
               /             \
          BacSi               YTa
           
           
KhoaKham ◇────────────── 1..* NhanVienYTe

Trong Mermaid:

<|-- = Inheritance
o-- = Aggregation
"1..*" = một đến nhiều
- = private
+ = public

Đây là cấu trúc đúng với yêu cầu bài: NhanVienYTe gom dữ liệu chung, BacSi và YTa kế thừa, còn KhoaKham aggregation với NhanVienYTe.
