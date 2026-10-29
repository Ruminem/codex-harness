# codex-harness

A short `AGENTS.md` for running Codex CLI on a time-boxed coding task, where the process (conversation, git log, diff, tests) is reviewed along with the result.

It covers three things:
- **Environment**: bind servers to 0.0.0.0, kill only processes you started (by PID), ask before memory-heavy work or irreversible commands, never update Codex or `git push`.
- **How to work**: don't guess, show a short plan before multi-file changes, list every place a change must reach, prefer what already exists, never cut validation, data-loss handling or security, fix root causes, keep edits minimal, leave one small test that actually fails when broken, cite external code.
- **What to leave behind**: one local commit per feature, one line per decision in `DECISIONS.md` (including how it was verified), an up-to-date `README.md` with run steps and how to verify it works (commands + expected result), and a closing line on every reply naming what was skipped or left unchecked.

## Use

```sh
git clone https://github.com/Ruminem/codex-harness
mkdir -p ~/.codex && cp codex-harness/AGENTS.md ~/.codex/AGENTS.md   # global
# or: cp codex-harness/AGENTS.md ./AGENTS.md                          # project root
```

Start `codex` and ask it to list three rules from `AGENTS.md` to confirm it was loaded.

The file itself is written in Korean.

## License

Apache-2.0. A few lines are adapted from [ponytail](https://github.com/DietrichGebert/ponytail) (MIT); see `THIRD_PARTY_NOTICES.md`.

---

# codex-harness (한국어)

시간 제한이 있는 코딩 과제에서 Codex CLI 에 주는 짧은 `AGENTS.md` 임. 결과물뿐 아니라 과정(대화·git log·diff·테스트)도 검토되는 자리를 전제로 함.

세 가지를 다룸.
- **환경**: 서버는 0.0.0.0 에 띄움, 프로세스는 직접 띄운 것만 PID 로 끔, 메모리를 크게 쓰는 일과 되돌릴 수 없는 명령은 먼저 물음, Codex 업데이트와 `git push` 는 안 함
- **일하는 법**: 짐작하지 않음, 여러 파일을 고치기 전에 짧은 계획을 보임, 변경이 닿아야 할 곳을 다 적음, 이미 있는 것을 먼저 씀, 입력 검증·데이터 유실 처리·보안은 줄이지 않음, 원인을 고침, 고칠 자리만 고침, 깨지면 실제로 실패하는 작은 테스트를 하나 남김, 외부 코드는 출처를 남김
- **남기는 것**: 기능마다 로컬 커밋 하나, 결정마다 `DECISIONS.md` 한 줄(어떻게 확인했는지 포함), 실행 방법과 동작 확인 방법(명령 + 기대 결과)이 늘 최신인 `README.md`, 답마다 끝에 건너뛴 것·확인 안 한 것 한두 줄

## 쓰는 법

```sh
git clone https://github.com/Ruminem/codex-harness
mkdir -p ~/.codex && cp codex-harness/AGENTS.md ~/.codex/AGENTS.md   # 전역
# 또는: cp codex-harness/AGENTS.md ./AGENTS.md                         # 프로젝트 루트
```

`codex` 를 띄우고 `AGENTS.md` 에서 읽은 규칙 세 개를 말해 보라고 하면 실렸는지 확인됨.

## 라이선스

Apache-2.0. 몇 줄은 [ponytail](https://github.com/DietrichGebert/ponytail)(MIT)에서 옮겨 고쳤음 — `THIRD_PARTY_NOTICES.md` 참고
