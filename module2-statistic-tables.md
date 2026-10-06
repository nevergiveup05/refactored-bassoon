# CÁC BẢNG THỐNG KÊ MA TRẬN PHƯƠNG THỨC VÀ ĐỐI TƯỢNG (MODULE 2)

Tài liệu này tổng hợp đầy đủ **Bảng 1 (Trích xuất Message và ứng viên Operation)** và **Bảng 2 (Tổng hợp Đối tượng, Thuộc tính và Phương thức)** cho toàn bộ 5 Use Case thuộc Module 2. Tất cả thiết kế tuân thủ mô hình 3 lớp **Boundary - Control - Entity (ECB)**, đồng bộ 100% với Sơ đồ CSDL Domain Model (`domain_hethong.vpd.png`) và tài liệu đặc tả `Sequence_Module2.docx`.

---

## 1. USE CASE 2.1: XEM BÁO CÁO THỐNG KÊ NHẬP / XUẤT

### Bảng 1: Trích xuất Message và ứng viên Operation (UC 2.1)

| Message | Đối tượng nhận | Ứng viên Operation |
| :--- | :--- | :--- |
| `1: ChonChucNangBaoCaoThongKe()` | `GiaoDienBaoCaoThongKe` | `chonChucNangBaoCaoThongKe()` |
| `2: YeuCauKhoiTaoManHinh()` | `QuanLyBaoCaoControl` | `yeuCauKhoiTaoManHinh()` |
| `3: LayDanhSachKho()` | `Kho` | `layDanhSachKho()` |
| `4: DSKho(maKho, tenKho)` | `QuanLyBaoCaoControl` | *(Return message)* |
| `5: HienThiFormBoLocAndDashboard(DSKho)` | `GiaoDienBaoCaoThongKe` | `hienThiFormBoLocAndDashboard(dsKho: List)` |
| `6: NhapThongTinLoc(tuNgay, denNgay, loaiGD, maKho)` | `GiaoDienBaoCaoThongKe` | `nhapThongTinLoc(tuNgay, denNgay, loaiGD, maKho)` |
| `7: NhanNutXemBaoCao()` | `GiaoDienBaoCaoThongKe` | `nhanNutXemBaoCao()` |
| `8: TraCuuBaoCao(tuNgay, denNgay, loaiGD, maKho)` | `QuanLyBaoCaoControl` | `traCuuBaoCao(tuNgay: Date, denNgay: Date, loaiGD: String, maKho: String)` |
| `9: KiemTraThoiGianValid(tuNgay, denNgay)` | `QuanLyBaoCaoControl` | `kiemTraThoiGianValid(tuNgay: Date, denNgay: Date)` |
| `9.1: HienThiThongBaoLoi('Mốc thời gian không hợp lệ')` | `GiaoDienBaoCaoThongKe` | `hienThiThongBaoLoi(msg: String)` |
| `10: LayDanhSachPhieuXuat(tuNgay, denNgay, maKho)` | `PhieuXuatKho` | `layDanhSachPhieuXuat(tuNgay: Date, denNgay: Date, maKho: String)` |
| `11: DSPhieuXuat(maPXK, ngayXuat, tongSoLuong)` | `QuanLyBaoCaoControl` | *(Return message)* |
| `12: LayDanhSachPhieuNhap(tuNgay, denNgay, maKho)` | `PhieuNhapKho` | `layDanhSachPhieuNhap(tuNgay: Date, denNgay: Date, maKho: String)` |
| `13: DSPhieuNhap(maPNK, ngayNhap, slThucNhap)` | `QuanLyBaoCaoControl` | *(Return message)* |
| `14: LayThongTinMatHang(maNL)` | `NguyenLieu` | `layThongTinMatHang(maNL: String)` |
| `15: ThongTinMatHang(tenNL, donViTinh)` | `QuanLyBaoCaoControl` | *(Return message)* |
| `16: GomNhomVaTinhToanKPIs()` | `QuanLyBaoCaoControl` | `gomNhomVaTinhToanKPIs()` |
| `17: TraVeKetQuaThongKe(KPIs, BieuDo, BangGomNhom)` | `GiaoDienBaoCaoThongKe` | `traVeKetQuaThongKe(kpis: Map, bieuDo: Object, bangData: List)` |
| `18: NhanNutXuatExcel()` | `GiaoDienBaoCaoThongKe` | `nhanNutXuatExcel()` |
| `19: YeuCauXuatBaoCaoExcel(KetQuaBaoCao)` | `QuanLyBaoCaoControl` | `yeuCauXuatBaoCaoExcel(data: List)` |
| `20: TraVeLuongFileExcel(.xlsx)` | `GiaoDienBaoCaoThongKe` | `traVeLuongFileExcel(fileStream: Byte[])` |

### Bảng 2: Tổng hợp Đối tượng, Thuộc tính và Phương thức (UC 2.1)

