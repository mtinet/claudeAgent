# claudeAgent

Claude Agent를 만드는 코드 
- agentPromptTeam.md
- agentStartPrompt.md
# 📄 두 문서 비교 분석

> **한 줄 요약:** 문서 1은 "Agent+Skill 시스템을 설계해주는 AI 팀 프롬프트"이고, 문서 2는 "교육자용 시스템 그 자체의 설계 명세서"입니다. 즉 문서 1로 만들어낸 결과물의 예시가 문서 2인 셈입니다.

---

## 🎯 목적과 성격

**문서 1 (agentPromptTeam.md)** 은 **메타 도구**입니다. Claude Project에 붙여넣으면 Sam·Jenny·Will이라는 가상의 팀이 사용자와 대화하며 어떤 분야든 Agent+Skill 시스템을 설계해주는 범용 프롬프트입니다. 교육자용 시스템을 만들 수도 있고, 마케터용, 개발팀용도 만들 수 있습니다.

**문서 2 (agentStartPrompt.md)** 는 **실제 결과물**입니다. 교육자를 위한 시스템이 어떻게 생겨야 하는지 완전히 명세화된 설계 문서로, 이걸 Claude Code에 넣으면 바로 파일들을 생성할 수 있습니다.

---

## 🏗️ 구조와 복잡도

문서 1은 Agent 3개(orchestrator + curriculum-planner + material-creator)로 단순한 구조인 반면, 문서 2는 Agent 6개로 훨씬 세분화되어 있습니다. Lesson Planner, Assessment, Materials, Communication, Research로 각 교육 업무를 전담 Agent가 나눠 맡는 구조입니다.

Skill도 문서 1은 3개(curriculum-design, slide-generator, document-writer)인데, 문서 2는 6개로 quiz-generator, rubric-builder, parent-letter, learning-objectives, exam-creator, classroom-activity까지 커버합니다. 특히 **가정통신문, 루브릭, 퀴즈** 같은 교육 현장 특화 기능이 추가된 게 눈에 띕니다.

---

## 🔗 워크플로우 방식

가장 큰 기술적 차이는 처리 방식입니다. 문서 1은 **혼합 방식(순차+병렬)** 으로 상황에 따라 유연하게 동작하는 반면, 문서 2는 **명시적 병렬 처리**를 핵심으로 설계했습니다. Orchestrator가 여러 Agent를 동시에 호출해서 수업 계획서·PPT·퀴즈를 한꺼번에 만드는 구조입니다.

---

## 🚀 활용 방법

|  | 문서 1 | 문서 2 |
|---|---|---|
| **어디에 넣나** | Claude Project Instructions | Claude Code |
| **무엇을 만드나** | Agent 시스템 설계 | 실제 교육 자료 |
| **대상** | 시스템 설계자 | 현장 교육자 |
| **재사용성** | 모든 도메인에 적용 가능 | 교육 전용 |

---

## 💡 실제 활용 흐름

```
문서 1 (메타 도구)
    ↓ Claude Project에 붙여넣기
Sam·Jenny·Will과 대화하며 요구사항 수집 및 설계
    ↓ 결과물 생성
문서 2 같은 설계 명세서 완성
    ↓ Claude Code에 적용
실제 교육 자료 자동 생성
```
