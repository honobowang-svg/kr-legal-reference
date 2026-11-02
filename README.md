# 대한민국 법률 참고 어시스턴트 — Knowledge Base

Free, public **South Korea** legal **reference** knowledge base for a single Grok Bot with internal triage.

**법률 상담·법률 의견이 아닙니다. 변호사가 아닙니다.** 법령·금액·절차는 개정됩니다. 반드시 [국가법령정보센터](https://www.law.go.kr/)、[대법원](https://www.scourt.go.kr/)、고용노동부·공정거래위원회 등 공식 정보로 확인하고, 필요하면 **변호사** 또는 **대한법률구조공단（132）**에 상담하십시오.

## What this is

- **대한민국 전국법**을 중심으로, 필요할 때만 **관할·지역 창구**에 언급합니다.
- **11 branches**, 각 5파일: `system_prompt.md`, `knowledge_base.md`, `calculators.md`, `deadlines.md`, `templates.md`.
- 답변 언어 기본은 **한국어**. 사용자가 중국어 또는 영어로 쓴 경우 그에 맞춰 답변 가능（법령 공식 명칭은 한국어 유지）.

## Branches

| Dir | Topic |
|-----|--------|
| `family/` | 이혼·양육비·친권 |
| `inheritance/` | 상속·유언·유류분（2024 헌재 결정·후속 개정 포함） |
| `contracts/` | 민법·채권（계약） |
| `torts/` | 불법행위·교통사고（민사） |
| `property/` | 주택임대차보호법·전세·보증금（전세사기 관련 참고） |
| `employment/` | 근로기준법·최저임금 2026·퇴직금·해고예고·연장·야간·휴일 가산 |
| `criminal/` | 형사의 **권리·절차만**（형량 예측·수사 회피 금지） |
| `business/` | 회사법·상표·저작권 |
| `admin/` | 행정심판·출입국/체류（**참고만**） |
| `consumer/` | 전자상거래법 청약철회 등 소비자 |
| `procedure/` | 소액사건（3,000만원）·지급명령·대한법률구조공단 |

## How to use (Bot assembly)

1. 루트 `bot_master_prompt.md`를 Bot Instructions에 붙이거나 첨부.
2. 각 브랜치 5파일을 지식으로 첨부.
3. `test_cases.md`와 `eval_report.md`는 QA용. 일반 답변 지식에는 넣지 않음.

## Verification rule

조문 인용은 공식 소스만（[국가법령정보센터](https://www.law.go.kr/)、[대법원](https://www.scourt.go.kr/)、[고용노동부](https://www.moel.go.kr/)、[최저임금위원회](https://www.minimumwage.go.kr/)、[공정거래위원회](https://www.ftc.go.kr/)）. **법령명＋조호＋시행／개정일** 명시. 미확인은 **`【확인필요】`**. 법령·숫자·판례 날조 금지.

## Disclaimer (every answer)

본 프로젝트는 **참고 정보만** 제공합니다. **법률 의견이 아니며**, 어시스턴트는 **변호사가 아니고**, 이용자는 **변호사 또는 대한법률구조공단（132）**에 상담해야 합니다.

## License / cost

Free public reference materials. No affiliation with any commercial marketplace or private company brand is implied.
