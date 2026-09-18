# Production Plan Research Note

**Retrieved:** 2026-09-18

This note records evidence used to improve the planning contract. It is evidence for the additions below, not a claim that the cited providers or practices are interchangeable.

## Sources and verified observations

1. [Google SRE Launch Coordination Checklist](https://sre.google/sre-book/launch-checklist/)
   - Verified observations: launch review covers architecture, capacity and launch spikes, load tests, failover, monitoring the monitoring, backups/disaster recovery, security, repeatable releases, canaries/staged rollout, 10x growth, external dependency degradation, SOPs, and change windows.
   - Implementation implication: make launch readiness, capacity/load evidence, resilience drills, monitored monitoring, dependency fallback, staged rollout, pause criteria, growth horizon, and change windows explicit plan fields.
2. [AWS Well-Architected Reliability Pillar](https://docs.aws.amazon.com/wellarchitected/latest/reliability-pillar/welcome.html)
   - Verified observations: reliability guidance emphasizes strong foundations, resilient architecture, consistent change management, and proven recovery processes; reliability is one pillar alongside operational excellence, security, performance, cost, and sustainability.
   - Implementation implication: preserve cross-domain planning and require evidence for change and recovery rather than treating reliability as an isolated availability checkbox.
3. [Microsoft Azure Well-Architected Reliability](https://learn.microsoft.com/en-us/azure/well-architected/reliability/)
   - Verified observations: guidance covers identifying flows, failure-mode analysis, reliability targets, monitoring, redundancy/scaling/self-healing, testing and drills, disaster recovery, maturity, and trade-offs.
   - Implementation implication: add explicit failure-mode, dependency, monitoring, target, drill, and trade-off evidence to domains and acceptance checks.
4. [W3C WCAG 2 Overview](https://www.w3.org/WAI/standards-guidelines/wcag/)
   - Verified observations: WCAG 2.2 is the latest published version; conformance uses testable success criteria and levels A, AA, and AAA; it applies to dynamic, mobile, and AI web content.
   - Implementation implication: require web plans to name the WCAG version and conformance level, recommending WCAG 2.2 AA and requiring a documented exception for another target.

## Scope and evidence handling

These sources inform planning requirements, but project evidence still determines applicability, targets, ownership, and approval. Mark unsupported project facts `UNKNOWN` or `DEFERRED` under the existing rules; do not substitute provider guidance for measured capacity, executed drills, or product-specific accessibility evidence.
