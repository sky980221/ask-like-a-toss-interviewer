# Ask Like a Toss Interviewer

레포지토리, 포트폴리오 또는 학습 주제를 바탕으로 한국어 서버 개발자 모의면접을 진행하는 Codex·Claude Code Skill입니다.

> [!IMPORTANT]
> 이 프로젝트는 토스와 관련 없는 비공식 개인 프로젝트입니다. 실제 면접 질문, 유출 자료 또는 내부 평가 기준을 포함하지 않으며, 토스의 채용 절차를 재현하거나 대변하지 않습니다.

## 만든 이유

최근 토스 서버 개발자 면접에서 떨어졌습니다.

면접을 복기하면서 기술의 이름이나 정의를 아는 것과, 실제 문제에서 왜 그 기술을 선택했는지 설명하는 것은 전혀 다른 일이라는 걸 느꼈습니다. 선택의 근거뿐 아니라 내부 동작, 실패 상황, 다중 인스턴스 환경, 데이터 정합성과 운영까지 이어지는 질문에 흔들리지 않으려면 반복해서 사고하고 말하는 연습이 필요했습니다.

다시는 같은 실수를 반복하지 않기 위해 이 스킬을 만들었습니다. 정답을 외우는 대신 자신의 프로젝트와 코드를 근거로 판단을 설명하고, 꼬리질문을 통해 이해의 빈틈을 발견하는 것이 목적입니다.

## 면접 모드

### 레포지토리 기반

실제 코드, 설정과 테스트를 살펴본 뒤 설계 판단이 드러나는 파일과 심볼을 근거로 질문합니다. 구현 의도에서 시작해 대안, 내부 동작, 실패 조건, 확장, 테스트와 운영으로 깊이를 확장합니다.

### 자료 기반

포트폴리오, 이력서와 채용 공고에 적힌 프로젝트 경험과 기술적 주장을 중심으로 질문합니다. 수행하지 않은 경험을 임의로 가정하지 않습니다.

### 학습 주제 기반

현재 공부 중인 기술 주제에서 시작해 개념, 선택 기준, 반례, 장애 상황과 실제 시스템 적용으로 꼬리질문을 이어갑니다.

입력 없이 스킬만 호출하면 현재 작업 공간을 임의로 면접 대상으로 삼지 않습니다. 먼저 기술 주제, 포트폴리오 또는 면접 대상 레포지토리를 요청합니다.

## Codex 설치

저장소를 복제합니다.

```bash
git clone https://github.com/sky980221/ask-like-a-toss-interviewer.git
```

스킬 디렉터리를 개인 Codex 스킬 폴더에 복사합니다.

```bash
mkdir -p ~/.codex/skills
cp -R ask-like-a-toss-interviewer/skills/ask-like-a-toss-interviewer ~/.codex/skills/
```

이미 같은 이름의 스킬이 설치되어 있다면 기존 디렉터리를 직접 덮어쓰지 말고 필요한 변경 사항을 먼저 확인하세요.

## Claude Code 설치

가장 단순한 방법은 같은 스킬 디렉터리를 Claude Code의 개인 스킬 폴더에 복사하는 것입니다.

```bash
mkdir -p ~/.claude/skills
cp -R ask-like-a-toss-interviewer/skills/ask-like-a-toss-interviewer ~/.claude/skills/
```

설치 후 Claude Code에서 다음 명령으로 시작합니다.

```text
/ask-like-a-toss-interviewer
```

플러그인과 마켓플레이스를 통한 설치, 프로젝트 단위 설치와 문제 해결 방법은 [Claude Code 사용 가이드](docs/claude-code.md)를 참고하세요.

## 사용법

Codex에서는 `$` 접두사로 호출합니다.

```text
$ask-like-a-toss-interviewer
```

레포지토리를 지정할 수도 있습니다.

```text
$ask-like-a-toss-interviewer 이 레포지토리의 주문·결제 모듈을 기반으로 직무 인터뷰를 진행해줘.
```

학습 중인 주제로 바로 시작할 수도 있습니다.

```text
$ask-like-a-toss-interviewer 트랜잭션 격리 수준을 공부했어. 이 주제로 면접을 진행해줘.
```

Claude Code에서는 `/` 명령으로 호출하고 뒤에 요청을 이어서 입력합니다.

```text
/ask-like-a-toss-interviewer 트랜잭션 격리 수준을 공부했어. 이 주제로 면접을 진행해줘.
```

면접 중에는 한 번에 하나의 질문만 제시합니다. 평가와 모범 답안은 사용자가 면접을 중단하거나 피드백을 요청한 뒤 제공합니다.

## 프로젝트 구조

```text
.
├── .claude-plugin/
│   ├── marketplace.json
│   └── plugin.json
├── docs/
│   └── claude-code.md
├── assets/
│   └── mana-tear-crying-doodle.jpg
├── plugin.json
└── skills/
    └── ask-like-a-toss-interviewer/
        ├── SKILL.md
        ├── agents/
        │   └── openai.yaml
        └── references/
            ├── repository-interview-mode.md
            └── server-interview-patterns.md
```

## 한계

- 이 스킬은 비공식 연습 도구이며 특정 회사의 합격을 보장하지 않습니다.
- 토스의 현재 질문 목록, 평가 방식과 내부 의사결정을 알고 있다고 주장하지 않습니다.
- 결과 평가는 통계적인 합격 확률이 아니라 답변을 바탕으로 한 주관적인 준비도 판단입니다.

## License

[MIT License](LICENSE)
