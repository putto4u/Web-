**curl**은 **클라이언트 URL(Client URL)**의 약자로, 커맨드 라인에서 **다양한 프로토콜(HTTP, HTTPS, FTP 등)**을 이용해 데이터를 전송하거나 수신할 수 있게 해주는 강력한 도구입니다. 웹 서버에 요청을 보내고 응답을 확인하거나, 파일을 다운로드하거나, API를 테스트할 때 주로 사용됩니다.
📝 curl 기본 사용법 및 예시
curl 명령어의 기본 구문은 curl [옵션...] <URL>입니다. 옵션을 지정하지 않으면 기본적으로 해당 URL에 대한 GET 요청을 보냅니다.
1. 웹 페이지 내용 가져오기 (GET 요청)
가장 기본적인 사용법으로, 해당 URL의 HTML 소스 코드를 터미널에 출력합니다.
curl https://www.google.com

2. 응답 헤더 확인
요청/응답의 HTTP 헤더 정보만 출력하고 본문(Body)은 표시하지 않을 때 사용합니다.
curl -I https://www.google.com
# 또는 --head

3. 파일 다운로드
원격 서버에 있는 파일을 로컬에 저장할 때 사용합니다.
 * -O (대문자 O): 원본 파일 이름 그대로 저장합니다.
   curl -O https://example.com/image.jpg 
# 로컬에 image.jpg 파일로 저장됨

 * -o (소문자 o): 저장할 파일 이름을 지정합니다.
   curl -o local_name.jpg https://example.com/image.jpg

🛠️ 주요 옵션 (API 테스트용)
curl은 특히 REST API를 테스트할 때 유용하며, 이때는 HTTP 메서드, 헤더, 데이터 등을 지정하는 옵션을 많이 사용합니다.
| 옵션 | Long 형식 | 설명 | 예시 |
|---|---|---|---|
| -X | --request | 사용할 HTTP 메서드를 지정합니다. (GET, POST, PUT, DELETE 등) | curl -X POST ... |
| -H | --header | HTTP 요청 헤더를 추가로 지정합니다. (JSON 타입 지정, 인증 토큰 전달 등에 사용) | curl -H "Content-Type: application/json" ... |
| -d | --data | **POST/PUT 요청 시 보낼 데이터(본문/Body)**를 지정합니다. | curl -d '{"key": "value"}' ... |
| -L | --location | 서버가 리다이렉션(Redirection, 3xx 응답)을 요청할 경우, 자동으로 따라가게 합니다. | curl -L http://short.url |
| -v | --verbose | 요청 및 응답 과정을 상세하게 출력하여 디버깅에 유용합니다. | curl -v https://example.com |
| -k | --insecure | HTTPS 요청 시 SSL 인증서 유효성 검사를 무시하고 연결합니다. (테스트 환경에서 유용) | curl -k https://test-server.com |
POST 요청 (JSON 데이터 전송) 예시
curl -X POST \
  -H "Content-Type: application/json" \
  -d '{"name": "Gemini", "role": "AI Assistant"}' \
  https://api.example.com/users

이 명령어는 Content-Type: application/json 헤더를 포함하고, JSON 형식의 데이터를 본문에 담아 지정된 URL에 POST 요청을 보냅니다.
