# Brainstorm Plugin

여러 AI의 의견을 병렬로 수집하고 종합 분석하는 Claude Code 플러그인입니다.

## 기능

`/brainstorm` 명령으로 3개 AI 회사의 관점을 종합합니다:

| AI | 회사 | 역할 |
|----|------|------|
| Gemini | Google | 의견 제공 |
| Codex | OpenAI | 의견 제공 |
| Claude | Anthropic | 의견 수집 + 종합 분석 |

## 사전 요구사항

다음 CLI가 설치되어 있어야 합니다:

```bash
# Gemini CLI
npm install -g @anthropic-ai/gemini-cli
# 또는 Google 공식 CLI

# Codex CLI (OpenAI)
# https://github.com/openai/codex 참조
```

## 설치

### 방법 1: 심볼릭 링크 (개발용)

```bash
ln -s ~/claude-plugins/brainstorm-plugin ~/.claude/plugins/brainstorm-plugin
```

### 방법 2: Git 클론 후 링크

```bash
git clone https://github.com/your-username/brainstorm-plugin.git
ln -s /path/to/brainstorm-plugin ~/.claude/plugins/brainstorm-plugin
```

## 사용법

```
/brainstorm Obsidian 태그 체계를 어떻게 구성하면 좋을까?
/brainstorm Redis vs Memcached 선택 기준은?
/brainstorm 마이크로서비스 간 통신 방식 추천해줘
```

## 동작 흐름

```
/brainstorm "질문"
      ↓
┌─────────────────────────────────────┐
│  서브에이전트 (haiku)               │
│  ├── Gemini CLI  ────┐              │
│  ├── Codex CLI   ────┤ 병렬 실행    │
│  └── 결과 종합                      │
└─────────────────────────────────────┘
      ↓
  요약만 메인 컨텍스트로 반환
```

## 라이선스

MIT
