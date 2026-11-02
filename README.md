# prompt_engineering_practice

Hands-on LLM helpdesk (DevDesk) for internal developer questions: prompt design, JSON schema validation, function calling, retries, and token cost estimation.

사내 개발자 문의에 답하는 LLM 헬프데스크(DevDesk) 실습입니다. 사내 문서와 티켓을 근거로 개발환경 설치, 저장소 접근, 장애 문의에 답하는 프로그램을 단계별로 만듭니다.

## 배우는 내용

| 단계 | 함수 | 주제 |
|---|---|---|
| 정책 프롬프트 | `build_instructions` | 시스템 프롬프트 설계, Few-shot 예시, Reasoning 체크리스트 |
| 답변 검증과 수정 | `answer_format`, `validate_answer`, `finish_answer` | Structured Output(JSON Schema), 출처 검증, 1회 수정 요청 |
| 티켓 조회 | `tool_schema`, `execute_tool`, `tool_roundtrip` | Function Calling, call_id 매칭 |
| 오류 화면 입력 | `image_content` | 멀티모달(텍스트 + 이미지) 입력 |
| 호출 재시도 | `call_with_retry` | 재시도 가능한 오류 판별, 지수 백오프 |
| 사용량과 비용 | `cache_settings`, `usage_record` | 프롬프트 캐싱, 토큰 비용 계산 |
| 전체 연결 | `run_pipeline` | 위 기능을 하나의 흐름으로 연결 |

## 파일 구성

```text
main.py             구현 코드
main_explained.py   main.py 를 한 줄씩 해설한 공부용 사본
GUIDE.md            설치, 실행, 확인 방법 안내
ASSIGNMENT.md       문제와 기능별 요구사항
support.py          실행, 저장 도우미
checks.py           기능별 검사
data/               문서, 티켓, 질문 사례, 오류 화면, 가격표
artifacts/          실행 결과
```

## 실행

[uv](https://docs.astral.sh/uv/)와 Python 3.12가 필요합니다.

```bash
uv sync --frozen
uv run --frozen python main.py demo           # 환경 확인 (API 키 불필요)
uv run --frozen python main.py check policy   # 기능별 검사
uv run --frozen python main.py run policy     # 준비된 응답으로 실행
```

실제 API 호출은 `.env.example`을 `.env`로 복사해 `OPENAI_API_KEY`를 넣은 뒤 `--live`를 붙여 실행합니다. 자세한 내용은 [GUIDE.md](GUIDE.md)를 참고하세요.
