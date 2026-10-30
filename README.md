# codex-harness

A short `AGENTS.md` for running Codex CLI on a time-boxed coding task, where the process (conversation, git log, diff, tests) is reviewed along with the result.

It covers three things:
- **Environment**: bind servers to 0.0.0.0, kill only processes you started (by PID), ask before memory-heavy work or irreversible commands, never update Codex or `git push`.
- **How to work**: don't guess, show a short plan before multi-file changes, list every place a change must reach, prefer what already exists, never cut validation, data-loss handling or security, fix root causes and stop to rethink after three failed fixes, keep edits minimal, leave one small test that actually fails when broken, check every task requirement against evidence before calling it done, cite external code.
- **What to leave behind**: one local commit per feature, one entry in `DECISIONS.md` at every judgment fork (boundaries, sort order, ties, blank or malformed rows — with the alternative rejected, the source of the rule, and how it was verified; guesses are marked as guesses and flagged at once), an up-to-date `README.md` with run steps and how to verify it works (commands + expected result), and a closing line on every reply naming what was skipped or left unchecked.

## Use

```sh
git clone https://github.com/Ruminem/codex-harness
mkdir -p ~/.codex && cp codex-harness/AGENTS.md ~/.codex/AGENTS.md   # global
# or: cp codex-harness/AGENTS.md ./AGENTS.md                          # project root
cp codex-harness/templates/DECISIONS.md ./DECISIONS.md                # decision log skeleton
```

`templates/DECISIONS.md` is an empty skeleton (sections only, no answers): questions asked, one entry per judgment fork, Codex output that was changed or rejected, verification, remaining limits.

Start `codex` and ask it to list three rules from `AGENTS.md` to confirm it was loaded.

The file itself is written in Korean.

## Approval workflow and verification

Read-only investigation comes first. Once enough information is available, explain the facts, unknowns, why the information matters, what it enables, and the proposed next action; then wait for approval. After that approval, present the files and impact, behavior, chosen approach and alternatives, validation, and exclusions; wait for a separate explicit design approval before implementation. Showing a plan alone is insufficient.

Answers, supplied material, and silence do not count as approval. Approval applies only to the presented stage and scope. Obtain approval for changes to that scope; continue routine work within the approved implementation scope without asking again. The user may explicitly waive a particular approval stage. Before approval, only read-only investigation and proposals in the conversation are allowed; file edits, implementation, commits, and settings changes wait.

For global installation on an existing PC, back up `~/.codex/AGENTS.md` to a unique filename before using the copy command above. This installs global user instructions. It does not replace the system prompt or prove that an existing session reloaded the file.

In a fresh Codex session, request information gathering only. Expect an information report and an approval request without file edits. Approve that report: expect a design proposal and another approval request without implementation. Supply extra information without approving: expect implementation to remain pending. Explicitly approve the design: implementation may proceed within that scope. These are manual behavioral checks; static text checks cannot guarantee model compliance.

## License