| Đối tượng | Thuộc tính | Phương thức (Operations) |
| :--- | :--- | :--- |
| **`GiaoDienBaoCaoThongKe`** *(Boundary)* | `tuNgay`, `denNgay`, `loaiGiaoDich`, `maKhoSelected`, `danhSachKhoDropdown`, `kpiData`, `chartData`, `tableData` | `chonChucNangBaoCaoThongKe()`, `hienThiFormBoLocAndDashboard(dsKho)`, `nhapThongTinLoc(tuNgay, denNgay, loaiGD, maKho)`, `nhanNutXemBaoCao()`, `hienThiThongBaoLoi(msg)`, `traVeKetQuaThongKe(kpis, bieuDo, bangData)`, `nhanNutXuatExcel()`, `traVeLuongFileExcel(fileStream)` |
| **`QuanLyBaoCaoControl`** *(Control)* | `tuNgayHopLe`, `denNgayHopLe`, `tongNhapInPeriod`, `tongXuatInPeriod`, `danhSachKetQua` | `yeuCauKhoiTaoManHinh()`, `traCuuBaoCao(tuNgay, denNgay, loaiGD, maKho)`, `kiemTraThoiGianValid(tuNgay, denNgay)`, `gomNhomVaTinhToanKPIs()`, `yeuCauXuatBaoCaoExcel(data)` |
| **`PhieuXuatKho`** *(Entity)* | `maPXK`, `ngayXuat`, `tongSoLuong`, `nguoiLap`, `maKho`, `trangThai` | `layDanhSachPhieuXuat(tuNgay, denNgay, maKho)` |
| **`PhieuNhapKho`** *(Entity)* | `maPNK`, `ngayNhap`, `slThucNhap`, `nguoiLap`, `maKho`, `trangThai` | `layDanhSachPhieuNhap(tuNgay, denNgay, maKho)` |
| **`NguyenLieu`** *(Entity)* | `maNL`, `tenNL`, `donViTinh`, `loaiKhoBaoQuan` | `layThongTinMatHang(maNL)` |
| **`Kho`** *(Entity)* | `maKho`, `tenKho`, `loaiKho` | `layDanhSachKho()` |

---

## 2. USE CASE 2.2: XEM BÁO CÁO TỒN KHO CHI TIẾT & CẢNH BÁO HSD

### Bảng 1: Trích xuất Message và ứng viên Operation (UC 2.2)

| Message | Đối tượng nhận | Ứng viên Operation |
| :--- | :--- | :--- |
| `1: ChonChucNangBaoCaoTonKho()` | `GiaoDienBaoCaoTonKho` | `chonChucNangBaoCaoTonKho()` |
| `2: YeuCauKhoiTaoManHinh()` | `QuanLyTonKhoControl` | `yeuCauKhoiTaoManHinh()` |
| `3: LayDanhSachKhoActive()` | `Kho` | `layDanhSachKhoActive()` |
| `4: DSKho(maKho, tenKho)` | `QuanLyTonKhoControl` | *(Return message)* |
| `5: HienThiBoLoc(Kho, TrangThaiHSD, TuKhoa)` | `GiaoDienBaoCaoTonKho` | `hienThiBoLoc(dsKho: List)` |
| `6: NhapThongTinLoc(maKho, trangThaiHSD, tuKhoa)` | `GiaoDienBaoCaoTonKho` | `nhapThongTinLoc(maKho, trangThaiHSD, tuKhoa)` |
| `7: NhanNutApDungLoc()` | `GiaoDienBaoCaoTonKho` | `nhanNutApDungLoc()` |
| `8: TraCuuTonKhoChiTiet(maKho, trangThaiHSD, tuKhoa)` | `QuanLyTonKhoControl` | `traCuuTonKhoChiTiet(maKho: String, trangThaiHSD: String, tuKhoa: String)` |
| `9: LayDanhSachLoHang(tuKhoa, trangThaiHSD)` | `LoNguyenLieu` | `layDanhSachLoHang(tuKhoa: String, trangThaiHSD: String)` |
| `10: TraVeDSLoHang(maLo, maNL, ngaySanXuat, hanSuDung, soLuongTon)` | `QuanLyTonKhoControl` | *(Return message)* |
| `11: LaySoLuongTonTaiViTri(maLo)` | `TonKho` | `laySoLuongTonTaiViTri(maLo: String)` |
| `12: TraVeThongTinTon(slTon, maViTri)` | `QuanLyTonKhoControl` | *(Return message)* |
| `13: LayToaDoLuuTru(maViTri)` | `ViTriKho` | `layToaDoLuuTru(maViTri: String)` |
| `14: TraVeToaDo(day, ke, tang, oslot, maKho)` | `QuanLyTonKhoControl` | *(Return message)* |
| `15: LayThongTinNguyenLieu(maNL)` | `NguyenLieu` | `layThongTinNguyenLieu(maNL: String)` |
| `16: TraVeNguyenLieu(tenNL, donViTinh)` | `QuanLyTonKhoControl` | *(Return message)* |
| `17: TinhSoNgayConLaiVaGanCoMau(hanSuDung - NgayHienTai)` | `QuanLyTonKhoControl` | `tinhSoNgayConLaiVaGanCoMau(hanSuDung: Date)` |
| `18: TraVeKetQuaTonKho(DSTonKho, CoMauCanhBao)` | `GiaoDienBaoCaoTonKho` | `traVeKetQuaTonKho(dsTonKho: List, coMauData: List)` |
| `19: NhanNutXuatExcel()` | `GiaoDienBaoCaoTonKho` | `nhanNutXuatExcel()` |
| `20: YeuCauXuatBaoCaoExcel(DSTonKho)` | `QuanLyTonKhoControl` | `yeuCauXuatBaoCaoExcel(dsTonKho: List)` |
| `21: TraVeLuongFileExcel(.xlsx)` | `GiaoDienBaoCaoTonKho` | `traVeLuongFileExcel(fileStream: Byte[])` |

