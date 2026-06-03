# Demo script

## 0:00 - Hook

"NEO tra loi kha tot khi cau hoi ro. Nhung khi hanh khach hoi ve hanh ly tra truoc, rui ro khong nam o viec bot co biet FAQ hay khong. Rui ro nam o viec user thieu thong tin nhung van nhan duoc mot cau tra loi qua chac."

## 0:30 - Evidence

"Em test 11 prompt voi NEO. Happy path cho thay NEO tra loi duoc cach mua, deadline 3 tieng, phi, 23kg/158cm. Nhung voi prompt 'khong nho mua qua website/app hay dai ly', NEO khang dinh van co the tu mua online thay vi hoi lai. Voi prompt 've da bao gom hanh ly mien cuoc chua', NEO chi yeu cau so ve/ma dat cho, trong khi user can checklist tu kiem tra truoc khi tra tien. Prompt ve doi chuyen bay va tui the thao qua kho cho thay co hai route can handoff/backlog. Khi em hoi nguon, NEO moi dua link chinh sach. Dieu nay dan toi opportunity: source va checklist nen hien mac dinh."

## 1:15 - Insight

"User khong chi can cau tra loi 'co mua hanh ly duoc khong'. Ho can mot eligibility check truoc khi tra tien: con bao lau truoc gio bay, ve co phai 738 khong, hang khai thac nao, co phai ATR72 khong, hanh ly co vuot 23kg/158cm khong."

## 1:45 - Prototype

"Prototype cua em la NEO Baggage Eligibility Checker. No khong thay the Vietnam Airlines, ma augment quyet dinh cua user bang checklist co source."

Demo:

1. Nhap case happy: con hon 3 tieng, ve 738, Vietnam Airlines/Pacific Airlines, khong ATR72, 20kg/150cm.
2. Show output: co the mua hanh ly tra truoc, buoc tiep theo, source card.
3. Xoa mot truong: hang khai thac unknown.
4. Show low-confidence: khong ket luan, hoi lai.
5. Nhap failure: khoi hanh sau 2 tieng hoac vali 25kg/160cm.
6. Show fallback: khong mua hanh ly tra truoc online, ra san bay mua hanh ly tinh cuoc / chia hanh ly / xac minh nguon.
7. Sua input va show correction log.

## 3:30 - Failure handling

"Failure mode nguy hiem nhat la AI tra loi qua chac khi user thieu dieu kien. Prototype xu ly bang 3 lop: ask again, source card, fallback. Human role la decider va rescuer: user quyet cuoi, Vietnam Airlines support can thiep khi booking/eligibility khong ro."

## 4:15 - Learning signal

"Prototype log correction: user sua thoi gian, can nang, kich thuoc, kenh mua. Nhung signal nay co the bien thanh eval set cho lan sau: input nao hay thieu, case nao hay bi handoff, source nao hay duoc bam."

## 4:45 - Close

"Day khong phai chatbot hanh ly moi. Day la mot lat cat nho cho thay AI product can thiet ke cho uncertainty: khi dung thi nhanh, khi thieu thong tin thi hoi lai, khi sai/khong du dieu kien thi recover an toan."