Apache-2.0. A few lines are adapted from [ponytail](https://github.com/DietrichGebert/ponytail) and [superpowers](https://github.com/obra/superpowers) (both MIT); see `THIRD_PARTY_NOTICES.md`.

---

# codex-harness (한국어)

시간 제한이 있는 코딩 과제에서 Codex CLI 에 주는 짧은 `AGENTS.md` 임. 결과물뿐 아니라 과정(대화·git log·diff·테스트)도 검토되는 자리를 전제로 함.

세 가지를 다룸.
- **환경**: 서버는 0.0.0.0 에 띄움, 프로세스는 직접 띄운 것만 PID 로 끔, 메모리를 크게 쓰는 일과 되돌릴 수 없는 명령은 먼저 물음, Codex 업데이트와 `git push` 는 안 함
- **일하는 법**: 짐작하지 않음, 여러 파일을 고치기 전에 짧은 계획을 보임, 변경이 닿아야 할 곳을 다 적음, 이미 있는 것을 먼저 씀, 입력 검증·데이터 유실 처리·보안은 줄이지 않음, 원인을 고침, 세 번 고쳐도 안 되면 멈추고 다시 봄, 고칠 자리만 고침, 깨지면 실제로 실패하는 작은 테스트를 하나 남김, 끝났다고 하기 전에 요구사항을 항목마다 증거로 확인함, 외부 코드는 출처를 남김
- **남기는 것**: 기능마다 로컬 커밋 하나, 판단이 갈리는 지점(경계값·정렬 순서·동률·빈 값과 잘못된 줄)마다 `DECISIONS.md` 한 항목(버린 대안, 규칙의 출처, 어떻게 확인했는지 — 추정이면 추정이라 쓰고 바로 알림), 실행 방법과 동작 확인 방법(명령 + 기대 결과)이 늘 최신인 `README.md`, 답마다 끝에 건너뛴 것·확인 안 한 것 한두 줄

## 쓰는 법

```sh
git clone https://github.com/Ruminem/codex-harness
mkdir -p ~/.codex && cp codex-harness/AGENTS.md ~/.codex/AGENTS.md   # 전역
# 또는: cp codex-harness/AGENTS.md ./AGENTS.md                         # 프로젝트 루트
cp codex-harness/templates/DECISIONS.md ./DECISIONS.md                # 결정 기록 뼈대
```

`templates/DECISIONS.md` 는 답이 없는 빈 뼈대임(절만 있음): 물어본 것, 갈림길마다 한 항목, Codex 가 낸 것 중 고치거나 버린 것, 검증, 남은 한계.

`codex` 를 띄우고 `AGENTS.md` 에서 읽은 규칙 세 개를 말해 보라고 하면 실렸는지 확인됨.

## 승인 절차와 동작 확인 방법

읽기 전용 조사 → 정보의 필요성·가능한 작업·다음 행동 보고 → 정보 수집 결과 승인 → 파일·영향 범위·처리 규칙·방법과 대안·검증·제외 범위 설계 제시 → 별도 설계 승인 → 승인 범위 구현 순서로 진행함. 계획을 보여 주는 것만으로 승인을 대신하지 않음.

추가 답변·자료·침묵은 승인이 아님. 승인은 제시한 단계와 범위에만 적용하고, 범위를 바꿀 때 다시 승인받음. 승인 범위 안의 통상 작업에는 매번 재승인을 요구하지 않음. 사용자가 특정 승인 단계를 명시적으로 생략할 수 있음. 승인 전에는 읽기 전용 조사·대화 속 제안만 하고, 파일 수정·구현·커밋·설정 적용은 기다림.

이 PC에 전역 적용할 때는 기존 `~/.codex/AGENTS.md`를 겹치지 않는 파일명으로 백업한 뒤 위 복사 명령을 실행함. 적용 대상은 전역 사용자 지침이며, 시스템 프롬프트 교체나 실행 중 세션의 재로딩을 뜻하지 않음.

PowerShell에서 정적 문구 검사와 의도적 누락 검사를 실행함:

```powershell
$rules = Get-Content -LiteralPath .\AGENTS.md -Raw -Encoding UTF8
$required = @('정보 수집 승인', '설계 승인', '각 정보가 필요한 이유', '계획을 보여 주는 것만으로 승인을 대신하지 않는다', '질문에 대한 답변·자료 전달·침묵은 승인으로 간주하지 않는다', '승인 전 작업', '사용자가 특정 승인 단계를 명시적으로 생략', '매 작업마다 재승인을 요구하지 않는다')
function Test-ApprovalRules([string]$text) {
    foreach ($phrase in $required) {
        if (-not $text.Contains($phrase)) { return $false }
    }
    return $true
}
Test-ApprovalRules $rules
Test-ApprovalRules ($rules.Replace('설계 승인', ''))
git diff --check
```

기대 결과는 차례로 `True`, `False`이며, `git diff --check`는 출력 없이 종료 0이어야 함. 두 번째 검사는 메모리의 문자열만 바꾸므로 원본 파일은 수정하지 않음. 문구의 존재를 검사할 뿐 모델 행동을 보장하지는 않음.

전역 적용 후 동일 내용인지 확인함:

```powershell
(Get-FileHash .\AGENTS.md).Hash -eq (Get-FileHash "$env:USERPROFILE\.codex\AGENTS.md").Hash
```

기대 결과는 `True`임. 새 Codex 세션에서 다음 수동 확인도 수행함:

1. 정보 수집만 요청 → 필요성·가능한 작업·다음 행동 보고와 승인 요청, 파일 변경 없음.
2. 정보 수집 결과만 승인 → 설계 제시와 별도 승인 요청, 구현 없음.
3. 추가 자료만 전달 → 구현 승인으로 취급하지 않고 승인 대기.
4. 설계를 명시적으로 승인 → 승인 범위 안에서 구현 진행.

이 수동 확인은 별도 새 세션이 필요하며, 파일 일치나 정적 문구 검사로 대체되지 않음. 실제 수행 여부와 한계는 `DECISIONS.md`에 기록함.

## 라이선스

Apache-2.0. 몇 줄은 [ponytail](https://github.com/DietrichGebert/ponytail)·[superpowers](https://github.com/obra/superpowers)(둘 다 MIT)에서 옮겨 고쳤음 — `THIRD_PARTY_NOTICES.md` 참고
