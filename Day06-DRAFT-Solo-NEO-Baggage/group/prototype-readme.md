# Prototype README

## Ten prototype

NEO Baggage Eligibility Checker

## Muc tieu

Prototype chung minh mot AI decision hep: dua vao thong tin hanh khach cung cap, AI ho tro check xem co nen mua hanh ly tra truoc online khong, can kiem tra them gi, va fallback nao an toan neu khong du dieu kien.

## Cach chay

Mo file:

```text
prototype/index.html
```

Khong can server. Prototype chay bang HTML/CSS/JavaScript tinh.

## Flow demo

1. Happy path: chon `Con hon 3 tieng`, `ve 738`, `Vietnam Airlines/Pacific Airlines`, `khong ATR72`, `23kg`, `158cm`.
2. Low-confidence path: bo trong mot vai truong nhu hang khai thac, thoi gian con lai, hoac hanh ly mien cuoc.
3. Failure path: chon `Duoi 3 tieng` hoac nhap `25kg`, `160cm`.
4. Correction path: sua input sau khi co ket qua va bam "Kiem tra lai"; xem correction log.

## AI behavior duoc mo phong

Prototype khong tra cuu booking that va khong thanh toan. AI behavior duoc mo phong bang rule + copy UX:

- Neu du thong tin va dat dieu kien: goi y mua hanh ly tra truoc neu hanh ly mien cuoc chua du.
- Neu thieu thong tin: hoi lai truoc khi ket luan.
- Neu qua deadline/vuot chuan: dua fallback an toan.
- Moi output quan trong deu co source card va checklist xac minh.

## Source

- Vietnam Airlines - Mua them hanh ly ky gui: https://www.vietnamairlines.com/vn/vi/travel-information/baggage/excess-baggage
- Vietnam Airlines - Dieu khoan su dung Chatbot NEO: https://www.vietnamairlines.com/vn/vi/support/condition-of-chatbot-NEO
- Vietnam Airlines - Chat ngay cung NEO: https://www.vietnamairlines.com/cn/vi/help-desk/other-topics/Chat-with-vna

## Gioi han

- Khong dung PNR/so ve that.
- Khong tinh phi theo tung chang bay.
- Khong tich hop he thong Vietnam Airlines.
- Khong xu ly sau add-on booking change bang booking that.
- Khong xu ly hanh ly dac biet/tui the thao qua kho nhu flow chinh; chi handoff.
- Khong thay the thong tin chinh thuc; output luon yeu cau user xac minh tren website/app Vietnam Airlines.