### Bảng 2: Tổng hợp Đối tượng, Thuộc tính và Phương thức (UC 2.2)

| Đối tượng | Thuộc tính | Phương thức (Operations) |
| :--- | :--- | :--- |
| **`GiaoDienBaoCaoTonKho`** *(Boundary)* | `maKhoSelected`, `trangThaiHSDSelected`, `tuKhoaTimKiem`, `danhSachKetQua`, `coMauHighlightMap` | `chonChucNangBaoCaoTonKho()`, `hienThiBoLoc(dsKho)`, `nhapThongTinLoc(maKho, trangThaiHSD, tuKhoa)`, `nhanNutApDungLoc()`, `traVeKetQuaTonKho(dsTonKho, coMauData)`, `nhanNutXuatExcel()`, `traVeLuongFileExcel(fileStream)` |
| **`QuanLyTonKhoControl`** *(Control)* | `todayDate`, `soNgayConLai`, `coMauDanhGia` | `yeuCauKhoiTaoManHinh()`, `traCuuTonKhoChiTiet(maKho, trangThaiHSD, tuKhoa)`, `tinhSoNgayConLaiVaGanCoMau(hanSuDung)`, `yeuCauXuatBaoCaoExcel(dsTonKho)` |
| **`LoNguyenLieu`** *(Entity)* | `maLo`, `maNL`, `ngaySanXuat`, `hanSuDung`, `soLuongTon`, `soLuongReserved`, `trangThai` | `layDanhSachLoHang(tuKhoa, trangThaiHSD)` |
| **`TonKho`** *(Entity)* | `maTonKho`, `maLo`, `maViTri`, `slTon`, `ngayCapNhat` | `laySoLuongTonTaiViTri(maLo)` |
| **`ViTriKho`** *(Entity)* | `maViTri`, `maKho`, `day`, `ke`, `tang`, `oslot`, `trangThai` | `layToaDoLuuTru(maViTri)` |
| **`NguyenLieu`** *(Entity)* | `maNL`, `tenNL`, `donViTinh`, `loaiKhoBaoQuan` | `layThongTinNguyenLieu(maNL)` |
| **`Kho`** *(Entity)* | `maKho`, `tenKho`, `loaiKho` | `layDanhSachKhoActive()` |

---

## 3. USE CASE 2.3: LẬP PHIẾU XUẤT KHO NGUYÊN LIỆU (THỰC XUẤT TẠI KỆ)

### Bảng 1: Trích xuất Message và ứng viên Operation (UC 2.3)

