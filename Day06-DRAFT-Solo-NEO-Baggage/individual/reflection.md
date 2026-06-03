# Individual reflection

**Hoc vien:** Nguyễn Bách Điệp  
**ID hoc vien:** 2A202600535

## Vai tro ca nhan

Em lam mot minh, nen phu trach toan bo cac vai tro:

- Research: chat voi NEO, chup screenshot, doc chinh sach Vietnam Airlines.
- SPEC: chot user, pain, build slice, auto/aug decision va 4 paths.
- Prototype: thiet ke flow eligibility checker.
- Test: tao prompt tests va failure log.
- Demo/repo: viet demo script va sap xep artifact.

## Viec da lam

Em da test NEO bang 11 prompt quanh task mua hanh ly tra truoc:

- Happy path: hoi cach mua hanh ly tra truoc.
- Low-confidence: khong nho mua ve qua kenh nao.
- Safe boundary: khong co ma dat cho, hoi tra cuu bang ten/so dien thoai.
- Correction: sua thanh ve mua qua dai ly.
- Trust/source: yeu cau link chinh sach.
- Failure: chuyen bay khoi hanh sau 2 tieng.
- Constraint: vali 25kg/160cm.
- Trust recovery: hoi NEO can tu kiem tra thong tin nao vi NEO co the sai.
- Entitlement: hoi ve da bao gom hanh ly mien cuoc chua de tranh mua thua add-on.
- Add-on validity: hoi hanh ly tra truoc co con hieu luc khi doi ngay/chuyen bay khong.
- Special baggage: hoi tui the thao qua kho co dung prepaid baggage thuong khong.

## AI da ho tro gi

AI ho tro em:

- Bien transcript/screenshot thanh evidence pack.
- Nhom evidence thanh insight va opportunity.
- Chot build slice nho hon thay vi build chatbot travel rong.
- Viet thin SPEC, failure log, demo script va prototype.
- De xuat failure path va correction path theo framework Day 05.

## Quyet dinh product quan trong

Em khong build "AI assistant cho travel". Em cat scope thanh "baggage eligibility checker" cho mot task hep: hanh khach da mua ve muon mua them hanh ly tra truoc.

Quyet dinh auto/aug: chon augmentation. AI chi ho tro check dieu kien va dua checklist, user van quyet cuoi. Ly do la task lien quan chi phi, deadline va dieu kien ve; sai co the gay thiet hai thuc te.

## Bai hoc

Bai hoc lon nhat la AI product khong chi can tra loi dung o happy path. NEO tra loi kha tot khi cau hoi ro, nhung low-confidence path moi la noi can thiet ke product: thieu thong tin thi hoi lai, thong tin quan trong thi hien source, case khong du dieu kien thi co fallback.

## Neu co them thoi gian

- Test voi booking gia lap/PNR demo neu Vietnam Airlines co sandbox.
- Lay them 10-20 review/social comments ve hanh ly/phi san bay.
- Them source click tracking va correction analytics vao prototype.
- Mo rong sang doi/hoan ve, nhung van giu tung task hep rieng.
