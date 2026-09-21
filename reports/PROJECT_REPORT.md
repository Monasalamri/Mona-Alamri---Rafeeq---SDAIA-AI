# Rafeeq Mini Project Report | تقرير مشروع رفيق ميني

- Training program | البرنامج التدريبي: Advanced Agentic AI Systems Engineering · هندسة أنظمة الذكاء الاصطناعي التوكيلية المتقدمة
- SDAIA Academy GitHub external reference | مرجع أكاديمية سدايا على GitHub: https://github.com/SDAIAAcademy

## Run and outcome | التشغيل والنتيجة

- Assessment run ID | معرّف تشغيل التقييم: `run-763d474f9e634b02`
- Generated UTC | وقت الإنشاء: 2026-09-21T18:28:26.350539+00:00
- Decision | القرار: READY
- Evidence cells | خلايا الأدلة: C9, C20, C23, C26, C27, C28

## Gates | البوابات

| Gate | Passed |
|---|---:|
| Day 1 gate | True |
            | Day 2 gate | True |
            | Security + learner regression gate | True |
            | Readiness gate | True |

## Public evidence and metrics | الأدلة والمقاييس العامة

- Functional case IDs | معرّفات الحالات الوظيفية: EVAL-AR-01, EVAL-AR-02, EVAL-AR-03, EVAL-AR-04, EVAL-EN-01, EVAL-EN-02, EVAL-EN-03, EVAL-EN-04
- Security case IDs | معرّفات الحالات الأمنية: SEC-01, SEC-02, SEC-03, SEC-04, SEC-05, SEC-06, SEC-07, SEC-08
- Functional accuracy | الدقة الوظيفية: 100%
- Security pass rate | نسبة اجتياز الأمن: 100%
- Median latency | وسيط الزمن: 1.165 ms
- Trace records | سجلات التتبع: 547
- Trace parent integrity | سلامة روابط التتبع: True
- Runtime | بيئة التشغيل: offline deterministic stub on free CPU

## Architecture | المعمارية

Thin supervisor, OrdersAgent, RefundAgent, scoped memory, current-policy retrieval, MCP stdio tools, human approval gate and redacted traces.

منسق خفيف، وكيلا الطلبات والاسترداد، ذاكرة محددة النطاق، استرجاع السياسة السارية، أدوات MCP عبر stdio، بوابة موافقة بشرية، وتتبعات منقحة.

## Learner security evidence | دليل أمن المتدرب

- New threat case metadata | بيانات الحالة الجديدة: `{"asset": "Refund write", "case_id": "L-SEC-02", "control": "Trusted approval metadata + amount gate", "expected_flag": "approval_bypass", "payload_length": 268}`
- Weak local baseline exposed | كشف خط الأساس الضعيف: True
- Repaired guard regression passed | نجاح اختبار الحاجز المُصلح: True

## Optimization evidence | دليل التحسين

- Optimization | التحسين: current_policy_cache
- Before | قبل: 2.207 ms / 500 iterations
- After | بعد: 0.172 ms / 500 iterations
- Cache hits / misses | إصابات / إخفاقات التخزين: 499 / 1
- Learner trade-off and guardrail | مقايضة وضابط المتدرب: Trade-off: caching cut lookup time from 2.207ms to 0.172ms over 500 calls (499 hits / 1 miss), but the cache is now keyed only on (locale, category, version) — if the active policy is updated mid-run without bumping the version string, stale policy data could be served until the cache is cleared. Guardrail: never widen the cache key to include customer_id, order_id, or any per-customer field, and call invalidate_policy_cache() on every policy publish or bump _active_version so stale data cannot 

## Residual risks and limitations | المخاطر المتبقية والقيود

Synthetic public data only; no real delivery, payment or customer system; production identity, policy, secrets and operations are out of scope.

بيانات عامة اصطناعية فقط؛ لا اتصال بأنظمة توصيل أو دفع أو عملاء حقيقية؛ والهوية والسياسات والأسرار وعمليات الإنتاج خارج النطاق.

The deterministic stub does not measure live-model quality, rate limits or provider cost. Local approval and memory stores are training simulations, not durable production controls.

لا يقيس النمط الحتمي جودة نموذج حي أو حدود المعدل أو تكلفة المزود، كما أن مخازن الموافقة والذاكرة المحلية محاكاة تدريبية وليست ضوابط إنتاج دائمة.
