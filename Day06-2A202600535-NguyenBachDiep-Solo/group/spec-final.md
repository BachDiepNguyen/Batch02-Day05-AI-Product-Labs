# Thin SPEC - NEO baggage eligibility checker

## 1. Track, product/app va user

**Track:** Travel & Hospitality  
**Hoc vien:** Nguyễn Bách Điệp - 2A202600535  
**Product/app that:** Vietnam Airlines NEO chatbot  
**User cu the:** Hanh khach noi dia da mua ve Vietnam Airlines, muon mua them hanh ly tra truoc nhung khong chac dieu kien ap dung.  
**Nhom co phai user that khong? Neu khong, khac o dau?** Nhom co the dong vai hanh khach tuong tu khi hoi thong tin hanh ly. Khac biet: chua co booking that, nen khong test duoc booking lookup/PNR that.

## 2. Evidence summary

| Evidence | Nguon | User/pain noi len dieu gi? | SPEC phai doi gi? |
|---|---|---|---|
| NEO tra loi happy path: cach mua, deadline 3 tieng, phi, 23kg/158cm. | Self-use screenshot `evidence/screenshots/neo-01-happy-baggage.JPG` | FAQ ro thi NEO tra loi duoc. | Prototype khong can "bot moi" tra loi FAQ chung; can them eligibility + source. |
| NEO khang dinh co the tu mua online ngay ca khi user khong nho kenh mua. | Self-use screenshot `evidence/screenshots/neo-02-low-confidence-channel.JPG` | Input thieu ngu canh nhung bot van tra loi chac. | Them low-confidence path: hoi lai PNR/so ve, kenh mua, hang khai thac, deadline. |
| NEO tu choi tra cuu bang ten + so dien thoai, yeu cau PNR/so ve va dua hotline/email. | Self-use screenshot `evidence/screenshots/neo-03-safe-boundary.JPG` | Safe boundary tot khi lien quan booking ca nhan. | Giu pattern nay: khong nhap PII, chuyen kenh chinh thuc khi can. |
| Khi user hoi nguon, NEO dua link chinh sach. | Self-use screenshot `evidence/screenshots/neo-05-source-request.JPG` | Source co san nhung khong hien mac dinh. | Output mac dinh phai co source card. |
| NEO xu ly case khoi hanh sau 2 tieng: khong mua online, ra san bay mua hanh ly tinh cuoc. | Self-use screenshot `evidence/screenshots/neo-06-deadline-failure.JPG` | Failure path co gia tri thuc te. | Prototype phai demo case qua deadline. |
| NEO gap prompt "ve da bao gom hanh ly mien cuoc chua?" va chi yeu cau so ve/ma dat cho. | Self-use screenshot `evidence/screenshots/neo-09-entitlement-check.JPG` | Entitlement la thong tin user can biet truoc khi tra tien, nhung booking lookup khong phai luc nao user san sang cung cap. | Them checklist "kiem tra hanh ly mien cuoc trong Quan ly dat cho" truoc khi mua add-on. |
| NEO tra loi case da mua hanh ly tra truoc nhung doi ngay/chuyen bay: co the tiep tuc su dung neu doi voi chi phi ngang bang/cao hon va hoan tat it nhat 3 tieng truoc chang bay moi. | Self-use screenshot `evidence/screenshots/neo-10-add-on-validity.JPG` | Add-on co dieu kien hieu luc sau booking change; user can biet truoc de tranh mat tien. | Dua vao bonus/backlog: booking changed route can booking data that. |
| NEO tra loi case tui the thao qua kho: neu la dung cu the thao/hanh ly cong kenh thi theo hanh ly dac biet, lien he chi nhanh it nhat 24 tieng truoc gio khoi hanh. | Self-use screenshot `evidence/screenshots/neo-11-special-baggage.JPG` | Special baggage la route khac prepaid baggage thuong. | Edge case: neu special/oversized, prototype handoff som thay vi xu ly nhu kien thuong. |
| Dieu khoan NEO noi phan hoi co the khong chinh xac, user nen xac minh thong tin quan trong. | Vietnam Airlines - Dieu khoan su dung Chatbot NEO | Trust risk chinh thuc duoc thua nhan. | To-be UX can dua verification checklist vao output. |

## 3. Pain statement

```text
User la hanh khach noi dia da mua ve Vietnam Airlines dang gap kho o buoc quyet dinh co nen mua hanh ly tra truoc online,
vi dieu kien mua phu thuoc vao hanh ly mien cuoc da co trong ve, deadline 3 tieng, ve 738, hang khai thac, ngoai le ATR72, PNR/so ve, va gioi han 23kg/158cm,
dan toi viec user co the tin vao cau tra loi chung chung, mua thua/mua sai cach, hoac ra san bay moi biet phai tra phi cao hon.
Bang chung chinh la self-use voi NEO: bot tra loi tot khi hoi ro, nhung khong hoi lai khi user thieu thong tin ve kenh mua/dieu kien ve.
```

