# CTO Plugin

개인 CTO Orchestrator 스킬을 버전관리하기 위한 Codex 플러그인 저장소입니다.

## 구조

```text
.agents/
  plugins/
    marketplace.json
plugins/
  cto-plugin/
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

`plugins/cto-plugin/skills/cto/SKILL.md`가 실제 CTO 스킬 진입점입니다.

Codex에서 사용할 때는 다음처럼 호출합니다.

```text
$cto 이 요구사항을 CTO 관점으로 분석해줘
```

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
- 플러그인 등록 정보는 `plugins/cto-plugin/.codex-plugin/plugin.json`에서 관리합니다.
- Codex UI 등록용 마켓플레이스 항목은 `.agents/plugins/marketplace.json`에서 관리합니다.

## Git 초기화

이 폴더에서 Git 저장소를 초기화하면 플러그인과 스킬을 한 번에 버전관리할 수 있습니다.

```powershell
git init
git add .
git commit -m "Initial CTO plugin skill"
```
