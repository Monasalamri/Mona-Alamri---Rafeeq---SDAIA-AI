Rafeeq Mini Labs · لابات رفيق المصغّر
Implementation · تطبيق

Mona Alamri · منى العمري








Rafeeq Mini is a cumulative, bilingual guided-engineering mini-capstone for building a safe delivery-support agent. Learners build the system in small stages, test each stage, and produce an auditable technical submission.

رفيق المصغّر مشروع هندسي تراكمي وثنائي اللغة لبناء مساعد آمن لدعم عمليات التوصيل. يتم بناء النظام على مراحل صغيرة مع اختبار كل مرحلة وإنتاج تسليم تقني قابل للتدقيق.

Release candidate 0.9.0-rc3: the project uses Google Colab Free CPU, LLM_MODE=stub, synthetic data, and no API key, GPU, terminal, PAT, or paid service.

مرشح الإصدار 0.9.0-rc3: يعمل المشروع على Google Colab المجاني باستخدام CPU والوضع LLM_MODE=stub وبيانات مصطنعة، دون الحاجة إلى مفتاح API أو GPU أو طرفية أو PAT أو خدمة مدفوعة.

Start · ابدأ

Clone or open the repository.

Open the cumulative notebook located at:
notebooks/Rafeeq_Mini_Capstone.ipynb

Run the notebook from the beginning in Google Colab using the standard CPU runtime.

Run C0_ENV_DOCTOR first and verify:
C0 = READY

Continue through the required cells in order.

Run the required validation and assessment checks.

Complete the final export through C29 and verify:
FINAL_EXPORT_CREATED

افتح المستودع.

افتح الدفتر التراكمي الموجود في:
notebooks/Rafeeq_Mini_Capstone.ipynb

شغّل الدفتر في Google Colab باستخدام بيئة CPU القياسية.

ابدأ بتشغيل C0_ENV_DOCTOR وتأكد من ظهور:
C0 = READY

تابع تشغيل الخلايا المطلوبة بالترتيب.

نفّذ اختبارات التحقق والتقييم المطلوبة.

أكمل التصدير النهائي من خلال C29 وتأكد من ظهور:
FINAL_EXPORT_CREATED

Detailed instructions are available in the learner guide.

تتوفر التعليمات التفصيلية في دليل المتدرب.

If the runtime disconnects, follow the recovery guide.

إذا انقطعت بيئة التشغيل، اتبع دليل الاستعادة.

Project scenario · سيناريو المشروع

A customer contacts the fictional delivery company Tawseel in Arabic or English to ask about an order or request a refund.

Rafeeq detects the intent and order ID, verifies ownership through a scoped tool, retrieves the active policy, delegates to the appropriate specialist, and records a redacted trace.

Refunds require a delay greater than two days. Amounts above SAR 500 require explicit human approval. Re-running a write remains safe through deterministic idempotency.

يتواصل عميل مع شركة التوصيل الافتراضية توصيل بالعربية أو الإنجليزية للسؤال عن طلب أو طلب استرداد.

يحدد رفيق النية ورقم الطلب، ويتحقق من الملكية عبر أداة مقيّدة، ويسترجع السياسة السارية، ويفوض المهمة إلى الوكيل المتخصص المناسب، ويسجل أثرًا منقحًا.

يشترط الاسترداد تأخرًا يزيد على يومين، وتتطلب المبالغ الأعلى من 500 ريال موافقة بشرية صريحة. وتظل إعادة عملية الكتابة آمنة باستخدام منع التكرار الحتمي.

Bilingual request · طلب ثنائي اللغة
Input guard · حارس المدخل
Thin supervisor · المنسق الخفيف
OrdersAgent
RefundAgent
MCP tools + scoped data · أدوات وبيانات مقيّدة
Policy + approval · السياسة والموافقة
Redacted trace + evidence · أثر منقح وأدلة
Three-day build · البناء خلال ثلاثة أيام
Day	Cells	Build outcome · ناتج البناء	Gate · البوابة
1 · Core & tools · النواة والأدوات	C0–C9	Typed state, bounded graph, ReAct, schemas, and a local MCP stdio connection · حالة محددة النوع، مخطط محدود، ReAct، مخططات أدوات، واتصال MCP محلي	C9_DAY1_GATE
2 · Memory & orchestration · الذاكرة والتنسيق	C10–C20	Session memory, scoped recall, policy retrieval, two specialists, typed delegation, planning, refund gate, and interrupt/resume · ذاكرة جلسية، استرجاع مقيّد، سياسات، وكيلان متخصصان، تفويض، تخطيط، بوابة استرداد، وتوقف/استئناف	C20_DAY2_GATE
3 · Security & evidence · الأمن والأدلة	C21–C29	Threat model, attack suite, guard repair, bounded reflection, traces, optimization, assessment, readiness, and safe export · نموذج تهديد، اختبارات هجوم، إصلاح الحواجز، انعكاس محدود، آثار، تحسين، تقييم، جاهزية، وتصدير آمن	C29_EXPORT_SAFETY_CHECK

