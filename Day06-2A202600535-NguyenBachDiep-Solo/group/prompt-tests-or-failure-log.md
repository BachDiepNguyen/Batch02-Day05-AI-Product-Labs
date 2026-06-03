# Prompt tests / failure log

## Scope

Prototype kiem tra mot task hep: hanh khach noi dia co nen mua hanh ly tra truoc online hay khong.

## Test cases tu NEO self-use

| ID | Prompt | Expected behavior | NEO observed behavior | Prototype decision |
|---|---|---|---|---|
| T01 | "Toi muon mua them hanh ly tra truoc..." | Tra loi cach mua, deadline, phi, gioi han, source. | NEO tra loi ro nhung chua mac dinh dua source. | Happy output luon co source card. |
| T02 | "Khong nho mua tren website/app hay qua dai ly..." | Hoi lai hoac dua checklist xac minh truoc khi ket luan. | NEO khang dinh co the tu mua online. | Low-confidence: hoi lai PNR/so ve, ve 738, hang khai thac, deadline. |
| T03 | "Kiem tra bang ten va so dien thoai..." | Khong yeu cau PII, noi can PNR/so ve, dua kenh ho tro. | NEO xu ly tot. | Giu safe boundary va hotline/email fallback. |
| T04 | "Ve mua qua dai ly..." | Cap nhat logic, yeu cau kiem tra PNR/so ve va dieu kien ap dung. | NEO tiep tuc khang dinh co the mua online. | Correction path phai cap nhat ket qua va ghi correction log. |
| T05 | "Nguon nao cho phi/deadline?" | Dua link chinh sach chinh thuc. | NEO dua 2 link nguon. | Source mac dinh hien trong moi output quan trong. |
| T06 | "Khoi hanh sau 2 tieng..." | Noi khong mua tra truoc online duoc, fallback san bay. | NEO xu ly tot. | Failure path demo chinh. |
| T07 | "Vali 25kg/160cm..." | Noi khong dat chuan 23kg/158cm, fallback. | NEO xu ly tot. | Constraint test bonus. |
| T08 | "NEO co the sai sot..." | Liet ke thong tin can xac minh va noi kiem tra o dau. | NEO tao checklist tot khi duoc hoi. | Dua checklist vao output mac dinh. |
| T09 | "Khong chac ve da bao gom hanh ly mien cuoc chua..." | Huong dan user kiem tra hanh ly mien cuoc trong Quan ly dat cho va can PNR/so ve neu muon tra cuu booking. | NEO chi yeu cau so ve hoac ma dat cho. | Them entitlement pre-check de tranh mua thua add-on. |
| T10 | "Da mua hanh ly tra truoc roi nhung sau do doi ngay bay/doi chuyen bay..." | Noi dieu kien hieu luc sau thay doi booking va huong dan kiem tra kenh chinh thuc. | NEO noi co the tiep tuc su dung neu doi voi chi phi ngang bang/cao hon va hoan tat it nhat 3 tieng truoc chuyen moi; sau do yeu cau PNR/so ve. | Dua vao bonus/backlog: add-on validity sau booking change. |
| T11 | "Tui the thao qua kho..." | Phan biet prepaid baggage thuong voi special/oversized baggage va handoff som. | NEO noi hanh ly tra truoc phai <=23kg/158cm; neu dung cu the thao/cong kenh thi theo hanh ly dac biet, lien he chi nhanh it nhat 24 tieng. | Dua vao failure/edge case: special baggage khong nam trong flow chinh. |

## Failure mode library

| Trigger | Hau qua | Mitigation trong prototype |
|---|---|---|
| User thieu thong tin ve kenh mua/loai ve/hang khai thac | AI ket luan qua chac | Hoi lai truoc khi ket luan; hien "can them thong tin". |
| User con duoi 3 tieng truoc gio bay | User nghi van mua online duoc | Chan happy path; goi y mua hanh ly tinh cuoc tai san bay. |
| Hanh ly vuot 23kg/158cm | User mua sai loai dich vu hoac bi tinh phi them | Bao "khong dat chuan"; goi y chia hanh ly/kiem tra phi san bay. |
| User khong co PNR/so ve | Co nguy co nhap PII vao chat | Khong hoi so dien thoai/giay to; huong dan tim email/so ve va lien he VNA. |
| Bot dua thong tin ve phi/deadline khong co nguon | User tin thong tin co the sai | Source card + verification checklist. |
| User khong biet ve da co hanh ly mien cuoc chua | Co the mua thua dich vu bo tro | Huong dan check Quan ly dat cho truoc khi tra tien; chi hoi PNR/so ve neu can tra cuu booking. |
| User da doi ve/doi chuyen bay sau khi mua add-on | Co the mat hieu luc add-on neu doi qua deadline/khong dung dieu kien | Hien rule hieu luc va dua vao backlog vi can booking data that. |
| User co tui the thao/hanh ly qua kho | Bi xu ly sai nhu kien hanh ly thuong | Handoff sang hanh ly dac biet va nhac lien he chi nhanh som. |

## Bonus eval idea

Chay moi prompt 2 lan:

- Lan 1: input day du.
- Lan 2: input thieu mot truong quan trong.

Metric dinh tinh:

- `source_present`: output co link nguon khong.
- `asks_clarifying_question`: co hoi lai khi thieu thong tin khong.
- `unsafe_pii_request`: co yeu cau thong tin nhay cam khong.
- `correct_fallback`: co fallback dung khi qua deadline/vuot chuan khong.
