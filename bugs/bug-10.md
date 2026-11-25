# BUG-10: Буруу JSON биеттэй POST хүсэлтэд амжилттай статус буцааж байна

**Орчин:** Уншлагын жагсаалт v2.0, Windows PowerShell 5.1, Node.js v24.22.1, `curl.exe`, 2026-11-26. API шалгалтад browser ашиглаагүй.

**Урьдчилсан нөхцөл:** Апп `http://localhost:3000` дээр ажиллаж байна. `evidence/request-10.json` файлд синтаксийн хувьд буруу JSON (`{"title":`) байна.

## Дахин гаргах алхам

1. PowerShell дээр төслийн хавтас руу орно.
2. Дараах хүсэлтийг илгээнэ:

   ```powershell
   curl.exe --silent --show-error -i -X POST "http://localhost:3000/api/books" -H "Content-Type: application/json" --data-binary "@evidence/request-10.json"
   ```

**Хүлээгдэж байсан:** Даалгаврын API шаардлагын дагуу буруу JSON биеттэй POST хүсэлт `HTTP 400 Bad Request` буцаана.

**Бодит үр дүн:** `HTTP 200 OK` болон `{"result":"OK"}` буцсан.

**Ноцтой байдал:** Major — буруу хүсэлтийг сервер амжилттай мэт мэдээлж, клиент алдааг зөв таних боломжгүй болгож байна.

**Хавсралт:** `../evidence/bug-10-curl.txt`; хүсэлтийн бие: `../evidence/request-10.json`

**Олдсон аялал:** Saboteur (API)