The notebook contains 30 named sections and 14 learner TODOs. The remaining content provides runnable scaffolding, tests, hints, and evidence generation.

يحتوي الدفتر على 30 قسمًا مسمى و14 مهمة للمتدرب، بينما توفر بقية الأجزاء البنية التشغيلية والاختبارات والتلميحات وتوليد الأدلة.

Repository map · خريطة المستودع
Path	Purpose · الغرض
notebooks/	Cumulative Colab notebook · الدفتر التراكمي
src/rafeeq/	Typed state, graph, agents, memory, retrieval, guards, tracing, assessment · النواة البرمجية
mcp_server/	Local educational MCP stdio server · خادم MCP محلي
data/public/	Versioned synthetic datasets · بيانات مصطنعة ذات إصدار
tests/public/	Contract and safety tests · اختبارات العقود والسلامة
tests/schemas/	JSON contracts for state, traces, assessment, and export · عقود JSON
scripts/	Verification, assessment, demo, validation, and export tools · أدوات التحقق والتقييم والتصدير
reports/	Project, security, trace, assessment, and evidence artifacts · تقارير وأدلة المشروع
reference-results/	Versioned result-only comparison contracts · عقود مقارنة النتائج
recovery/	Restart and checkpoint guidance · إرشادات الاستعادة
docs/	Technical and learner documentation · التوثيق الفني ودليل المتدرب
Local verification · التحقق المحلي

The core verification path can be run without a paid service:

python scripts/doctor.py
python -m unittest discover -s tests/public -p "test_*.py" -v
python scripts/validate_notebook.py
python scripts/run_assessment.py
python scripts/validate_release.py


يمكن تشغيل مسار التحقق الأساسي دون خدمة مدفوعة. جميع البيانات المستخدمة تعليمية ومصطنعة، وعمليات الاسترداد محاكاة ولا تنفذ معاملات مالية حقيقية.

Final validation · التحقق النهائي

Before considering the submission complete:

Confirm the notebook exists at notebooks/Rafeeq_Mini_Capstone.ipynb.

Run the required validation checks.

Run C29 successfully.

Confirm all_passed: true.

Confirm missing_outputs: [].

Confirm secret_findings: [].

Confirm FINAL_EXPORT_CREATED.

Confirm the final generated artifacts are present in the repository.

قبل اعتبار التسليم مكتملًا:

تأكد من وجود الدفتر في notebooks/Rafeeq_Mini_Capstone.ipynb.

نفّذ اختبارات التحقق المطلوبة.

شغّل C29 بنجاح.

تأكد من ظهور all_passed: true.

تأكد من ظهور missing_outputs: [].

تأكد من ظهور secret_findings: [].

تأكد من ظهور FINAL_EXPORT_CREATED.

تأكد من رفع المخرجات النهائية المطلوبة إلى المستودع.

Safety boundary · حدود السلامة

Never enter real customer or trainee data, credentials, private links, tokens, or API keys.

Trusted identity and approval context are attached by the host runtime, never accepted as model-controlled tool arguments.

Traces store decisions, counters, codes, and short rationale only—never raw prompts or private chain-of-thought.

Read operations may receive one bounded retry for a transient failure; write operations are never retried automatically.

Hidden tests, solutions, private notes, and sensitive recovery checkpoints must not be published in the public repository.

لا تدخل بيانات حقيقية لعميل أو متدرب، أو بيانات دخول، أو روابط خاصة، أو رموزًا، أو مفاتيح API.

يضيف المضيف هوية العميل وسياق الموافقة الموثوق، ولا تقبلها الأدوات ضمن معاملات يتحكم بها النموذج.

تسجل الآثار القرارات والعدادات والرموز ومبررًا قصيرًا فقط، ولا تسجل الأوامر الخام أو سلسلة التفكير الخاصة.

قد تعاد عمليات القراءة مرة واحدة فقط عند فشل عابر، ولا تعاد عمليات الكتابة تلقائيًا.

يجب عدم نشر الاختبارات الخفية أو الحلول أو الملاحظات الخاصة أو نقاط الاستعادة الحساسة في المستودع العام.

Educational use · الاستخدام التعليمي

Educational simulation only · محاكاة تعليمية فقط.

Learner reuse is governed by the applicable course-use terms in COURSE_USE_PERMISSION.md.

يخضع استخدام المتدرب للشروط المحددة في COURSE_USE_PERMISSION.md.
