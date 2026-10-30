# Codex 사전 환경 점검 프롬프트

공개 스킬의 설치·인식과 최소 동작을 확인하는 15분 사전 체험용 프롬프트다. 과제의 문제·답안·데이터, 공식 PDF 원문, 개인 PC의 경로·인증 정보는 포함하지 않는다.

사용할 플랫폼이 이 문서의 반입과 공개 스킬 설치를 허용하는지 먼저 확인한다. 이 문서를 공개했다는 사실이 특정 대회에서의 사용 허가를 의미하지 않는다. 실제 응시 안내와 운영진의 안내가 항상 우선한다.

## 사용 방법

제공된 Codex에서 이 문서의 전문을 읽도록 한 뒤 아래 프롬프트의 점검 절차를 실행하도록 요청한다. 문서가 길어 도구 출력이 잘리면 구간을 나누어 끝까지 읽는다. 플랫폼의 브라우저나 감독 장치는 사람이 직접 확인한다.

Codex 작업은 최대 9분을 목표로 하며 남은 시간은 화면 동작·감독 연결·종료 절차를 확인하는 데 사용한다. 설치가 오래 걸리면 실패 사유를 남기고 기본 점검을 계속한다.

## 실행할 프롬프트

```text
지금은 15분 사전 체험의 환경 점검이다.
아래 작업을 실제 수행해줘. 계획 설명으로 끝내지 마.
지금부터 최대 9분을 목표로 하고, 시간이 부족하면 설치보다
파일 저장·서버 실행·결과 기록을 우선해줘.

[작업 범위]
- 현재 프로젝트의 README와 제공된 응시 안내를 먼저 읽고 우선 적용해줘.
- 개인 PC 파일·PDF·API 키를 요구하지 말고 제공된 Codex만 사용해줘.
- 공개 자료는 현재 환경 안에서 가져오고 문제·파일·결과물은 외부에 전송하지 마.
- Git Push, 외부 계정 연결, 감독·보안 설정 변경은 하지 마.
- 이번 점검에서는 브라우저 자동 조작·자동 클릭·캡처·녹화를 하지 마.
- webapp-testing의 Playwright 자동 실행 허용 여부는 별도로 확인해야 한다.
  스킬 설치·파일·의존성만 확인하고 자동 브라우저 테스트는 보류해줘.
- 카메라·휴대폰·전체 화면 공유·화면 버튼은 내가 직접 확인한다.
- 기존 파일을 보존하고 체험용 파일은 preflight-check/ 아래에 작성해줘.
- 실제 남은 체험 시간이 이 계획보다 짧다면 남은 시간을 우선해줘.

1. 환경과 기존 설치 확인
OS·셸·작업 경로, Codex·Node·npm/npx·Git·Python 버전을 확인해줘.
설치된 플러그인과 스킬도 확인하고 이미 같은 출처가 있으면 중복 설치하지 마.
Windows PowerShell에서는 아래 npx 명령을 npx.cmd로 실행해줘.
제공된 Codex 자체는 재설치·업그레이드하지 마.

2. 없는 스킬 설치
설치 단계 전체는 약 3분으로 제한하고 네트워크 명령은 가능하면 60초 제한을 적용해줘.
오류가 나면 원인을 기록하고 다른 항목을 계속해줘. 반복 재시도는 하지 마.

Matt Pocock 전체는 plugin 명령이 지원될 때 다음으로 설치해줘.
  codex plugin marketplace add mattpocock/skills
  codex plugin add mattpocock-skills@mattpocock

Engineering은 코드 리뷰·문서화 두 스킬만 전역 설치해줘.
  npx --yes skills@latest add anthropics/knowledge-work-plugins --skill code-review documentation -a codex -g -y

webapp-testing 스킬 파일도 전역 설치해줘.
  npx --yes skills@latest add anthropics/skills --skill webapp-testing -a codex -g -y

종료 코드와 개별 실패를 확인해줘. 성공 문구만 보고 설치 성공으로 판단하지 마.
권한·버전·네트워크·plugin 미지원 문제는 기록하고 제한 우회 없이 다음으로 넘어가.
플러그인 설치에는 -g를 붙이지 마. -g는 위 skills add 명령의 전역 설치 옵션이다.

3. 설치와 인식 확인
각 스킬의 실제 SKILL.md 경로·출처·호출명을 확인해줘.
플러그인 설치는 codex plugin list로, 개별 설치는 skills list로 나누어 확인해줘.
Matt는 설치 버전의 manifest에 선언된 전체 활성 스킬의 파일 존재와 현재 인식을
대조하고 목록을 기록해줘. 전체 스킬을 전부 실행하지는 마.
새 세션이 필요하면 현재 세션을 스스로 종료하지 말고 설치된 SKILL.md를 직접 읽어
아래 과제에 적용해줘. 이때 “지침 직접 적용”과 “현재 세션 자동 인식”을 구분해줘.
자동 인식을 확인하지 못했다면 미확인으로 기록해줘.

4. Matt grilling 동작 확인
실제 grilling 지침을 읽고 “팀원이 남은 업무를 확인하는 작은 도구” 기획에 대해
질문 1개와 추천 답변 1개를 작성해줘.
이번은 동작 확인이므로 내 답을 기다리지 말고 다음 검증으로 진행해줘.
기획 합의가 완료됐다고 기록하지 마.

5. Engineering 코드 리뷰 확인
preflight-check/average.mjs에 다음 함수를 작성해줘.
  export function average(xs) { return xs.reduce((a, b) => a + b) / (xs.length - 1); }

요구사항은 “유한한 숫자 배열의 산술평균 반환, 빈 배열은 null 반환”이다.
Engineering 출처 code-review 지침으로 오류·줄 번호·재현 입력·수정 방향을 보고해줘.
Matt의 code-review는 사용하지 마.
Node로 재현 입력의 실제 결과도 확인하되 검토 대상 함수는 수정하지 마.

6. 서버 실행과 Engineering 문서화 확인
제공된 실행 예제가 있으면 활용해줘. 없으면 외부 패키지 없이 실행되는 작은
Node HTTP 서버와 숫자 증가 버튼을 preflight-check/ 안에 만들어줘.
서버는 0.0.0.0에 바인딩하고 실제 포트와 / 경로를 알려줘.
HTTP 요청으로 응답을 확인하고 서버는 내가 화면을 확인하도록 유지해줘.

Engineering documentation 지침으로 preflight-check/README.md에
필요 버전·작업 위치·실행 명령·실제 포트·버튼 사용법·예상 결과·종료법을 작성해줘.
확인 문구 파일도 쓰고 다시 읽어 파일 생성·저장을 검증해줘.
스킬 지침을 불러오지 못해 기본 Codex로 대신 수행했다면 스킬 성공으로 기록하지 마.

7. webapp-testing 설치 상태 확인
SKILL.md와 scripts/with_server.py 등 보조 파일 존재,
Python·Playwright 패키지·Chromium 바이너리 설치 여부를 각각 확인해줘.
--help 같은 비브라우저 확인만 수행하고 브라우저는 실행하지 마.
누락된 의존성은 기록하고 이번 점검에서는 Chromium을 새로 다운로드하지 마.
import·파일 존재 확인을 실제 브라우저 실행 성공으로 기록하지 마.

8. 결과 기록과 직접 확인 안내
진행할 때마다 preflight-check/RESULT.md에 짧게 저장해줘.
항목별 출처·설치/버전·현재 인식·실행 결과·오류·근거를 기록하고
통과/실패/부분 확인/미실행/보류를 구분해줘.
Matt 전체 목록 확인과 grilling 대표 실행을 구분해줘.

마지막 답변은 10줄 이내로 실제 포트·경로·보고서 위치·실패 항목을 먼저 알려주고,
내가 직접 할 다음 행동을 안내해줘.
① 플랫폼이 요구하는 감독 장치·카메라 구도·전체 화면 공유·충전 확인
② 내장 Browser에 실제 포트와 / 입력 → 버튼 직접 클릭 → 숫자 증가 확인
③ 에디터에서 문구 수정·저장 → 파일 재열기·화면 갱신 확인
④ 플랫폼 도우미·문제 신고 위치 확인
⑤ 체험 종료 → 예시 후속 문항 → 완료 흐름 확인

직접 확인 항목은 내가 수행했다고 추정하지 마.
체험 종료·제출·본 과제 시작 버튼은 내가 직접 누른다.
```

