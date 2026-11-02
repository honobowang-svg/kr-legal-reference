# 대한민국 법률 참고 어시스턴트 · Architecture（단일 Bot 내부분진）

> Workspace: `/workspace/global-law-agents/kr/`  
> Free public **legal reference** knowledge base（법률 의견 아님）.  
> **1**개의 Grok Bot으로 내부 라우팅（복수 Bot 아님）.  
> 개정: 2026-11-02（Asia/Shanghai）

---

## 1. Design goals

1. Mirror JP pack (`global-law-agents/jp`) and US pack (`global-law-agents/us`): master prompt + 11 branches × 5 files.
2. **Nationwide-law first** triage; ask **region / court** only when venue, labor office, or lease situs matters.
3. Criminal = rights/procedure only; immigration = reference only.
4. Never fabricate statutes; mark gaps **`【확인필요】`**.
5. 유류분: 2024.4.25 Constitutional Court + follow-up Civil Code amendments with verified effective dates.
6. Answer language: Korean default; Chinese/English if user writes in them; keep official law names in Korean.

---

## 2. Runtime assembly

| Layer | File(s) | Role |
|-------|---------|------|
| Instructions | `bot_master_prompt.md` | Persona, triage, routing, refusals, disclaimer |
| Branch playbooks | `*/system_prompt.md` | Scope, refuse list, flow |
| Knowledge | `*/knowledge_base.md` | Cited statutes / official portals |
| Tools | `*/calculators.md` | Formulas (OT, MW, severance, inheritance, interest) |
| Clocks | `*/deadlines.md` | Limitation / procedure clocks |
| Forms | `*/templates.md` | Checklists / letter skeletons |
| QA (optional) | `test_cases.md`, `eval_report.md` | Do **not** attach as user-facing knowledge unless testing |

---

## 3. Triage sequence

```
User question
  → Ask key facts (+ region/court when relevant)
  → Route to one of 11 categories
  → Load that branch five-pack
  → Answer with citations + disclaimer (answer language)
```

---

## 4. Coverage policy

| Tier | Content |
|------|---------|
| National | Civil Code, Labor Standards Act, Housing Lease Protection Act, Electronic Commerce Act, Small Claims Act via law.go.kr |
| Verified snapshots | 2026 MW ₩10,320; small claims ₩30M; LSA Art.56 premiums; Art.26 notice; severance; 유류분 post-2024 |
| Help portals | scourt.go.kr, moel.go.kr, ftc.go.kr, klac.or.kr (132), easylaw.go.kr |

---

## 5. Safety rails

- No sentence prediction / crime-evasion / evidence destruction.
- No guaranteed immigration outcomes; no false filing coaching.
- No fake statute numbers; no jeonse-fraud how-to.
- Every answer ends with disclaimer (§7 of master prompt).

---

## 6. Maintenance

When a statute amends: update the branch `knowledge_base.md` quote + date line; bump calculator tables (esp. minimum wage each summer); add a regression case to `test_cases.md`.