## 4. Build slice

```text
Cho hanh khach noi dia da mua ve dang muon mua them hanh ly tra truoc,
prototype se dung AI de hoi lai cac thong tin bat buoc va check entitlement/eligibility cho mot kien hanh ly,
tao ra checklist hanh dong co nguon xac minh,
va xu ly failure mode "thieu dieu kien/qua deadline/vuot chuan hanh ly/co the mua thua add-on" bang ask-again, source card va fallback sang Quan ly dat cho/san bay/hotline.
```

## 5. Auto/Aug decision

- [x] **Augmentation:** AI goi y/checklist, user quyet cuoi.
- [ ] **Conditional automation:** AI tu lam trong case hep; case mo ho/rui ro chuyen nguoi.
- [ ] **Automation:** AI tu quyet va tu hanh dong.

**Ly do chon:** Task lien quan chi phi, dieu kien ve va deadline. Sai co the lam user mat tien/thoi gian, nhung user van co the tu quyet neu AI dua checklist + source ro.  
**Human role:** Decider + rescuer. User quyet mua/khong mua; Vietnam Airlines support/reservation channel can thiep khi user khong co PNR/so ve hoac case khong eligible.

## 6. Four paths

| Path | Prototype phai the hien gi? |
|---|---|
| Happy | User du thong tin: da kiem tra hanh ly mien cuoc, con hon 3 tieng, ve 738, Vietnam Airlines/Pacific Airlines, khong ATR72, kien <=23kg va <=158cm. Output: "Co the mua hanh ly tra truoc neu hanh ly hien co chua du", cac buoc mua, source link. |
| Low-confidence | User thieu kenh mua/PNR/so ve/hang khai thac/thoi gian. Output: khong ket luan ngay; hoi lai 2-3 thong tin bat buoc va giai thich vi sao can. |
| Failure | Qua deadline 3 tieng, kien 25kg/160cm, user chua biet ve da co hanh ly mien cuoc chua, hoac hanh ly la special/oversized. Output: "Chua nen tra tien ngay", fallback kiem tra Quan ly dat cho / mua hanh ly tinh cuoc tai san bay / lien he chi nhanh neu hanh ly dac biet, source link, canh bao co the ton phi cao hon. |
| Correction | User sua thong tin, vi du "ve mua qua dai ly" hoac "vali 25kg". Prototype cap nhat ket qua, ghi correction log, hien rule bi anh huong. |

## 7. Failure mode nguy hiem nhat

```text
Neu user khong chac hanh ly mien cuoc da co trong ve, kenh mua, loai ve hoac hang khai thac nhung hoi "toi co nen mua them hanh ly online khong",
AI co the tra loi qua chac hoac chi yeu cau PNR/so ve ma khong dua checklist tu xac minh,
hau qua la user co the mua thua add-on, khong mua duoc dung han hoac phai tra phi tai san bay.
Prototype se xu ly bang ask again + entitlement/eligibility checklist + source card + fallback Quan ly dat cho/hotline/san bay.
Owner kiem thu path nay la Nguyễn Bách Điệp.
```

## 8. Owner plan cho sang Day 06

| Thanh vien | Viec phu trach | Bang chung can co trong repo |
|---|---|---|
| Nguyễn Bách Điệp | Research / evidence | 11 screenshot NEO + link chinh sach Vietnam Airlines |
| Nguyễn Bách Điệp | SPEC | `group/spec-final.md` |
| Nguyễn Bách Điệp | Prototype | `prototype/index.html` |
| Nguyễn Bách Điệp | Test / failure path | `group/prompt-tests-or-failure-log.md` |
| Nguyễn Bách Điệp | Demo script / repo | `group/demo-script.md`, `group/prototype-readme.md`, `individual/reflection.md` |

## 9. Backlog

Nhung thu khong build trong Day 06:

- Tra cuu booking that bang PNR/so ve.
- Thanh toan hanh ly truc tiep.
- Tich hop API gia phi theo tung hanh trinh.
- Xu ly add-on sau khi doi ve/doi chuyen bay bang booking that.
- Xu ly hanh ly dac biet/tui the thao qua kho nhu mot flow rieng.
- Ho tro quoc te/nhieu chang/noi chuyen phuc tap.
- Dang nhap Lotusmiles hoac xu ly thong tin ca nhan.
