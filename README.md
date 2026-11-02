# FDE Field Design Validation

**기준 템플릿이 실제 산업 문제에서 문제 정의 → 대안 비교 → 방법 선택 → 설계 인계까지 도와주는지 검토하는 별도 저장소입니다.**

[기준 template](https://github.com/daehuikim/fde-service-template)의 `a146432`에서 GitHub template 생성으로 파생했습니다. 제품별 앱·agent·optimizer는 구현하지 않았습니다. 기존 template 앱은 원본 그대로 상속되어 있습니다.

| 검토 사례 | 현재 선택 | 검토한 다른 접근 | 상태 |
|---|---|---|---|
| [충전소 입지](designs/ev-siting/README.md) | 자료 정합성·SQL/공간 조회·조사 shortlist | 시트, 조합 최적화, 수요 예측, ontology | 투자 입력 부족, 실행/투자 결론 보류 |
| [파트너 QA](designs/partner-qa/README.md) | FAQ baseline·권한 필터 검색·정책 체크 | 제한 LLM, 자율승인 agent, 지식그래프 | 실제 정책/질문 부족, 현장 효과 미검증 |

[충전소 빠른 초안](designs/ev-siting/BRIEF.md) · [QA 빠른 초안](designs/partner-qa/BRIEF.md) · [기술 용어](docs/technology-glossary.md) · [빠른 초안 평가](docs/study/quick-review.md)

[공식 자료 조사](docs/study/sources.md) · [정성 평가](docs/study/qualitative-review.md) · [부족분/기준 레포 반영](docs/study/findings.md) · [설계 playbook](docs/design-playbook.md)

```bash
pnpm install --frozen-lockfile
pnpm design:check designs/ev-siting/design.json
pnpm design:check designs/partner-qa/design.json
pnpm brief designs/ev-siting/design.json
pnpm brief designs/partner-qa/design.json
pnpm design:eval
pnpm test
pnpm design:start my-field-problem
# 새 draft는 작성 전까지 design:check에 실패하는 것이 정상입니다.
```

각 사례는 대안5개/요구사항5개/실패·변화 시나리오8개를 담습니다. 자동 검사는 구조/참조/traceability와 허위 outcome claim을 검사합니다. 좋은 방법을 선택했는지, 문서가 사실인지, 사용자가 가치 있다고 느끼는지는 자동 합격시키지 않습니다.

정성 평가는 동일 AI의 self review이며 독립 전문가/실제 사용자 평가가 아닙니다. EV 자료는 공개 공급 위치8건+합성 계산표, QA는 실제 규정이 아닌 작은 정책 mock입니다. 원격 vendor API/LLM과 제품 성능을 평가하지 않았습니다. 산업 현장의 검증된 문제 해결 능력이나 'Jarvis급' 완성을 주장하지 않습니다.

자체 자료/도구 MIT. 공개 데이터와 외부 자료 조건은 source 링크 및 THIRD_PARTY_NOTICES를 따릅니다.
