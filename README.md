# MyTeam

개인 MyTeam Orchestrator 스킬을 버전관리하기 위한 Codex 플러그인 저장소입니다.

## 구조

```text
.agents/
  plugins/
    marketplace.json
plugins/
  myteam-plugin/
    .codex-plugin/
      plugin.json
    assets/
      myteam.svg
    skills/
      team/
        SKILL.md
        agents/
          openai.yaml
        references/
          routing.json
          agents/
            pm.md
            frontend.md
            backend.md
            architect.md
            domain.md
            qa.md
            skill_evaluator.md
```

## 사용 방식

`plugins/myteam-plugin/skills/team/SKILL.md`가 실제 MyTeam 스킬 진입점입니다.

Codex에서 사용할 때는 다음처럼 호출합니다.

```text
$team 이 요구사항을 MyTeam 관점으로 분석해줘
```

외부에서 직접 호출하는 명령은 `$team` 하나만 사용합니다.
PM, Frontend, Backend, Architect, Domain, QA, Skill Evaluator는 별도 명령이 아니라 `$team` 내부에서 필요한 경우에만 선택되는 역할입니다.

`$team`은 PM 분석을 먼저 수행하고, PM 결과에 따라 필요한 전문 역할만 generic `worker` 또는 `explorer` 하위 에이전트에 위임한 뒤 결과를 병합하도록 설계되어 있습니다.
실제 sub-agent 위임이 불가능한 환경에서는 그 사유를 명시하고 같은 순서의 역할 기반 분석으로 대체합니다.

코드 리뷰, 변경 영향도, 아키텍처 병목, 기술 부채, 테스트 사각지대 분석에서는 `code-review-graph` 도구 사용을 우선 검토합니다.
도구가 없거나 실패하면 실패 사유를 기록하고 일반 코드 탐색과 git diff 기반 리뷰로 대체합니다.

## 실제 설치 위치

Codex 앱에서 인식되는 개인 플러그인 설치 위치는 아래 경로입니다.

```text
C:\Users\yusco\.codex\plugins\cache\personal-plugins\myteam-plugin
```

설치된 마켓플레이스 파일은 캐시 루트 기준으로 관리합니다.

```text
C:\Users\yusco\.codex\plugins\cache\personal-plugins\.agents\plugins\marketplace.json
```

이때 `marketplace.json`의 플러그인 경로는 캐시 루트 기준으로 `./myteam-plugin`을 사용합니다.

## 관리 규칙

- 메인 오케스트레이션 규칙은 `skills/team/SKILL.md`에 둡니다.
- 전문 역할별 세부 지침은 `skills/team/references/agents/` 아래에서 관리합니다.
- 라우팅 키워드는 `skills/team/references/routing.json`에서 관리합니다.
- 플러그인 등록 정보는 `plugins/myteam-plugin/.codex-plugin/plugin.json`에서 관리합니다.
- Codex UI 등록용 마켓플레이스 항목은 `.agents/plugins/marketplace.json`에서 관리합니다.