| Message | Đối tượng nhận | Ứng viên Operation |
| :--- | :--- | :--- |
| `1: ChonChucNangLenhDieuPhoiXuatKho()` | `GiaoDienPhieuXuatKho` | `chonChucNangLenhDieuPhoiXuatKho()` |
| `2: TruyXuatDanhSachLenhChoXuat()` | `QuanLyXuatKhoControl` | `truyXuatDanhSachLenhChoXuat()` |
| `3: LayDanhSachLenhChoXuat(trangThai='Chờ xuất')` | `LenhDieuPhoi` | `layDanhSachLenhChoXuat(trangThai: String)` |
| `4: DSLenhDieuPhoi(maLenh, maLo, maViTri, soLuongPhanBo)` | `QuanLyXuatKhoControl` | *(Return message)* |
| `5: HienThiDanhSachLenhChoXuat(DSLenhDieuPhoi)` | `GiaoDienPhieuXuatKho` | `hienThiDanhSachLenhChoXuat(dsLenh: List)` |
| `6: ChonLenhDieuPhoi(maLenh)` | `GiaoDienPhieuXuatKho` | `chonLenhDieuPhoi(maLenh: String)` |
| `7: KhoiTaoFormPhieuXuat(maLenh)` | `QuanLyXuatKhoControl` | `khoiTaoFormPhieuXuat(maLenh: String)` |
| `8: DienSanThongTinVaKhoaTruong(maLo, maViTri, soLuongPhanBo)` | `GiaoDienPhieuXuatKho` | `dienSanThongTinVaKhoaTruong(maLo, maViTri, slPhanBo)` |
| `8.1a: ChonDieuChinhSoThucXuat()` | `GiaoDienPhieuXuatKho` | `chonDieuChinhSoThucXuat()` |
| `8.2a: NhapSoThucXuatVaLyDo(slThucXuat, lyDoChenhLech)` | `GiaoDienPhieuXuatKho` | `nhapSoThucXuatVaLyDo(slThucXuat: Decimal, lyDo: String)` |
| `8.3a: KiemTraInput(0 < slThucXuat <= soLuongPhanBo)` | `GiaoDienPhieuXuatKho` | `kiemTraInput(slThucXuat: Decimal, slPhanBo: Decimal)` |
| `9: KiemDemTaiKeVaBamXacNhanXuatKho()` | `GiaoDienPhieuXuatKho` | `kiemDemTaiKeVaBamXacNhanXuatKho()` |
| `10: ThucHienXuatKho(payloadXuatKho)` | `QuanLyXuatKhoControl` | `thucHienXuatKho(payload: Map)` |
| `11: LuuPhieuXuatKhoMoi(maPXK, maLenh, maKho, ngayXuat, nguoiLap, tongSoLuong)` | `PhieuXuatKho` | `luuPhieuXuatKhoMoi(maPXK, maLenh, maKho, ngayXuat, nguoiLap, tongSoLuong)` |
| `12: PhieuXuatSaved` | `QuanLyXuatKhoControl` | *(Return message)* |
| `13: LuuChiTietPhieuXuat(maChiTiet, maPXK, maLo, slThucXuat, soLuongPhanBo, lyDoChenhLech)` | `ChiTietPhieuXuat` | `luuChiTietPhieuXuat(maChiTiet, maPXK, maLo, slThucXuat, slPhanBo, lyDo)` |
| `14: ChiTietSaved` | `QuanLyXuatKhoControl` | *(Return message)* |
| `15: TruTonKhoThucTe(maLo, slThucXuat, soLuongPhanBo)` | `LoNguyenLieu` | `truTonKhoThucTe(maLo: String, slThucXuat: Decimal, slPhanBo: Decimal)` |
| `16: TonKhoUpdated` | `QuanLyXuatKhoControl` | *(Return message)* |
| `17: TruSoLuongLuuTaiViTri(maTonKho, slThucXuat)` | `TonKho` | `truSoLuongLuuTaiViTri(maTonKho: String, slThucXuat: Decimal)` |
| `18: BinStockUpdated` | `QuanLyXuatKhoControl` | *(Return message)* |
| `19: CapNhatTrangThaiViTri(maViTri, trangThai='CON_TRONG')` | `ViTriKho` | `capNhatTrangThaiViTri(maViTri: String, trangThai: String)` |
| `20: LocationReleased` | `QuanLyXuatKhoControl` | *(Return message)* |
| `21: CapNhatTrangThaiLenh(maLenh, trangThai='Đã xuất')` | `LenhDieuPhoi` | `capNhatTrangThaiLenh(maLenh: String, trangThai: String)` |
| `22: LenhUpdated` | `QuanLyXuatKhoControl` | *(Return message)* |
| `23: CapNhatTrangThaiPhieuGoc(maPhieuYeuCau, trangThai)` | `PhieuYeuCauXuat` | `capNhatTrangThaiPhieuGoc(maPhieuYC: String, trangThai: String)` |
| `24: PhieuGocUpdated` | `QuanLyXuatKhoControl` | *(Return message)* |
| `25: HienThiThongBaoThanhCong('Xuất kho nguyên liệu thành công')` | `GiaoDienPhieuXuatKho` | `hienThiThongBaoThanhCong(msg: String)` |

### Bảng 2: Tổng hợp Đối tượng, Thuộc tính và Phương thức (UC 2.3)

