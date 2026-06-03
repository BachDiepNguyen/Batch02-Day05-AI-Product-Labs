# Evidence Pack - NEO baggage helper

## 1. Nhom va track

**Ten nhom:** Solo - Nguyễn Bách Điệp  
**ID hoc vien:** 2A202600535  
**Track:** Travel & Hospitality  
**Product/app da chon:** Vietnam Airlines NEO chatbot  
**Build slice dang nghi:** AI baggage pre-check cho hanh khach muon mua hanh ly tra truoc nhung chua chac dieu kien ap dung.

## 2. Self-use evidence

Nguon self-use: Nguyễn Bách Điệp truc tiep chat voi NEO tren trang `vietnamairlines.com/vn/vi/support/chatbot`, ngay 2026-06-03.

| Observation | Screenshot/link | Path lien quan | Dieu hoc duoc |
|---|---|---|---|
| Prompt: "Toi muon mua them hanh ly tra truoc cho chuyen bay noi dia..." NEO tra loi ro cach mua, han mua 3 tieng, phi 300.000 VND/kien, gioi han 23kg/158cm. | `evidence/screenshots/neo-01-happy-baggage.JPG` | Happy | NEO co the tra loi dung task FAQ co rule ro. Tuy nhien cau tra loi dau tien chua mac dinh hien link nguon, trong khi day la thong tin ve tien va deadline. |
| Prompt: "Toi da mua ve roi nhung khong nho la mua tren website, app, hay qua dai ly..." NEO khang dinh van co the tu mua online, khong hoi lai. | `evidence/screenshots/neo-02-low-confidence-channel.JPG` | Low-confidence | Khi input thieu ngu canh ve kenh mua/loai ve, NEO co xu huong tra loi chac chan thay vi hoi lai 1-2 thong tin bat buoc. |
| Prompt: "Toi khong co ma dat cho... kiem tra bang ten hanh khach va so dien thoai..." NEO tu choi tra cuu bang ten + so dien thoai, yeu cau PNR/so ve, dua hotline/email. | `evidence/screenshots/neo-03-safe-boundary.JPG` | Failure / safe boundary | NEO co boundary tot voi thong tin ca nhan va booking lookup. Day la recovery path co the hoc cho prototype. |
| Prompt correction: "Y toi la ve mua qua dai ly du lich..." NEO tiep tuc khang dinh co the tu mua online va lap lai dieu kien. | `evidence/screenshots/neo-04-correction-agency.JPG` | Correction | NEO nhan correction nhung chua bien correction thanh check-list xac minh rui ro. Nen co buoc "kiem tra PNR/so ve 738, hang khai thac, ATR72, han 3 tieng" truoc khi ket luan. |
| Prompt: "Ban lay thong tin phi 300.000 VND/kien va han mua truoc 3 tieng tu nguon nao?" NEO dua 2 link chinh sach chinh thuc. | `evidence/screenshots/neo-05-source-request.JPG` | Trust / source | Khi user hoi, NEO co the dua nguon. Product opportunity: voi thong tin quan trong, nguon nen duoc hien mac dinh, khong doi user hoi. |
| Prompt: "Chuyen bay khoi hanh sau 2 tieng nua..." NEO noi khong the mua hanh ly tra truoc online nua va goi y mua hanh ly tinh cuoc tai san bay. | `evidence/screenshots/neo-06-deadline-failure.JPG` | Failure / recovery | NEO xu ly tot rule 3 tieng va co fallback. Prototype nen giu behavior nay, kem source va next action ro hon. |
| Prompt: "Vali 25kg, 160cm..." NEO phat hien vuot 23kg va 158cm, goi y tra phi phan vuot tai san bay. | `evidence/screenshots/neo-07-constraint-test.JPG` | Failure / constraint | NEO xu ly constraint tot. Co the them suggestion de giam thiet hai: chia bot hanh ly neu con thoi gian, kiem tra phi truoc khi ra san bay. |
| Prompt: "NEO co the sai sot... thong tin nao nen tu kiem tra lai?" NEO liet ke deadline, 23kg/158cm, ve 738, Vietnam Airlines/Pacific Airlines, tru ATR72, hieu luc voi dung chuyen bay/ma dat cho, va dua link baggage info. | `evidence/screenshots/neo-08-trust-recovery.JPG` | Trust recovery | NEO co kha nang tao verification checklist khi duoc hoi truc tiep. To-be product nen dua checklist nay vao output mac dinh. |
| Prompt bonus: "Toi khong chac ve da bao gom hanh ly ky gui mien cuoc hay chua..." NEO chi yeu cau so ve hoac ma dat cho de ho tro tra cuu. | `evidence/screenshots/neo-09-entitlement-check.JPG` | Low-confidence / entitlement | NEO dung khi can booking data, nhung chua dua checklist tu kiem tra truoc khi user tra tien. Day noi truc tiep voi pain public ve mua/bi tinh tien dich vu co the da bao gom. |
| Prompt bonus: "Da mua hanh ly tra truoc roi nhung sau do doi ngay bay/doi chuyen bay..." NEO noi hanh ly tra truoc co the tiep tuc su dung neu doi voi chi phi ngang bang/cao hon va hoan tat it nhat 3 tieng truoc chang bay moi; sau do yeu cau so ve/ma dat cho. | `evidence/screenshots/neo-10-add-on-validity.JPG` | Add-on validity / correction | NEO dua dieu kien quan trong ve hieu luc sau thay doi booking. Prototype nen hien "hieu luc voi chuyen bay/ve da mua" va nhac kiem tra lai khi booking thay doi. |
| Prompt bonus: "Tui the thao qua kho..." NEO phan biet hanh ly tra truoc voi hanh ly dac biet/qua kich thuoc, nhac lien he chi nhanh it nhat 24 tieng truoc gio khoi hanh va fallback hanh ly tinh cuoc tai san bay. | `evidence/screenshots/neo-11-special-baggage.JPG` | Special baggage / route | NEO xu ly tot route dac biet. Prototype/backlog nen tach "hanh ly dac biet" ra khoi prepaid baggage checker va handoff som. |

