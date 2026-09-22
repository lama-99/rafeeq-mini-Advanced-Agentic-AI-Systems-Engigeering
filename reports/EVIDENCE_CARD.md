# Required evidence cards · بطاقات الأدلة الإلزامية

## Submission identity · هوية التسليم

| Field | Entry |
|---|---|
| Public learner ID · معرف المتدرب العام | `lama-99` |
| Assessment `run_id` · معرف تشغيل التقييم | `run-61255a3b42c24bd2` |
| Final clean run date (UTC) · تاريخ التشغيل النظيف | `2026-09-22` |

## EV-D1 · Day 1 core and tools · نواة اليوم الأول وأدواته

| Field | Entry |
|---|---|
| Testable claim · الادعاء القابل للاختبار | Day 1 agent core, state controls, tool scope, and public tests complete successfully. |
| Cell/gate · الخلية/البوابة | `C9 / C9_DAY1_GATE` |
| Public case or metric · الحالة العامة أو المقياس | `public_tests_passed = true` |
| Expected result · النتيجة المتوقعة | Day 1 public tests and learner checks pass. |
| Actual result · النتيجة الفعلية | All Day 1 public tests passed and learner checks 1–5 completed successfully. |
| Status · الحالة | `PASS` |
| Public artifact path · مسار الدليل العام | `day1_results.json` |
| Reproduce · إعادة التنفيذ | 1. Open the cumulative notebook. 2. Run Day 1 cells in order. 3. Run `C9_DAY1_GATE`. 4. Verify `all_passed = true`. |

Safe observation · الملاحظة الآمنة: Agent state and tool-scope checks passed; the Day 1 gate reported `public_tests_passed = true`, `learner_checks_complete = true`, and `all_passed = true`.

## EV-D2 · Day 2 memory and orchestration · ذاكرة اليوم الثاني وتنسيقه

| Field | Entry |
|---|---|
| Testable claim · الادعاء القابل للاختبار | Day 2 scoped memory, supervisor routing, delegation, refund policy, and approval controls complete successfully. |
| Cell/gate · الخلية/البوابة | `C20 / C20_DAY2_GATE` |
| Public case or metric · الحالة العامة أو المقياس | `public_tests_passed = true` |
| Expected result · النتيجة المتوقعة | Day 2 memory, routing, refund-gate, and reflection tests pass. |
| Actual result · النتيجة الفعلية | All Day 2 public tests passed and learner checks 6–10 completed successfully. |
| Status · الحالة | `PASS` |
| Public artifact path · مسار الدليل العام | `day2_results.json` |
| Reproduce · إعادة التنفيذ | 1. Run Day 2 cells in order. 2. Run the memory and orchestration checks. 3. Run `C20_DAY2_GATE`. 4. Verify `all_passed = true`. |

Safe observation · الملاحظة الآمنة: Scoped memory and supervisor routing passed; refund requests above SAR 500 require human approval, and the Day 2 gate reported `all_passed = true`.

## EV-D3 · Day 3 security and evidence · أمن اليوم الثالث وأدلته

| Field | Entry |
|---|---|
| Testable claim · الادعاء القابل للاختبار | The final system passes the security suite, functional assessment, trace checks, and C29 export-safety checks. |
| Cell/gate · الخلية/البوابة | `C29 / C29_EXPORT_SAFETY_CHECK` |
| Public case or metric · الحالة العامة أو المقياس | `8/8 security cases passed; 8/8 functional cases passed` |
| Expected result · النتيجة المتوقعة | Security and functional cases pass with zero unauthorized writes and all critical gates passing. |
| Actual result · النتيجة الفعلية | 8/8 security cases and 8/8 functional cases passed; unauthorized writes = 0; all critical gates passed; final export precheck passed. |
| Status · الحالة | `PASS` |
| Public artifact path · مسار الدليل العام | `reports/assessment_results.json` |
| Reproduce · إعادة التنفيذ | 1. Run Day 3 security and assessment cells. 2. Verify the security and functional results. 3. Run the C29 export-safety check. 4. Verify all critical gates and final precheck are true. |

Safe observation · الملاحظة الآمنة: Security controls blocked or safely handled the tested attack cases; 8/8 security cases passed, unauthorized writes remained 0, and the final C29 export-safety precheck passed.

## Required redaction declaration · إقرار التنقيح الإلزامي

- [x] I used only the instructor-assigned `learner_id` or GitHub username. · استخدمت `learner_id` الذي تقدمه المدربة أو اسم مستخدم GitHub فقط.
- [x] All identifiers are supplied synthetic fixtures. · جميع المعرفات من الحالات المصطنعة المرفقة.
- [x] No password, token, API key, cookie, private link, or environment value appears. · لا توجد كلمة مرور أو رمز وصول أو مفتاح API أو Cookie أو رابط خاص أو قيمة بيئة.
- [x] No real person, customer, employee, order, payment, support, or trainee data appears. · لا توجد بيانات حقيقية لشخص أو عميل أو موظف أو طلب أو دفعة أو دعم أو متدرب.
- [x] No copied solution, instructor note, answer key, scoring rule, hidden test, or private chain-of-thought appears. · لا يوجد حل منسوخ أو ملاحظة مدربة أو مفتاح إجابة أو قاعدة درجات أو اختبار خفي أو تفكير داخلي خاص.
- [x] Every declared `PASS` matches an actual final-run result. · كل نتيجة `PASS` معلنة تطابق نتيجة فعلية من التشغيل النهائي.