| Đối tượng | Thuộc tính | Phương thức (Operations) |
| :--- | :--- | :--- |
| **`GiaoDienPhieuXuatKho`** *(Boundary)* | `maLenhSelected`, `slThucXuatInput`, `lyDoChenhLechInput`, `isEnableEdit` | `chonChucNangLenhDieuPhoiXuatKho()`, `hienThiDanhSachLenhChoXuat(dsLenh)`, `chonLenhDieuPhoi(maLenh)`, `dienSanThongTinVaKhoaTruong(maLo, maViTri, slPhanBo)`, `chonDieuChinhSoThucXuat()`, `nhapSoThucXuatVaLyDo(slThucXuat, lyDo)`, `kiemTraInput(slThucXuat, slPhanBo)`, `kiemDemTaiKeVaBamXacNhanXuatKho()`, `hienThiThongBaoThanhCong(msg)` |
| **`QuanLyXuatKhoControl`** *(Control)* | `payloadData`, `statusPhieuGocNext` | `truyXuatDanhSachLenhChoXuat()`, `khoiTaoFormPhieuXuat(maLenh)`, `thucHienXuatKho(payload)` |
| **`LenhDieuPhoi`** *(Entity)* | `maLenh`, `maPhieuYeuCau`, `maKho`, `ngayDieuPhoi`, `nguoiDieuPhoi`, `trangThai` | `layDanhSachLenhChoXuat(trangThai)`, `capNhatTrangThaiLenh(maLenh, trangThai)` |
| **`PhieuXuatKho`** *(Entity)* | `maPXK`, `maLenh`, `maKho`, `ngayXuat`, `nguoiLap`, `xuongNhan`, `tongSoLuong`, `trangThai` | `luuPhieuXuatKhoMoi(maPXK, maLenh, maKho, ngayXuat, nguoiLap, tongSoLuong)` |
| **`ChiTietPhieuXuat`** *(Entity)* | `maChiTiet`, `maPXK`, `maLo`, `soLuongDuKien`, `soLuongThucXuat`, `soLuongPhanBo`, `lyDoChenhLech` | `luuChiTietPhieuXuat(maChiTiet, maPXK, maLo, slThucXuat, slPhanBo, lyDo)` |
| **`LoNguyenLieu`** *(Entity)* | `maLo`, `maNL`, `ngaySanXuat`, `hanSuDung`, `soLuongTon`, `soLuongReserved`, `trangThai` | `truTonKhoThucTe(maLo, slThucXuat, slPhanBo)` |
| **`TonKho`** *(Entity)* | `maTonKho`, `maLo`, `maViTri`, `slTon`, `ngayCapNhat` | `truSoLuongLuuTaiViTri(maTonKho, slThucXuat)` |
| **`ViTriKho`** *(Entity)* | `maViTri`, `maKho`, `day`, `ke`, `tang`, `oslot`, `trangThai` | `capNhatTrangThaiViTri(maViTri, trangThai)` |
| **`PhieuYeuCauXuat`** *(Entity)* | `maPhieuYeuCau`, `maKeHoach`, `xuongYeuCau`, `ngayYeuCau`, `lyDoXuat`, `trangThai` | `capNhatTrangThaiPhieuGoc(maPhieuYC, trangThai)` |

---

## 4. USE CASE 2.4: ĐIỀU PHỐI XUẤT NGUYÊN LIỆU THEO FEFO

### Bảng 1: Trích xuất Message và ứng viên Operation (UC 2.4)

