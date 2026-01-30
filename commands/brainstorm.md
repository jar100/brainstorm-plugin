---
description: 여러 AI(Gemini, Codex)에게 병렬로 의견을 수집하고 Claude가 종합 분석
argument-hint: <질문>
---

# Brainstorm

3개 AI 회사(Google, OpenAI, Anthropic)의 관점을 종합합니다.

## 사용자 질문

$ARGUMENTS

## Instructions

Task 도구를 사용하여 서브에이전트를 실행하세요:

- **subagent_type**: `general-purpose`
- **model**: `haiku`
- **description**: `AI 의견 수집`
- **prompt**: 아래 내용을 그대로 전달

```
Gemini와 Codex CLI를 병렬로 실행하여 다음 질문에 대한 의견을 수집하고 비교 분석해주세요.

질문: $ARGUMENTS

실행할 명령:
1. timeout 300 gemini "위 질문" 2>&1 | head -150
2. timeout 300 codex exec "위 질문" 2>&1 | head -150

두 명령을 병렬로 실행하고, 결과를 아래 형식으로 요약해주세요:

## 🤖 AI 의견 수집 결과
### Gemini (Google)
**핵심 제안**: (1-2문장 요약)
**주요 포인트**:
-
-

### Codex (OpenAI)
**핵심 제안**: (1-2문장 요약)
**주요 포인트**:
-
-

### 비교 분석
| 항목 | Gemini | Codex |
|------|--------|-------|
| 접근 방식 | | |
| 강조점 | | |
| 고유 인사이트 | | |

### 공통점
- (두 AI가 공통으로 제안한 내용)

### 종합 추천 (Claude 분석)
(두 의견 + Claude 관점을 종합한 최종 추천 2-3문장)
```

서브에이전트가 반환한 요약 결과를 사용자에게 전달하세요.
