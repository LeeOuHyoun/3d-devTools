# 실제 MQL 서버에서 확인할 항목

3d-mql-console, 3d-mql-graph 의 코드 검토에서 실제 MQL 환경에서 확인해야 결정할 수 있는 항목만 모았습니다.

## 공통 (확인 결과를 두 확장에 같이 적용)

| 확인할 것 | 결정할 것 |
|---|---|
| `chcp 949` PC에서 한글 description 을 수정하고 다시 읽으면 깨지는가 | 깨지면 `chcp 65001`·`MX_CHARSET` 으로 UTF-8 통일이 되는지 먼저 확인하고, 안 되면 `iconv-lite` 도입 |
| `password` 를 어디까지 줄여 쓸 수 있는가 (`p`, `pa`, `pas`, `pass`) | 비밀번호 가림의 최소 접두어 |
| `context` 를 어디까지 줄여 쓸 수 있는가 (`con`, `cont`) | context 변경 감지 패턴 범위 |
| 세션 기본 `escape` 값, 따옴표 안 `\` 처리 | 토크나이저 `\` 규칙 통일 |

## 3d-mql-console

| 확인할 것 | 결정할 것 |
|---|---|
| `set` 하위 명령 중 `print context;` 결과를 바꾸는 다른 명령이 있는가 | context 변경 감지에서 `set` 범위 축소 |
| `eval expr "<token>";` 이 대상 객체 없이 단독 실행되는가 | 응답 완료 마커 대체 가능 여부 |
| `print policy` 의 `allstate` 트리거 출력 형식 | 파서 수정 |
| `mod relationship` 에서 `all` 과 개별 `type` add/remove 의 순서 제약 | 구문 생성 순서 |

## 3d-mql-graph

| 확인할 것 | 결정할 것 |
|---|---|
| `start trans;`·`commit trans;` 축약형과 `update` 등 모드 단어를 받는가 | 트랜잭션 감지 패턴 |
| 트랜잭션 안에서 문장·commit 이 실패한 뒤에도 트랜잭션이 열려 있는가, 상태를 묻는 명령이 있는가 | 실패 시 TX 표시·바구니 commit 실패 처리 (자동 abort 여부) |
| 오류가 stderr 로 나오는가, stdout 과 순서가 뒤바뀌는가 | 출력 수신 구조 설계 |
| 줄 중간 `#`, 여러 줄 따옴표 안 `#` 줄을 주석으로 보는가 | 주석 처리 규칙 |
| `print bus … select … dump <구분자>` 에서 여러 줄 값·다중 값 속성의 출력 형태 | dump 한 번으로 원문 값 읽기 |
| 같은 두 객체 사이 같은 관계가 여러 개일 때 `disconnect` 가 어느 것을 끊는가 | 되돌리기를 `delete connection <id>` 기준으로 바꿀지 |

## 서버 확인과 별개로 정할 것

- 3d-mql-graph: 패널을 닫았다 다시 열 때 콘솔 기록을 복원할지
