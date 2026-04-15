[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23574206&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student ID:** 2A202600036  
**Name:** Do Dinh Hoan  
**Student Email:** 26ai.hoandd@vinuni.edu.vn

---

## Mo ta

Trong bai lab nay, toi xay dung mot ETL pipeline don gian de xu ly du lieu san pham tu file `raw_data.json`. Pipeline thuc hien day du 4 buoc `extract`, `validate`, `transform`, `load`, sau do ghi ket qua ra `processed_data.csv`. Ngoai phan ETL, project con mo phong mot agent tra loi dua tren du lieu da xu ly va so sanh hanh vi cua agent khi dung clean data va garbage data.

Muc tieu cua bai lab la cho thay chat luong du lieu anh huong truc tiep den ket qua cua he thong AI. Khi du lieu duoc lam sach, agent dua ra cau tra loi hop ly. Khi du lieu rac khong duoc kiem soat, agent van tra loi duoc nhung ket qua bi lech boi outlier va cac loi chat luong du lieu.

---

## Cach chay

### Cai dat thu vien

```bash
pip install pandas pytest
```

### Chay ETL pipeline

```bash
python solution.py
```

Pipeline se:
- Doc du lieu tu `raw_data.json`
- Loai record co `price <= 0`
- Loai record co `category` rong
- Chuan hoa `category` sang Title Case
- Them cot `discounted_price = price * 0.9`
- Them cot `processed_at`
- Luu ket qua vao `processed_data.csv`

### Tao garbage data

```bash
python generate_garbage.py
```

### Chay stress test cho agent

```bash
python agent_simulation.py
```

### Chay local autograder

```bash
python -m pytest tests -q -p no:cacheprovider
```

---

## Cau truc thu muc

```text
|-- solution.py
|-- raw_data.json
|-- processed_data.csv
|-- generate_garbage.py
|-- garbage_data.csv
|-- agent_simulation.py
|-- experiment_report.md
|-- tests/
`-- README.md
```

---

## Ket qua

Sau khi chay `solution.py`, pipeline doc tong cong 5 records tu file nguon, giu lai 3 records hop le va loai 2 records khong hop le. File `processed_data.csv` duoc tao thanh cong va co them hai cot moi la `discounted_price` va `processed_at`.

Ket qua stress test cho thay su khac biet ro rang giua clean data va garbage data:
- Voi `processed_data.csv`, agent tra loi: `Laptop` la lua chon tot nhat trong nhom electronics.
- Voi `garbage_data.csv`, agent tra loi: `Nuclear Reactor` la lua chon tot nhat vi bi anh huong boi outlier gia rat lon.

Dieu nay cho thay data quality la yeu to nen tang. Prompt co the tot, nhung neu du lieu dau vao sai hoac bi nhiem rac thi ket qua cua agent van se khong dang tin cay.
