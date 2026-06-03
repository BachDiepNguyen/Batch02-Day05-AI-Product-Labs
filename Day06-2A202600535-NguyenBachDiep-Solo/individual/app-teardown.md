# Individual UX Exercise - Mo app AI that: Vietnam Airlines NEO

**Hoc vien:** Nguyễn Bách Điệp  
**ID hoc vien:** 2A202600535

## 1. Product chosen

**Product:** Vietnam Airlines NEO chatbot  
**AI feature:** Chatbot ho tro thong tin chuyen bay, ve, hanh ly, dich vu bo tro va kenh lien he.  
**Task tested:** Mua them hanh ly tra truoc cho chuyen bay noi dia.

## 2. Promise vs reality

**Promise:** NEO la chatbot thong minh giup nguoi dung tim thong tin va giai dap thac mac nhanh.  
**Expected user:** Hanh khach can tra loi nhanh truoc khi bay, dac biet voi task lien quan hanh ly/phi/deadline.  
**Expected AI task:** Tra loi user co mua hanh ly tra truoc duoc khong, mua o dau, dieu kien nao can kiem tra.  
**Reality observed:** NEO tra loi tot voi FAQ ro, nhung khi input thieu ngu canh, bot co xu huong ket luan chac chan thay vi hoi lai. Source chi xuat hien khi user hoi truc tiep.

## 3. Four paths

| Path | What happened in NEO | Product reading |
|---|---|---|
| Happy | NEO tra loi cach mua, deadline 3 tieng, phi, gioi han 23kg/158cm. | FAQ co rule ro duoc xu ly tot. |
| Low-confidence | User khong nho mua qua website/app/dai ly, NEO van khang dinh co the tu mua online. | Thieu ask-again path cho input chua du dieu kien. |
| Failure | User khoi hanh sau 2 tieng, NEO noi khong mua tra truoc online duoc va goi y mua tai san bay. | Failure recovery tot, co the them source/fare warning. |
| Correction | User sua thanh ve mua qua dai ly, NEO van lap lai "co the mua online". | Correction chua tao ra verification checklist rieng. |
| Bonus edge | User hoi tui the thao qua kho, NEO route sang hanh ly dac biet va lien he chi nhanh truoc 24 tieng. | Bot co boundary tot khi task ro la special baggage; to-be flow nen handoff som voi edge case nay. |

## 4. Finding -> product decision

```text
Khi user hoi ve mua hanh ly tra truoc nhung thieu thong tin ve kenh mua, loai ve, hang khai thac hoac thoi gian con lai,
NEO co the tra loi qua chac thay vi hoi lai,
hau qua la user tin rang minh co the tu mua online trong moi truong hop va co the phat hien qua muon khi ra san bay.
Loi thuoc layer Intent + Data/Tool + UX Recovery.
Nen sua bang low-confidence path: hoi lai 2-3 thong tin bat buoc, hien checklist dieu kien, va dua source mac dinh cho thong tin co chi phi/deadline.
Do bang: ty le output co source, ty le prompt thieu thong tin duoc hoi lai, va so correction/handoff.
```

## 5. As-is sketch

```text
User hoi ve hanh ly tra truoc
        |
        v
NEO tra loi FAQ chung
        |
        +--> Neu cau hoi ro: user co buoc mua
        |
        +--> Neu cau hoi thieu thong tin: NEO van ket luan kha chac
        |
        v
User phai tu hoi them nguon/dieu kien neu muon xac minh
```

## 6. To-be sketch

```text
User hoi ve hanh ly tra truoc
        |
        v
AI check cac truong bat buoc:
deadline / ve 738 / hang khai thac / ATR72 / PNR-so ve / 23kg-158cm
        |
        +--> Du thong tin + eligible:
        |       hien checklist mua + source + CTA "vao Quan ly dat cho"
        |
        +--> Thieu thong tin:
        |       hoi lai 2-3 cau, khong ket luan
        |
        +--> Khong eligible:
                hien fallback san bay/hotline + source + risk note
```

## 7. What changes in SPEC

Finding nay doi SPEC tu "chatbot tra loi ve hanh ly" thanh "eligibility checker co source va failure path". Prototype phai demo it nhat mot low-confidence path, mot failure path, va mot correction log.

Bonus evidence tu prompt 10-11 cho thay co hai route khong nen build sau trong 1 ngay: add-on validity sau khi doi booking va hanh ly dac biet/tui the thao qua kho. Hai route nay nen nam o backlog hoac handoff, khong tron vao happy path hanh ly tra truoc.
