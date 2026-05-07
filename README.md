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
```

## 사용 방식

`plugins/cto-plugin/skills/cto/SKILL.md`가 실제 CTO 스킬 진입점입니다.

Codex에서 사용할 때는 다음처럼 호출합니다.

```text
$cto 이 요구사항을 CTO 관점으로 분석해줘
```

## 관리 규칙

- 스킬의 핵심 실행 규칙은 `SKILL.md`에 둡니다.
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
