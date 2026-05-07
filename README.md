# MyTeam

개인 CTO Orchestrator 스킬을 버전관리하기 위한 Codex 플러그인 저장소입니다.

## 구조

```text
.agents/
  plugins/
    marketplace.json
plugins/
  myteam-plugin/
    .codex-plugin/
      plugin.json
    skills/
      cto/
        SKILL.md
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
      cto-pm/
        SKILL.md
      cto-frontend/
        SKILL.md
      cto-backend/
        SKILL.md
      cto-architect/
        SKILL.md
      cto-domain/
        SKILL.md
      cto-qa/
        SKILL.md
      cto-skill-evaluator/
        SKILL.md
```

## 사용 방식

`plugins/myteam-plugin/skills/cto/SKILL.md`가 실제 CTO 스킬 진입점입니다.

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

Codex에서 사용할 때는 다음처럼 호출합니다.

```text
$cto 이 요구사항을 CTO 관점으로 분석해줘
```

`$cto`는 하나의 CTO를 기준으로 PM과 필요한 전문가 팀을 구성하는 진입점입니다.
항상 PM 역할을 먼저 위임하고, PM 결과에 따라 필요한 전문 역할만 선택한 뒤 CTO 관점으로 결과를 병합하도록 설계되어 있습니다.

Codex 플러그인은 이름 있는 custom sub-agent를 직접 실행하는 런타임이 아닙니다.
따라서 `$cto-pm` 같은 이름의 하위 에이전트 프로세스를 자동 실행한다고 가정하지 않습니다.
실행 환경에서 sub-agent 도구가 허용되면 generic `worker` 또는 `explorer` 하위 에이전트를 생성하고, 그 프롬프트에 `$cto-pm`, `$cto-frontend`, `$cto-backend`, `$cto-architect`, `$cto-domain`, `$cto-qa`, `$cto-skill-evaluator` 역할 지침을 주입해 팀처럼 사용합니다.

기대 흐름은 다음과 같습니다.

```text
$cto 호출
-> CTO가 PM worker를 먼저 위임
-> PM 결과로 필요한 전문 역할 선택
-> 선택된 전문 역할만 worker/explorer로 위임
-> CTO가 결과 충돌과 우선순위를 병합
-> 최종 CTO 결정 출력
```

런타임 정책상 실제 sub-agent 위임이 불가능한 환경에서는 `$cto`가 그 사실을 명시하고 같은 순서의 역할 기반 분석으로 대체합니다.

코드 리뷰, 변경 영향도, 아키텍처 병목, 기술 부채, 테스트 사각지대 분석에서는 `$cto`가 관련 specialist에게 `code-review-graph` 도구 사용을 우선 검토하도록 지시합니다.
도구가 없거나 실패하면 실패 사유를 기록하고 일반 코드 탐색과 git diff 기반 리뷰로 대체합니다.

전문 관점만 직접 사용할 때는 다음처럼 호출합니다.

```text
$cto-pm 이 요구사항을 PM 관점으로 분석해줘
$cto-frontend 이 화면 흐름을 프론트엔드 관점으로 검토해줘
$cto-backend 이 API 설계를 운영 안정성 관점으로 검토해줘
$cto-architect 이 구조의 서비스 경계를 검토해줘
$cto-domain 이 CAD/GIS 워크플로우가 도메인상 맞는지 검증해줘
$cto-qa 이 기능의 실패 케이스를 찾아줘
$cto-skill-evaluator CTO 스킬의 응답 행동을 평가해줘
```

## 관리 규칙

- 메인 오케스트레이션 규칙은 `skills/cto/SKILL.md`에 둡니다.
- 독립 호출 가능한 전문 스킬은 `skills/cto-*` 폴더에서 관리합니다.
- 전문 관점별 세부 지침은 `skills/cto/references/agents/` 아래에서 관리합니다.
- 라우팅 키워드는 `skills/cto/references/routing.json`에서 관리합니다.
- 스킬 자체의 응답 행동 평가는 `skill_evaluator.md` 관점으로 관리합니다.
- `$cto`는 전문 스킬을 단순히 나열하지 않고, 가능한 경우 generic 하위 에이전트에 역할 지침을 주입해 하나의 팀처럼 운용합니다.
- 코드 리뷰 관련 도구 사용 규칙은 메인 `cto`, `cto-backend`, `cto-architect`, `cto-qa`, `cto-skill-evaluator` 스킬에서 관리합니다.
- 플러그인 등록 정보는 `plugins/myteam-plugin/.codex-plugin/plugin.json`에서 관리합니다.
- Codex UI 등록용 마켓플레이스 항목은 `.agents/plugins/marketplace.json`에서 관리합니다.

## Git 초기화

이 폴더에서 Git 저장소를 초기화하면 플러그인과 스킬을 한 번에 버전관리할 수 있습니다.

```powershell
git init
git add .
git commit -m "Initial CTO plugin skill"
```
