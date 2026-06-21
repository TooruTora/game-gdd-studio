---
description: 새 게임 컨셉 문서 작성 시작. creative-director와 game-designer가 협업하여 게임 비전, 코어 루프, 필라를 정의합니다.
argument-hint: "[게임 제목 또는 컨셉 키워드 (선택)]"
---

게임 컨셉 문서 작성 워크플로우를 시작합니다.

$ARGUMENTS

**워크플로우:**

1. `design/concept/game-concept.md` 파일이 이미 존재하는지 확인합니다.
   - 존재하면: 현재 내용을 읽고 업데이트할 섹션을 물어봅니다.
   - 존재하지 않으면: 새 컨셉 문서 작성을 시작합니다.

2. 다음 질문들로 대화를 시작합니다:
   - 어떤 장르/스타일의 게임인가요?
   - 핵심 플레이어 경험은 무엇인가요? (플레이어가 무엇을 "하는" 게임인가요?)
   - 레퍼런스 게임이 있다면?
   - 대략적인 규모와 플랫폼은?

3. `${CLAUDE_PLUGIN_ROOT}/templates/game-concept.md` 템플릿을 기반으로 각 섹션을 순서대로 작성합니다:
   - Elevator Pitch
   - Core Identity
   - Core Fantasy & Unique Hook
   - Player Experience (MDA Framework)
   - Core Loop (30초 / 5-15분 / 세션 / 장기)
   - Game Pillars (3-5개)
   - MVP Definition

4. 각 섹션은:
   - 먼저 초안을 대화에서 보여주고
   - "이 섹션을 design/concept/game-concept.md에 작성해도 될까요?" 확인 후 작성

5. 컨셉 문서 완성 후 다음 단계 제안:
   - `/gdd-design [핵심 시스템명]` — 첫 번째 시스템 GDD 작성
   - `@creative-director` — 필라 심화 작업

**에이전트 역할:**
- 현재 컨텍스트에서 `creative-director`와 `game-designer`의 관점을 통합하여 답변합니다.
- 게임 비전(creative-director 관점)과 메카닉 실현 가능성(game-designer 관점)을 균형있게 제시합니다.
