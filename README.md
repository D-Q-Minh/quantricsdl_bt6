# Bài tập 6
#####
Yêu cầu bài tập: 
Cho file sv_tnut.sql (1.6MB)
1. Hãy nêu các bước để import được dữ liệu trong sv_tnut.sql vào sql server của em
2. dữ liệu đầu vào là tên của sv; sđt; ngày, tháng, năm sinh của sinh viên (của sv đang làm bài tập này)
3. nhập sql để tìm xem có những sv nào trùng hoàn toàn ngày/tháng/năm với em?
4. nhập sql để tìm xem có những sv nào trùng ngày và tháng sinh với em?
5. nhập sql để tìm xem có những sv nào trùng tháng và năm sinh với em?
6. nhập sql để tìm xem có những sv nào trùng tên với em?
7. nhập sql để tìm xem có những sv nào trùng họ và tên đệm với em.
8. nhập sql để tìm xem có những sv nào có sđt sai khác chỉ 1 số so với sđt của em.
9. BẢNG SV CÓ HƠN 9000 ROWS, HÃY LIỆT KÊ TẤT CẢ CÁC SV NGÀNH KMT, SẮP XẾP THEO TÊN VÀ HỌ ĐỆM, KIỂU TIẾNG  VIỆT, GIẢI THÍCH.
10. HÃY NHẬP SQL ĐỂ LIỆT KÊ CÁC SV NỮ NGÀNH KMT CÓ TRONG BẢNG SV (TRÌNH BÀY QUÁ TRÌNH SUY NGHĨ VÀ GIẢI NHỮNG VỨNG MẮC)

DEADLINE: 23H59:59 NGÀY 25/4/2025
## Bài làm:
##### 1. Import dữ liệu trong sv_tnut.sql vào sql server
###### tạo server sv_tnut
![1](https://github.com/user-attachments/assets/1499382f-448f-4346-b20f-fd707c666499)
###### Execute file sv_tnut.sql
![2](https://github.com/user-attachments/assets/d226d6aa-ce30-40ad-9789-7fb4e9d6ac06)

##### 2. dữ liệu đầu vào là tên của sv; sđt; ngày, tháng, năm sinh của sinh viên (của sv đang làm bài tập này)
```sql
select hodem, ten, sdt, ns from dbo.SV
where masv='K225480106047'
```
![2 sv lam bai](https://github.com/user-attachments/assets/096533ea-6df3-43c7-be2f-ac67f791bca9)

##### 3. tìm xem có những sv nào trùng hoàn toàn ngày/tháng/năm với sv làm bài
```sql
select * from dbo.SV
where ns = (select ns from dbo.SV where masv = 'K225480106047')
```
![3 sv trung ns](https://github.com/user-attachments/assets/9656d7ba-f9e7-4cb3-8bfb-56fbfaf81247)

##### 4. tìm xem có những sv nào trùng ngày và tháng sinh với sv làm bài
```sql
select * from dbo.SV
where day(ns) = day((select ns from dbo.SV where masv = 'K225480106047'))
	and MONTH(ns)=MONTH((select ns from dbo.SV where masv = 'K225480106047'))
```
![4 sv trung ns ngay thang](https://github.com/user-attachments/assets/2d9668a3-3b65-402a-9564-bc08bc3098a7)

##### 5. tìm xem có những sv nào trùng tháng và năm sinh với sv làm bài
```sql
select * from dbo.SV
where MONTH(ns)=MONTH((select ns from dbo.SV where masv = 'K225480106047'))
	and year(ns)=year((select ns from dbo.SV where masv = 'K225480106047'))
```
![5 sv trung ns thang nam](https://github.com/user-attachments/assets/da5f3408-7327-4781-a7f0-16491b7c1611)

##### 6. tìm xem có những sv nào trùng tên với sv làm bài
```sql
select * from dbo.SV
where ten = (select ten from dbo.SV where masv = 'K225480106047')
```
![6 sv trung ten](https://github.com/user-attachments/assets/af944d2b-9832-4bd1-bb96-f886434a1f5c)