## 판정할 때 구분할 것

- **설치:** 실제 파일과 설치 결과를 확인한다.
- **인식:** 현재 Codex 세션이 사용할 수 있는지 확인한다. 파일을 직접 읽어 적용한 결과와 구분한다.
- **동작:** 실제 요청·코드 실행·생성 파일과 결과를 확인한다.
- **사용 허용:** 설치와 동작 성공만으로 대회나 플랫폼의 사용 허가를 추정하지 않는다.
- Matt 전체 스킬의 파일 목록 확인은 전체 스킬의 실행 성공을 뜻하지 않는다.
- `webapp-testing`은 자동 브라우저 실행을 하지 않으므로 이번 점검으로 E2E 실행 성공을 확인할 수 없다.

## 공개 원본

- [Matt Pocock 스킬과 설치 안내](https://github.com/mattpocock/skills)
- [Engineering 코드 리뷰](https://github.com/anthropics/knowledge-work-plugins/blob/main/engineering/skills/code-review/SKILL.md)
- [Engineering 문서화](https://github.com/anthropics/knowledge-work-plugins/blob/main/engineering/skills/documentation/SKILL.md)
- [webapp-testing](https://github.com/anthropics/skills/blob/main/skills/webapp-testing/SKILL.md)
- [skills CLI 옵션](https://github.com/vercel-labs/skills/blob/main/docs/commands.md)

설치 명령과 지원 범위는 원본 버전 및 실행 환경에 따라 달라질 수 있다. 실행 환경의 실제 도움말과 오류를 기준으로 판단한다.