| Message | Đối tượng nhận | Ứng viên Operation |
| :--- | :--- | :--- |
| `1: ChonChucNangDieuPhoiFEFO()` | `GiaoDienDieuPhoiFEFO` | `chonChucNangDieuPhoiFEFO()` |
| `2: TruyXuatDanhSachPhieuChoXuLy()` | `QuanLyDieuPhoiControl` | `truyXuatDanhSachPhieuChoXuLy()` |
| `3: LayDanhSachPhieuChoXuLy(trangThai='Chờ xử lý')` | `PhieuYeuCauXuat` | `layDanhSachPhieuChoXuLy(trangThai: String)` |
| `4: DSPhieuYeuCau(maPhieuYeuCau, xuongYeuCau)` | `QuanLyDieuPhoiControl` | *(Return message)* |
| `5: HienThiDanhSachPhieuChoXuLy(DSPhieuYeuCau)` | `GiaoDienDieuPhoiFEFO` | `hienThiDanhSachPhieuChoXuLy(dsPhieu: List)` |
| `6: ChonPhieuYeuCau(maPhieuYeuCau)` | `GiaoDienDieuPhoiFEFO` | `chonPhieuYeuCau(maPhieuYC: String)` |
| `7: KichHoatThuatToanFEFO(maPhieuYeuCau)` | `QuanLyDieuPhoiControl` | `kichHoatThuatToanFEFO(maPhieuYC: String)` |
| `8: LayChiTietYeuCau(maPhieuYeuCau)` | `ChiTietYeuCauXuat` | `layChiTietYeuCau(maPhieuYC: String)` |
| `9: DSChiTiet(maNL, soLuongYeuCau, donViTinh)` | `QuanLyDieuPhoiControl` | *(Return message)* |
| `10: QuetLoAvailableTheoFEFO(maNL)` | `LoNguyenLieu` | `quetLoAvailableTheoFEFO(maNL: String)` |
| `11: DSLoGoiY(maLo, hanSuDung, soLuongTon, soLuongReserved)` | `QuanLyDieuPhoiControl` | *(Return message)* |
| `12: LayToaDoViTriKho(maLo)` | `ViTriKho` | `layToaDoViTriKho(maLo: String)` |
| `13: TraVeToaDo(maViTri, day, ke, tang, oslot, maKho)` | `QuanLyDieuPhoiControl` | *(Return message)* |
| `14: TinhToanSoLuongPhanBoFEFO(soLuongYeuCau)` | `QuanLyDieuPhoiControl` | `tinhToanSoLuongPhanBoFEFO(slYeuCau: Decimal)` |
| `15: HienThiKetQuaDeXuatFEFO(DSPhanBoGoiY)` | `GiaoDienDieuPhoiFEFO` | `hienThiKetQuaDeXuatFEFO(dsGoiY: List)` |
| `16a: KiemTraVaBamXacNhanDieuPhoi()` | `GiaoDienDieuPhoiFEFO` | `kiemTraVaBamXacNhanDieuPhoi()` |
| `17a: XacNhanDieuPhoiHopLe(maPhieuYeuCau, DSPhanBo)` | `QuanLyDieuPhoiControl` | `xacNhanDieuPhoiHopLe(maPhieuYC: String, dsPhanBo: List)` |
| `16b.1: ChonLoHSDXaHon(maLoChon)` | `GiaoDienDieuPhoiFEFO` | `chonLoHSDXaHon(maLoChon: String)` |
| `16b.2: HienThiPopupCanhBaoViPhamFEFO()` | `GiaoDienDieuPhoiFEFO` | `hienThiPopupCanhBaoViPhamFEFO()` |
| `16b.3: NhapLyDoBoQuaFEFO(lyDoBoQuaFEFO)` | `GiaoDienDieuPhoiFEFO` | `nhapLyDoBoQuaFEFO(lyDo: String)` |
| `17b: XacNhanDieuPhoiViPhamFEFO(maPhieuYeuCau, DSPhanBo, lyDo)` | `QuanLyDieuPhoiControl` | `xacNhanDieuPhoiViPhamFEFO(maPhieuYC: String, dsPhanBo: List, lyDo: String)` |
| `18b: GhiVetNhatKyViPham(logID, maPhieuYeuCau, maLoGoiY, maLoChon, lyDo, nguoiThucHien, thoiGian)` | `FEFOAuditLog` | `ghiVetNhatKyViPham(logID, maPhieuYC, maLoGoiY, maLoChon, lyDo, nguoiTH, thoiGian)` |
| `19b: LogSaved` | `QuanLyDieuPhoiControl` | *(Return message)* |
| `20: CapNhatSoLuongReserved(maLo, +soLuongPhanBo)` | `LoNguyenLieu` | `capNhatSoLuongReserved(maLo: String, slAdded: Decimal)` |
| `21: ReservedUpdated` | `QuanLyDieuPhoiControl` | *(Return message)* |
| `22: CapNhatTrangThaiPhieu('Đang điều phối')` | `PhieuYeuCauXuat` | `capNhatTrangThaiPhieu(maPhieuYC: String, trangThai: String)` |
| `23: PhieuStatusUpdated` | `QuanLyDieuPhoiControl` | *(Return message)* |
| `24: TaoLenhDieuPhoiMoi(maLenh, maPhieuYeuCau, maKho, ngayDieuPhoi, nguoiDieuPhoi, trangThai='Chờ xuất')` | `LenhDieuPhoi` | `taoLenhDieuPhoiMoi(maLenh, maPhieuYC, maKho, ngayDP, nguoiDP, trangThai)` |
| `25: LenhCreated` | `QuanLyDieuPhoiControl` | *(Return message)* |
| `26: TaoChiTietLenhDieuPhoi(maChiTiet, maLenh, maLo, maViTri, soLuongPhanBo)` | `ChiTietLenhDieuPhoi` | `taoChiTietLenhDieuPhoi(maChiTiet, maLenh, maLo, maViTri, slPhanBo)` |
| `27: ChiTietLenhCreated` | `QuanLyDieuPhoiControl` | *(Return message)* |
| `28: HienThiThongBaoThanhCong('Điều phối xuất kho FEFO thành công')` | `GiaoDienDieuPhoiFEFO` | `hienThiThongBaoThanhCong(msg: String)` |

### Bảng 2: Tổng hợp Đối tượng, Thuộc tính và Phương thức (UC 2.4)