## 3. User / review / social evidence

Nguon ngoai nhom duoi day khong dung de ket luan "NEO sai". Chung dung de chung minh user pain that quanh cac task co cung pattern: dich vu bo tro, dieu kien ve, app/website, hoan/doi/phi, va viec user can nguon xac minh truoc khi quyet dinh.

| Quote / review / observation | Nguon | User la ai? | Pain/failure mode |
|---|---|---|---|
| Review Trustpilot ve Vietnam Airlines co nhieu phan anh quanh refund/cancellation, app kem hieu qua, customer service va viec khong doi duoc seat/legroom nhu ky vong. | Trustpilot - Vietnam Airlines reviews | Hanh khach mua/quan ly ve va dich vu sau khi dat | User pain khong chi la "khong biet thong tin", ma la khong biet dieu kien nao ap dung va can kenh nao de xu ly khi co tien/dich vu lien quan. |
| Complaint tren BBB noi user bi tinh tien cho mot dich vu ma ho cho la da nam trong fare, do app interface thieu ro rang, sau do gap kho khi yeu cau refund. | Better Business Bureau - Vietnam Airlines complaints | Hanh khach da mua ve va dich vu lien quan hanh ly/add-on | Failure mode lien quan truc tiep den SPEC: UI/AI can lam ro entitlement vs paid add-on truoc khi user tra tien. |
| Thread Reddit ve excess baggage cho thay user quan tam viec biet truoc baggage rules va chi phi truoc khi ra san bay; mot comment noi nen check baggage rules truoc khi mua ve. | Reddit r/VietNam - Vietnam Airlines excess baggage discussion | Hanh khach co hanh ly qua kho/qua can | User can pre-check rule va cost truoc khi den san bay; day ung ho build slice "eligibility checker" thay vi FAQ chung. |
| Thread Reddit ve paid seat/add-on bi thay doi cho thay dich vu bo tro sau khi mua co the gay mat niem tin neu user khong ro dieu kien/refund/channel ho tro. | Reddit r/VietNam - paid seat selection discussion | Hanh khach da tra tien dich vu bo tro | Pattern ap dung cho hanh ly tra truoc: output can co source, dieu kien hieu luc, va fallback/handoff khi add-on khong nhu ky vong. |

## 3b. Official / policy evidence

