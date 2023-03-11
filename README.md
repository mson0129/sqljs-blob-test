# SQL.js BLOB Test
Body Element 안에 파일을 드랍할 경우, 파일의 바이너리 데이터를 SQL.js를 통해 인메모리 DB에 저장합니다.\
인메모리 DB에 저장된 파일을 다운로드할 수 있습니다.\
인메모리 DB는 SQLite 파일 형식으로 다운로드할 수 있습니다.

## 고려사항

### SQL.js에서 JavaScript와 SQLite 타입 간의 대응

SQL.js에서 JavaScript와 SQLite 타입은 다음과 같이 대응합니다.

| JavaScript 타입 | SQLite 타입 |
| -------------- | ---------- |
| number | Integer, Real |
| boolean | Integer |
| string | Text |
| Array, UInt8Array | BLOB |
| null | Null |

출처: https://sql.js.org/documentation/Statement.html

상기 대응표에 따라 Body Element 안에 파일을 드랍할 경우,
드랍한 파일의 내용이 담긴 ArrayBuffer로 UInt8Array를 생성하여 DB에 삽입(Insert)합니다.

## 참고(References)

### 예제 코드(Articles)

* [SQL.js](https://sql.js.org/)
  * SQL.js의 공식 사이트입니다.

* [How to get the filename from the Javascript FileReader?](https://stackoverflow.com/questions/24245105/how-to-get-the-filename-from-the-javascript-filereader)
  * FileReader의 onLoad 이벤트 핸들러로 파일 이름 값을 넘기기 위한 트릭입니다.

### 개발자 문서(Developer Documents)

* [SQL.js API](https://sql.js.org/documentation/)