| Đối tượng | Thuộc tính | Phương thức (Operations) |
| :--- | :--- | :--- |
| **`GiaoDienDieuPhoiFEFO`** *(Boundary)* | `maPhieuSelected`, `dsGoiYFEFO`, `maLoChonOverride`, `lyDoBoQuaInput` | `chonChucNangDieuPhoiFEFO()`, `hienThiDanhSachPhieuChoXuLy(dsPhieu)`, `chonPhieuYeuCau(maPhieuYC)`, `hienThiKetQuaDeXuatFEFO(dsGoiY)`, `kiemTraVaBamXacNhanDieuPhoi()`, `chonLoHSDXaHon(maLoChon)`, `hienThiPopupCanhBaoViPhamFEFO()`, `nhapLyDoBoQuaFEFO(lyDo)`, `hienThiThongBaoThanhCong(msg)` |
| **`QuanLyDieuPhoiControl`** *(Control)* | `slYeuCauTotal`, `slAccumulated`, `isViPhamFEFO` | `truyXuatDanhSachPhieuChoXuLy()`, `kichHoatThuatToanFEFO(maPhieuYC)`, `tinhToanSoLuongPhanBoFEFO(slYeuCau)`, `xacNhanDieuPhoiHopLe(maPhieuYC, dsPhanBo)`, `xacNhanDieuPhoiViPhamFEFO(maPhieuYC, dsPhanBo, lyDo)` |
| **`PhieuYeuCauXuat`** *(Entity)* | `maPhieuYeuCau`, `maKeHoach`, `xuongYeuCau`, `ngayYeuCau`, `lyDoXuat`, `tongSoLuong`, `trangThai` | `layDanhSachPhieuChoXuLy(trangThai)`, `capNhatTrangThaiPhieu(maPhieuYC, trangThai)` |
| **`ChiTietYeuCauXuat`** *(Entity)* | `maChiTiet`, `maPhieuYeuCau`, `maNL`, `soLuongYeuCau`, `donViTinh` | `layChiTietYeuCau(maPhieuYC)` |
| **`LoNguyenLieu`** *(Entity)* | `maLo`, `maNL`, `ngaySanXuat`, `hanSuDung`, `soLuongTon`, `soLuongReserved`, `trangThai` | `quetLoAvailableTheoFEFO(maNL)`, `capNhatSoLuongReserved(maLo, slAdded)` |
| **`ViTriKho`** *(Entity)* | `maViTri`, `maKho`, `day`, `ke`, `tang`, `oslot`, `trangThai` | `layToaDoViTriKho(maLo)` |
| **`LenhDieuPhoi`** *(Entity)* | `maLenh`, `maPhieuYeuCau`, `maKho`, `ngayDieuPhoi`, `nguoiDieuPhoi`, `trangThai` | `taoLenhDieuPhoiMoi(maLenh, maPhieuYC, maKho, ngayDP, nguoiDP, trangThai)` |
| **`ChiTietLenhDieuPhoi`** *(Entity)* | `maChiTiet`, `maLenh`, `maLo`, `maViTri`, `soLuongPhanBo` | `taoChiTietLenhDieuPhoi(maChiTiet, maLenh, maLo, maViTri, slPhanBo)` |
| **`FEFOAuditLog`** *(Entity)* | `maLog`, `maPhieuYeuCau`, `maLoGoiY`, `maLoChon`, `lyDoBoQuaFEFO`, `nguoiThucHien`, `thoiGian` | `ghiVetNhatKyViPham(logID, maPhieuYC, maLoGoiY, maLoChon, lyDo, nguoiTH, thoiGian)` |

---

## 5. USE CASE 2.5: QUẢN LÝ VAI TRÒ VÀ PHÂN QUYỀN

### Bảng 1: Trích xuất Message và ứng viên Operation (UC 2.5)

