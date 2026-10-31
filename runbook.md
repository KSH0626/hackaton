# 스킬 설치 명령

## Linux / Bash

```bash
# Matt Pocock 전체
codex plugin marketplace add mattpocock/skills
codex plugin add mattpocock-skills@mattpocock

# Engineering 코드 리뷰·문서화 전역 설치
npx --yes skills@latest add anthropics/knowledge-work-plugins --skill code-review documentation -a codex -g -y

# webapp-testing 전역 설치
npx --yes skills@latest add anthropics/skills --skill webapp-testing -a codex -g -y
```

## Windows PowerShell

```powershell
# Matt Pocock 전체
codex plugin marketplace add mattpocock/skills
codex plugin add mattpocock-skills@mattpocock

# Engineering 코드 리뷰·문서화 전역 설치
npx.cmd --yes skills@latest add anthropics/knowledge-work-plugins --skill code-review documentation -a codex -g -y

# webapp-testing 전역 설치
npx.cmd --yes skills@latest add anthropics/skills --skill webapp-testing -a codex -g -y
```
