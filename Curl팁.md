
cURL 명령어 심층 가이드 🌐
cURL (Client URL)은 명령어 줄에서 **다양한 프로토콜(HTTP, HTTPS, FTP, SMTP 등)**을 사용하여 서버와 데이터를 주고받는 데 사용하는 강력한 도구입니다. 웹 개발에서 API 테스트 및 디버깅에 필수적으로 사용됩니다.
1. 기본 사용법 및 개념
curl 명령어는 기본적으로 해당 URL에 GET 요청을 보내고, 서버 응답(HTML, JSON, XML 등)을 터미널에 그대로 출력합니다.
기본 구문
curl [옵션...] <URL>

| 기능 | 명령어 예시 | 설명 |
|---|---|---|
| 기본 GET 요청 | curl https://www.google.com | 해당 URL의 소스 코드를 출력합니다. |
| 헤더만 확인 | curl -I https://www.google.com | 응답 본문 없이 HTTP 헤더 정보만 출력합니다. |
| 상세 정보 출력 | curl -v https://api.example.com | 요청/응답 헤더 및 전체 과정을 자세하게(Verbose) 출력합니다. |
2. API 테스트를 위한 주요 옵션
curl은 REST API의 GET, POST, PUT, DELETE 등 모든 HTTP 메서드를 테스트하는 데 사용됩니다.
HTTP 메서드 및 데이터 전송
| 옵션 | Long 형식 | 역할 | 예시 |
|---|---|---|---|
| -X | --request | HTTP 요청 메서드를 지정합니다. | curl -X POST ... |
| -H | --header | 요청 헤더를 추가합니다. (API 키, 데이터 타입 지정) | curl -H "Content-Type: application/json" ... |
| -d | --data | **POST/PUT 요청 시 보낼 데이터(Body)**를 지정합니다. | curl -d 'key=value' ... |
| -L | --location | 서버가 리다이렉션(3xx 응답)을 요청하면 자동으로 따라갑니다. | curl -L http://short.url |
| -k | --insecure | HTTPS 요청 시 SSL 인증서 유효성 검사를 무시하고 연결합니다. (테스트 환경) | curl -k https://test-server.com |
💡 JSON POST 요청 예시
JSON 데이터를 API 서버로 전송하는 가장 일반적인 형태입니다.
curl -X POST \
  -H "Content-Type: application/json" \
  -d '{"username": "user1", "action": "create"}' \
  https://api.example.com/items

3. 파일 다운로드 및 출력 제어
curl은 원격 서버의 파일을 다운로드하는 데도 사용됩니다.
| 옵션 | 설명 | 예시 |
|---|---|---|
| -o | 지정한 파일명으로 응답 내용을 저장합니다. | curl -o result.zip https://example.com/file.zip |
| -O | 원격 서버의 원본 파일명 그대로 저장합니다. | curl -O https://example.com/backup.sql |
| -s | --silent | 진행 상황 메시지를 출력하지 않고 조용히 실행합니다. (스크립트에 유용) |
| -w | --write-out | 요청 후 응답 코드 등 사용자 정의 정보를 출력합니다. |