| Message | Đối tượng nhận | Ứng viên Operation |
| :--- | :--- | :--- |
| `1: ChonChucNangQuanLyVaiTroAndPhanQuyen()` | `GiaoDienQuanLyPhanQuyen` | `chonChucNangQuanLyVaiTroAndPhanQuyen()` |
| `2: TruyXuatDanhSachVaiTro()` | `QuanLyPhanQuyenControl` | `truyXuatDanhSachVaiTro()` |
| `3: LayDanhSachVaiTro()` | `VaiTro` | `layDanhSachVaiTro()` |
| `4: DSVaiTro(maVaiTro, tenVaiTro, moTa, isDeleted)` | `QuanLyPhanQuyenControl` | *(Return message)* |
| `5: DemSoUserTheoVaiTro(maVaiTro)` | `TaiKhoan` | `demSoUserTheoVaiTro(maVaiTro: String)` |
| `6: TraVeSoUser(soUser)` | `QuanLyPhanQuyenControl` | *(Return message)* |
| `7: HienThiDanhSachVaiTroAndMatrix(DSVaiTro, SoUserMap)` | `GiaoDienQuanLyPhanQuyen` | `hienThiDanhSachVaiTroAndMatrix(dsRole: List, userMap: Map)` |
| `1a: NhapThongTinVaiTroMoi(tenVaiTro, moTa)` | `GiaoDienQuanLyPhanQuyen` | `nhapThongTinVaiTroMoi(ten: String, moTa: String)` |
| `2a: ThemVaiTroMoi(tenVaiTro, moTa)` | `QuanLyPhanQuyenControl` | `themVaiTroMoi(ten: String, moTa: String)` |
| `3a: KiemTraTenDuyNhat(tenVaiTro)` | `VaiTro` | `kiemTraTenDuyNhat(ten: String)` |
| `4a: LuuVaiTroMoi(autoMaVaiTro, tenVaiTro, moTa)` | `VaiTro` | `luuVaiTroMoi(maVaiTro, ten, moTa)` |
| `5a: VaiTroCreated` | `QuanLyPhanQuyenControl` | *(Return message)* |
| `6a: HienThiThongBao('Thêm vai trò mới thành công')` | `GiaoDienQuanLyPhanQuyen` | `hienThiThongBao(msg: String)` |
| `1b: BamNutXoa(maVaiTro)` | `GiaoDienQuanLyPhanQuyen` | `bamNutXoa(maVaiTro: String)` |
| `2b: YeuCauXoaVaiTro(maVaiTro)` | `QuanLyPhanQuyenControl` | `yeuCauXoaVaiTro(maVaiTro: String)` |
| `3b: KiemTraSoUserDangDung(maVaiTro)` | `TaiKhoan` | `kiemTraSoUserDangDung(maVaiTro: String)` |
| `4b.1: HienThiThongBaoLoi('Không thể xóa vai trò đang có người dùng')` | `GiaoDienQuanLyPhanQuyen` | `hienThiThongBaoLoi(msg: String)` |
| `4b.2: CapNhatXoaMem(maVaiTro, isDeleted=true)` | `VaiTro` | `capNhatXoaMem(maVaiTro: String, isDeleted: Boolean)` |
| `5b: SoftDeleted` | `QuanLyPhanQuyenControl` | *(Return message)* |
| `6b: HienThiThongBao('Xóa vai trò thành công')` | `GiaoDienQuanLyPhanQuyen` | `hienThiThongBao(msg: String)` |
| `1c: ChonPhanQuyen(maVaiTro, DSQuyenChecked)` | `GiaoDienQuanLyPhanQuyen` | `chonPhanQuyen(maVaiTro: String, dsQuyen: List)` |
| `2c: CapNhatMaTranPhanQuyen(maVaiTro, DSQuyen)` | `QuanLyPhanQuyenControl` | `capNhatMaTranPhanQuyen(maVaiTro: String, dsQuyen: List)` |
| `3c: LuuMappingPhanQuyen(maVaiTro, maChucNang, xem, them, sua, xoa, duyet)` | `PhanQuyen` | `luuMappingPhanQuyen(maRole, maFunc, xem, them, sua, xoa, duyet)` |
| `4c: MappingUpdated` | `QuanLyPhanQuyenControl` | *(Return message)* |
| `5c: HienThiThongBao('Cập nhật phân quyền thành công')` | `GiaoDienQuanLyPhanQuyen` | `hienThiThongBao(msg: String)` |

### Bảng 2: Tổng hợp Đối tượng, Thuộc tính và Phương thức (UC 2.5)

| Đối tượng | Thuộc tính | Phương thức (Operations) |
| :--- | :--- | :--- |
| **`GiaoDienQuanLyPhanQuyen`** *(Boundary)* | `maVaiTroSelected`, `tenRoleInput`, `moTaRoleInput`, `checkedMatrixMap` | `chonChucNangQuanLyVaiTroAndPhanQuyen()`, `hienThiDanhSachVaiTroAndMatrix(dsRole, userMap)`, `nhapThongTinVaiTroMoi(ten, moTa)`, `hienThiThongBao(msg)`, `bamNutXoa(maVaiTro)`, `hienThiThongBaoLoi(msg)`, `chonPhanQuyen(maVaiTro, dsQuyen)` |
| **`QuanLyPhanQuyenControl`** *(Control)* | `soUserCurrent`, `isSystemRole` | `truyXuatDanhSachVaiTro()`, `themVaiTroMoi(ten, moTa)`, `yeuCauXoaVaiTro(maVaiTro)`, `capNhatMaTranPhanQuyen(maVaiTro, dsQuyen)` |
| **`VaiTro`** *(Entity)* | `maVaiTro`, `tenVaiTro`, `moTa`, `ngayTao`, `isDeleted`, `laMacDinh` | `layDanhSachVaiTro()`, `kiemTraTenDuyNhat(ten)`, `luuVaiTroMoi(maVaiTro, ten, moTa)`, `capNhatXoaMem(maVaiTro, isDeleted)` |
| **`TaiKhoan`** *(Entity)* | `maTaiKhoan`, `maNV`, `maVaiTro`, `tenDangNhap`, `matKhau`, `trangThai` | `demSoUserTheoVaiTro(maVaiTro)`, `kiemTraSoUserDangDung(maVaiTro)` |
| **`PhanQuyen`** *(Entity)* | `maVaiTro`, `maChucNang`, `xem`, `them`, `sua`, `xoa`, `duyet` | `luuMappingPhanQuyen(maRole, maFunc, xem, them, sua, xoa, duyet)` |
