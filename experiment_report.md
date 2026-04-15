# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600036
**Name:** Do Dinh Hoan
**Date:** 2026-04-15

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | `Agent: Based on my data, the best choice is Laptop at $1200.` | 9 | Du lieu clean chi con 3 record hop le sau validation. Agent tim dung nhom Electronics va chon Laptop la san pham co gia cao nhat trong nhom nay, nen cau tra loi hop ly voi tap du lieu da xu ly. |
| Garbage Data (`garbage_data.csv`) | `Agent: Based on my data, the best choice is Nuclear Reactor at $999999.` | 2 | Cau tra loi nay bi dan dat boi outlier gia rat lon. Agent van chay duoc, nhung ket qua khong dang tin cay vi bo du lieu rac co record bat thuong va khong duoc kiem soat chat luong. |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Agent tra loi sai khi dung `garbage_data.csv` vi logic trong `agent_simulation.py` chon record electronics co gia cao nhat bang `idxmax()`. Trong bo du lieu rac, record `Nuclear Reactor` co gia `999999`, la mot outlier cuc lon so voi cac san pham con lai. Vi khong co buoc validation, agent xem record nay la hop le va dua ra mot cau tra loi rat tu tin nhung sai trong boi canh mua sam thong thuong.

Ngoai outlier, bo du lieu rac con chua nhieu van de chat luong khac nhu duplicate ID, sai kieu du lieu (`ten dollars`) va null values. Nhung loi nay lam giam do tin cay cua toan bo tap du lieu. Trong he thong ETL hoac RAG thuc te, du lieu xau se dan den truy van sai, ranking sai, thong ke sai va co the gay loi xu ly o cac buoc sau. Thi nghiem nay cho thay neu khong lam sach du lieu tu dau, agent co the dua ra ket qua co ve hop ly ve mat cau truc nhung lai sai ve mat nghiep vu.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** (Dong y hay khong? Giai thich ngan gon.)

Dong y. Prompt tot chi giup agent dien dat hoac suy luan ro hon tren du lieu hien co, nhung khong the sua mot nguon du lieu sai hoac bi nhiem rac. Chat luong du lieu, validation va observability la nen tang de agent tra loi dung va on dinh.