| Observation | Nguon | Dung de lam gi trong SPEC? |
|---|---|---|
| Vietnam Airlines mo ta NEO la chatbot thong minh ho tro nguoi dung tim thong tin va giai dap thac mac nhanh. | Trang "Chat ngay cung NEO" cua Vietnam Airlines | Xac dinh promise cua product. |
| Dieu khoan NEO noi phan hoi duoc tao tu dong, co the khong chinh xac/khong day du; khuyen cao khong dua ra quyet dinh quan trong chi dua vao NEO. | Dieu khoan su dung Chatbot NEO | Xac dinh trust/safety requirement: thong tin quan trong phai co source va fallback. |
| Trang chinh sach hanh ly noi hanh ly tra truoc mua it nhat 3 tieng truoc gio khoi hanh; kien chuan toi da 23kg va 158cm; ap dung cho ve 738 do Vietnam Airlines/Pacific Airlines khai thac, tru ATR72. | Trang "Mua them hanh ly ky gui" cua Vietnam Airlines | Rule set cho prototype: deadline, can nang, kich thuoc, loai ve, hang khai thac, ngoai le. |

## 4. Competitor / analog evidence

| App / mo hinh tham khao | Ho xu ly task nay the nao? | Pattern hoc duoc | Co ap dung trong 1 ngay khong? |
|---|---|---|---|
| Checkout / service eligibility checker | Truoc khi cho mua dich vu, he thong hoi cac truong bat buoc va chi hien CTA khi eligible. | Eligibility checklist truoc khi ket luan. | Co. Prototype co form 4 truong: thoi gian con lai, so ve/PNR, hang khai thac, can nang/kich thuoc. |
| FAQ chatbot co citation | Cau tra loi quan trong kem source chip/link va "last checked". | Trust by default thay vi chi dua source khi user hoi. | Co. Them source card trong output. |
| Customer support triage | Case thieu thong tin thi hoi lai; case rui ro cao thi handoff hotline/email. | Low-confidence path va rescuer role. | Co. Them state "Can them thong tin" va "Lien he VNA". |

## 5. Evidence -> Insight

**Evidence noi bat nhat:**  
NEO tra loi tot khi cau hoi ro, nhung voi cau hoi thieu ngu canh ("khong nho mua qua kenh nao", "mua qua dai ly") NEO van co xu huong ket luan chac chan. Khi user hoi ve nguon hoac canh bao "NEO co the sai", NEO moi dua checklist/link xac minh. Voi prompt entitlement ("ve da bao gom hanh ly chua?"), NEO yeu cau PNR/so ve nhung chua dua duoc checklist tu kiem tra truoc khi tra tien. Voi add-on sau doi chuyen va tui the thao qua kho, NEO dua dieu kien/fallback huu ich; day la evidence cho viec prototype nen co route rieng cho "booking changed" va "special baggage".

**Insight:**  
Hanh khach khong chi can cau tra loi "co mua hanh ly tra truoc duoc khong". Ho can mot buoc xac minh dieu kien va entitlement truoc khi quyet dinh tra tien, vi task nay phu thuoc vao deadline 3 tieng, loai ve 738, hang khai thac, ngoai le ATR72, PNR/so ve, can nang/kich thuoc hanh ly, hanh ly mien cuoc da co trong ve, va viec booking/add-on co bi thay doi hay khong.

**Opportunity:**  
AI co the giup bang cach augment quyet dinh mua hanh ly: hoi lai cac thong tin thieu, check entitlement/eligibility, tao checklist hanh dong co source, va chuyen sang fallback an toan khi qua deadline, vuot chuan, hoac can booking lookup.

## 6. Evidence doi SPEC nhu the nao?

- [x] Doi user chinh.
- [x] Doi pain statement.
- [x] Doi build slice.
- [x] Doi Auto/Aug decision.
- [x] Doi 4 paths.
- [x] Doi failure mode.
- [x] Doi owner/test plan.

Truoc evidence, nhom co the build "chatbot hoi dap hanh ly".  
Sau evidence, nhom doi thanh "baggage eligibility checker co source va recovery path".  
Ly do: NEO da tra loi FAQ kha tot; gia tri moi nam o low-confidence path, trust-by-default va correction/failure handling.
