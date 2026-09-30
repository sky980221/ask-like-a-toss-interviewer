# Claude Code 사용 가이드

이 저장소의 `SKILL.md`는 Agent Skills 형식을 사용하므로 Codex와 Claude Code에서 같은 면접 지침을 사용할 수 있습니다. 별도의 Claude 전용 스킬 사본을 두지 않아 두 환경의 내용이 서로 달라지는 것을 방지합니다.

## 방법 1: 개인 스킬로 설치

모든 로컬 프로젝트에서 사용하려면 저장소를 복제한 뒤 스킬 디렉터리를 `~/.claude/skills/`에 복사합니다.

```bash
git clone https://github.com/sky980221/ask-like-a-toss-interviewer.git
mkdir -p ~/.claude/skills
cp -R ask-like-a-toss-interviewer/skills/ask-like-a-toss-interviewer ~/.claude/skills/
```

Claude Code를 새로 시작한 뒤 다음과 같이 호출합니다.

```text
/ask-like-a-toss-interviewer
```

이 방식은 명령 이름이 짧고 모든 프로젝트에서 사용할 수 있어 개인 사용에 가장 적합합니다.

## 방법 2: 특정 프로젝트에 설치

팀과 함께 사용하는 프로젝트라면 해당 프로젝트의 `.claude/skills/` 아래에 스킬을 복사하고 커밋할 수 있습니다.

```bash
mkdir -p .claude/skills
cp -R /path/to/ask-like-a-toss-interviewer/skills/ask-like-a-toss-interviewer .claude/skills/
```

해당 프로젝트에서 시작한 Claude Code 세션은 스킬을 `/ask-like-a-toss-interviewer`로 사용할 수 있습니다.

## 방법 3: 플러그인으로 설치

이 저장소는 Claude Code용 `.claude-plugin/plugin.json`과 마켓플레이스 목록을 포함합니다.

```bash
claude plugin marketplace add sky980221/ask-like-a-toss-interviewer
claude plugin install ask-like-a-toss-interviewer@ask-like-a-toss-interviewer-marketplace
```

플러그인으로 설치한 스킬은 플러그인 이름이 붙은 다음 명령으로 호출합니다.

```text
/ask-like-a-toss-interviewer:ask-like-a-toss-interviewer
```

설치 상태는 다음 명령으로 확인할 수 있습니다.

```bash
claude plugin list
claude plugin details ask-like-a-toss-interviewer
```

## 면접 시작 예시

### 입력 자료부터 선택

```text
/ask-like-a-toss-interviewer
```

입력이 없으면 스킬은 현재 작업 공간을 임의로 읽지 않고, 기술 주제·포트폴리오·레포지토리 중 무엇으로 진행할지 먼저 묻습니다.

### 현재 레포지토리 기반

```text
/ask-like-a-toss-interviewer 현재 레포지토리의 주문·결제 모듈을 기반으로 직무 인터뷰를 진행해줘.
```

레포지토리 기반 모드에서는 코드나 설정을 수정하지 않고 읽기 전용으로 탐색한 뒤, 파일과 심볼을 근거로 한 번에 하나씩 질문합니다.

### 포트폴리오 기반

```text
/ask-like-a-toss-interviewer 첨부한 포트폴리오를 기반으로 사전 인터뷰를 진행해줘.
```

### 학습 주제 기반

```text
/ask-like-a-toss-interviewer Kafka의 전달 보장을 공부했어. 이 주제로 직무 인터뷰를 진행해줘.
```

## 업데이트

개인 또는 프로젝트 스킬로 복사해 설치했다면 저장소를 업데이트한 뒤 스킬 디렉터리를 다시 복사합니다. 기존 파일을 덮어쓰기 전에 로컬에서 수정한 내용이 없는지 확인하세요.

플러그인으로 설치했다면 마켓플레이스와 플러그인을 업데이트합니다.

```bash
claude plugin marketplace update ask-like-a-toss-interviewer-marketplace
claude plugin update ask-like-a-toss-interviewer@ask-like-a-toss-interviewer-marketplace
```

## 문제 해결

- 명령이 보이지 않으면 Claude Code를 새로 시작하고 `/skills`에서 설치 여부를 확인합니다.
- 개인 스킬은 `~/.claude/skills/ask-like-a-toss-interviewer/SKILL.md` 경로에 파일이 있는지 확인합니다.
- 프로젝트 스킬은 프로젝트 루트의 `.claude/skills/ask-like-a-toss-interviewer/SKILL.md` 경로를 확인합니다.
- 같은 이름의 개인 스킬과 프로젝트 스킬이 함께 있으면 개인 스킬이 우선합니다.
- 플러그인 설치를 시험할 때는 저장소 루트에서 `claude plugin validate .`을 실행할 수 있습니다.

## 호출 방식 차이

| 환경 | 개인 스킬 호출 | 플러그인 호출 |
| --- | --- | --- |
| Codex | `$ask-like-a-toss-interviewer` | 설치 방식에 따라 다름 |
| Claude Code | `/ask-like-a-toss-interviewer` | `/ask-like-a-toss-interviewer:ask-like-a-toss-interviewer` |

Claude Code는 스킬 설명이 현재 요청과 일치하면 자동으로 불러올 수도 있습니다. 면접을 확실하게 시작하려면 위 명령으로 직접 호출하세요.

## 공식 문서

- [Claude Code Skills](https://code.claude.com/docs/en/skills)
- [Claude Code Plugins](https://code.claude.com/docs/en/plugins)
- [Claude Code Plugin Marketplaces](https://code.claude.com/docs/en/plugin-marketplaces)
