# GDD 스튜디오 산출물 출력 정책

> 모든 GDD 작성 커맨드·에이전트는 파일을 생성/갱신할 때 이 정책을 따릅니다.

## 핵심 원칙

- **정본(canonical source)은 항상 Markdown(`.md`)** — 에이전트 간 컨텍스트 공유, 후속 커맨드(`/gdd-review`, `/gdd-review-all`), 버전 관리의 기준입니다.
- **사용자에게 보여주는 표시본은 HTML** — 가독성 있는 뷰. md 정본과 항상 동일한 내용을 담습니다.
- **md를 생성하거나 갱신할 때마다 대응 html을 함께 생성/갱신**합니다. (md 정본이 승인·기록되면 html은 별도 승인 없이 자동 동반 생성)

## 파일 위치 규칙

표시용 html은 정본 md와 **동일한 하위 경로를 `design/html/` 아래에 미러링**합니다.

| 정본 (md) | 표시본 (html) |
|-----------|--------------|
| `design/concept/game-concept.md` | `design/html/concept/game-concept.html` |
| `design/gdd/combat.md` | `design/html/gdd/combat.html` |
| `design/quick-notes/pause-menu.md` | `design/html/quick-notes/pause-menu.html` |
| `design/narrative/world.md` | `design/html/narrative/world.html` |
| `design/levels/level-01.md` | `design/html/levels/level-01.html` |

## HTML 생성 규칙

- **자가완결형(self-contained) 단일 `.html`** — 외부 파일·CDN 의존 없이 브라우저에서 바로 열립니다.
- md 내용을 충실히 렌더링: 제목, 표, 목록, 코드블록, 인용, 강조 등.
- 아래 **표준 스타일을 `<head>`에 인라인**으로 넣어 문서 간 일관성을 유지합니다.
- 한국어 본문 가독성 우선.
- 문서 상단에 제목과, 그 아래 `정본: design/.../X.md` 출처를 `<p class="source">`로 표기합니다.

## 표준 HTML 스타일

생성하는 모든 html의 `<head>`에 아래 `<style>`을 그대로 인라인합니다.

```html
<style>
  :root { color-scheme: light dark; }
  body { font-family: -apple-system, "Segoe UI", "Malgun Gothic", system-ui, sans-serif;
         line-height: 1.7; max-width: 860px; margin: 2rem auto; padding: 0 1.25rem;
         color: #1a1a1a; background: #fff; }
  h1, h2, h3 { line-height: 1.3; font-weight: 700; }
  h1 { font-size: 1.9rem; border-bottom: 3px solid #4f46e5; padding-bottom: .4rem; }
  h2 { font-size: 1.4rem; margin-top: 2.2rem; border-bottom: 1px solid #e5e7eb; padding-bottom: .3rem; }
  h3 { font-size: 1.15rem; margin-top: 1.6rem; color: #4f46e5; }
  table { border-collapse: collapse; width: 100%; margin: 1rem 0; font-size: .95rem; }
  th, td { border: 1px solid #d1d5db; padding: .5rem .7rem; text-align: left; vertical-align: top; }
  th { background: #f3f4f6; font-weight: 600; }
  code { background: #f3f4f6; padding: .15rem .4rem; border-radius: 4px;
         font-family: "Cascadia Code", Consolas, monospace; font-size: .9em; }
  pre { background: #1e1e2e; color: #e5e7eb; padding: 1rem; border-radius: 8px; overflow-x: auto; }
  pre code { background: none; color: inherit; padding: 0; }
  blockquote { border-left: 4px solid #4f46e5; margin: 1rem 0; padding: .3rem 1rem;
               background: #f8f7ff; color: #444; }
  .source { font-size: .85rem; color: #6b7280; margin-top: -.4rem; }
</style>
```

### 골격 예시

```html
<!doctype html>
<html lang="ko">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>[문서 제목]</title>
  <style>/* 위 표준 스타일 */</style>
</head>
<body>
  <h1>[문서 제목]</h1>
  <p class="source">정본: design/gdd/combat.md</p>
  <!-- md 본문을 렌더링한 HTML -->
</body>
</html>
```

## 워크플로 통합

1. md 정본을 생성/승인/갱신한다. (섹션 단위 승인 게이트는 기존대로 md 기준으로 진행)
2. md가 기록되면, 같은 내용을 위 규칙으로 html로 변환해 `design/html/...`에 쓴다. (자동 — 별도 승인 불필요)
3. 작업 완료 시 사용자에게 html 표시본 경로를 안내한다.
   예: `표시본: design/html/gdd/combat.html (브라우저로 열어보세요)`

## 적용 범위

- **파일 산출물을 만드는 작성 커맨드/에이전트**: 위 규칙을 따른다.
- **읽기 전용 리뷰 커맨드**(`/gdd-review`, `/gdd-review-all`): 채팅으로 리포트를 출력하므로 html 산출물을 만들지 않는다. (단 사용자가 리포트 파일을 요청하면 동일 정책 적용)
