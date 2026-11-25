# BUG-12: JSON массивыг номын объект мэт амжилттай үүсгэж байна

**Орчин:** Уншлагын жагсаалт v2.0, Windows PowerShell 5.1, Node.js v24.22.1, `curl.exe`, 2026-11-26. API шалгалтад browser ашиглаагүй.

**Урьдчилсан нөхцөл:** Апп `http://localhost:3000` дээр ажиллаж байна. `evidence/request-12.json` файлд `[]` байна.

## Дахин гаргах алхам

1. PowerShell дээр төслийн хавтас руу орно.
2. Дараах хүсэлтийг илгээнэ:

   ```powershell
   curl.exe --silent --show-error -i -X POST "http://localhost:3000/api/books" -H "Content-Type: application/json" --data-binary "@evidence/request-12.json"
   ```

**Хүлээгдэж байсан:** Номын шаардлагатай талбаруудгүй массивыг номын объект гэж үзэхгүй, хүсэлт татгалзагдана.

**Бодит үр дүн:** `HTTP 201 Created` болон `{"result":"OK","id":22}` буцсан.

**Ноцтой байдал:** Major — номын шаардлага хангахгүй хүсэлтэд үүсгэлт амжилттай болсон гэж хариулж байна.

**Хавсралт:** `../evidence/bug-12-curl.txt`; хүсэлтийн бие: `../evidence/request-12.json`

**Олдсон аялал:** Saboteur (API)
