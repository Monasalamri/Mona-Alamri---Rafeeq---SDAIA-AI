Rafeeq Mini Labs · لابات رفيق المصغّر

Advanced Agentic AI Systems Engineering · هندسة أنظمة الذكاء الاصطناعي التوكيلي المتقدمة
Release Candidate · 0.9.0-rc3










🎯 Project Overview · نظرة عامة

Rafeeq Mini · رفيق المصغّر هو مشروع هندسة تطبيقية موجهة وتراكمية وثنائية اللغة صُمم كـ mini-capstone لدورة:

Advanced Agentic AI Systems Engineering

يبني المتدرب خلال ثلاثة أيام مساعدًا آمنًا لدعم عمليات التوصيل، بدءًا من النواة البرمجية والأدوات، مرورًا بالذاكرة والتنسيق بين الوكلاء، وانتهاءً بالأمن والأدلة والتصدير النهائي.

المشروع لا يهدف إلى إنشاء نظام إنتاجي مفتوح النطاق؛ بل يقدم محاكاة هندسية تحت الإشراف تركّز على بناء الأنظمة التوكيلية بصورة قابلة للاختبار، والتدقيق، وإعادة التشغيل.

English

Rafeeq Mini is a cumulative, bilingual, guided-engineering mini-capstone for the three-day Advanced Agentic AI Systems Engineering course.

Learners progressively build a safe delivery-support agent, validate each stage through explicit gates and evidence, and produce an auditable GitHub submission.

The project is intentionally designed as a supervised engineering simulation, not as a production deployment or open-ended software assignment.

🚀 Current Release · الإصدار الحالي

Release Candidate: 0.9.0-rc3

The repository currently provides:

Automated repository validation.

GitHub Actions checks.

GitHub Pages learner portal.

Versioned reference-result contracts.

A cumulative Google Colab notebook.

Public contract and safety tests.

Safe evidence generation.

Final submission validation.

Synthetic data only.

LLM_MODE=stub.

Google Colab Free CPU support.

No API key required.

Acceptance note: automated repository, CI, and Pages checks are verified. Clean-account hosted-Colab acceptance remains a manual instructor/learner verification step.

🧭 Start Here · ابدأ من هنا
1. GitHub Account · حساب GitHub

Sign in to a personal GitHub account and verify your email.

سجّل الدخول إلى حساب GitHub شخصي ووثّق بريدك الإلكتروني.

2. Create the Repository · إنشاء المستودع

Create a new public repository, add a clear GitHub About description, and create only:

LEARNING_PROGRESS.md


using the approved safe template.

3. Open the Notebook · فتح الدفتر

Open Rafeeq Mini in Google Colab

Then select:

File → Save a copy in Drive

4. Run the Environment Doctor · فحص البيئة

Select the standard CPU runtime and run:

C0_ENV_DOCTOR


Expected result:

C0 = READY

5. Follow the Gates · اتبع البوابات

Complete the notebook sequentially from C0 through C29.

After C9 and C20:

Update only the safe progress log.

Create a meaningful documentation commit.

After C29:

FINAL_EXPORT_CREATED


Then upload the clean submission and wait for:

Learner submission quality → GREEN

📚 Learner Resources · موارد المتدرب

Learner Portal

Learner Guide

Recovery Guide

Reference Comparison

Reference Results

Assessment Rubric

SDAIA Administrative Requirements

إذا انقطعت بيئة التشغيل، استخدم دليل الاستعادة بدل إعادة المشروع بالكامل.

🔐 Privacy & Identity · الخصوصية والهوية

Public repository files must contain only the assigned learner_id or GitHub username.

Do not place the following in public files:

Real name.

Personal email.

Phone number.

National ID.

Credentials.

API keys.

Private links.

Real customer or trainee data.

يجب وضع البيانات الشخصية فقط في نموذج التسليم الخاص الذي توفره المدربة.

إذا كانت سياسة جهة العمل أو المؤسسة تمنع المستودعات العامة، يجب إبلاغ المدربة قبل اليوم الأول واستخدام مسار التسليم الخاص المعتمد.

🧩 Project Scenario · سيناريو المشروع

يتعامل Rafeeq مع عميل يتواصل بالعربية أو الإنجليزية مع شركة التوصيل الافتراضية Tawseel · توصيل.

يمكن للعميل:

الاستفسار عن طلب.

طلب استرداد.

تقديم الطلب باللغة العربية أو الإنجليزية.

يقوم النظام بتطبيق سلسلة واضحة من الضوابط:

Customer Request
       ↓
Input Guard
       ↓
Thin Supervisor
       ↓
Intent + Order Detection
       ↓
Ownership Verification
       ↓
Scoped Policy Retrieval
       ↓
Specialist Agent
       ↓
Approval / Safety Gate
       ↓
Bounded Tool Execution
       ↓
Redacted Trace
       ↓
Evidence

Refund Safety

لا يتم تنفيذ الاسترداد إلا عند تحقق شرط التأخر لأكثر من يومين.

المبالغ التي تتجاوز SAR 500 تتطلب موافقة بشرية صريحة.

عمليات الكتابة لا تتم إعادة محاولتها تلقائيًا.

إعادة تشغيل عملية الكتابة تبقى آمنة من خلال deterministic idempotency.

🏗️ System Architecture · معمارية النظام
flowchart TB
    A["Bilingual Request · طلب ثنائي اللغة"]
    --> B["Input Guard · حارس المدخل"]

    B --> C["Thin Supervisor · المنسق الخفيف"]

    C --> D["OrdersAgent"]
    C --> E["RefundAgent"]

    D --> F["Scoped MCP Tools + Data"]
    E --> G["Policy + Approval Gate"]

    G --> F

    F --> H["Redacted Trace + Evidence"]


المبدأ الأساسي هو إبقاء المنسق Thin Supervisor قدر الإمكان، مع فصل المسؤوليات بين التحقق، والسياسات، والوكلاء المتخصصين، والأدوات، والأدلة.

📅 Three-Day Engineering Path · المسار الهندسي لثلاثة أيام
Day	Cells	Engineering Outcome	Gate
Day 1 — Core & Tools	C0–C9	Typed state, bounded graph, ReAct, schemas, local MCP stdio connection	C9_DAY1_GATE
Day 2 — Memory & Orchestration	C10–C20	Session memory, scoped recall, policy retrieval, specialists, typed delegation, planning, refund gate, interrupt/resume	C20_DAY2_GATE
Day 3 — Security & Evidence	C21–C29	Threat model, attack suite, guard repair, bounded reflection, traces, measured optimization, scorecard, readiness, safe export	C29_EXPORT_SAFETY_CHECK
🧪 Core vs Stretch · المسار الأساسي والتوسّع
Core · المسار الأساسي

المتطلبات الإلزامية هي:

14 Learner TODOs.

C0–C29 بالترتيب.

بوابات الأيام الثلاث.

التقارير والأدلة المطلوبة.

متطلبات SDAIA الإدارية.

GitHub upload نظيف.

نجاح GitHub Actions.

Stretch · مسار التوسع

الامتدادات اختيارية فقط عندما يتم تحديدها أو الإعلان عنها من المدربة.

ولا يمكن لأي امتداد أن:

يستبدل بوابة أساسية فاشلة.

يعوض نقصًا في المتطلبات الأساسية.

يضعف تجربة المتدرب المبتدئ.

📊 Assessment & SDAIA Requirements · التقييم ومتطلبات سدايا

المشروع يمثل تقييم الدورة كاملًا:

100 / 100

ويتضمن محور GitHub Delivery الحالي 15 درجة:

Requirement	Points
Clear & comprehensive repository description	2
Professional README: idea, run, and use	2
Appropriate technical documentation	2
Meaningful & safe Git history	2
Training-program reference	1
Working SDAIA Academy GitHub link	1
Administrative subtotal	10
Technical delivery evidence	5
Total GitHub delivery area	15

Read the full SDAIA administrative requirements

Read the complete 100-point assessment rubric

Passing threshold: 70/100, with every non-compensable gate also required to pass.

📦 Final Submission · التسليم النهائي

The final learner package includes:

reports/
├── PROJECT_REPORT.md
├── SECURITY_ASSESSMENT.md
├── trace.jsonl
├── assessment_results.json
├── monitoring_dashboard.png
├── submission_manifest.json
└── EVIDENCE_CARD.md

LEARNING_PROGRESS.md


Additionally:

Clean submission ZIP.

Deployable dependency-light Python package.

Local MCP server.

Generated evidence.

Validated assessment results.

Evidence Card

reports/EVIDENCE_CARD.md is completed from the provided template after extracting the C29 package.

It contains one concise evidence card for each day and serves as a required instructor-assessment record.

🔎 Validated Reference Results · النتائج المرجعية

Complete your own attempt first.

Then compare the evidence generated by your notebook, not your implementation, against the versioned reference contracts.

The comparison focuses on stable behavior such as:

Gate results.

Case IDs.

Safety decisions.

Execution bounds.

Required artifacts.

The comparison intentionally ignores values that naturally vary between runs, including:

Timestamps.

Generated IDs.

Paths.

Hashes.

File sizes.

Latency.

Open the visual comparison page

🛡️ Safety Boundary · حدود السلامة

The project follows explicit safety boundaries:

Never enter real customer or trainee data.

Never commit credentials, tokens, private links, or API keys.

Trusted identity and approval context are attached by the host runtime.

Model-controlled tool arguments cannot supply trusted identity or approval context.

Traces contain decisions, counters, codes, and short rationale only.

Raw prompts and private chain-of-thought are never stored.

Read operations may receive one bounded retry for transient failure.

Write operations are never automatically retried.

Hidden tests, solutions, instructor notes, and real recovery checkpoints remain outside the public repository.

🧪 Local Verification · التحقق المحلي

The core verification path requires no installation:

python scripts/doctor.py

python -m unittest discover \
  -s tests/public \
  -p "test_*.py" \
  -v

python scripts/validate_notebook.py

python scripts/run_assessment.py

python scripts/validate_release.py


All project data is synthetic, and refund operations are simulations only; no real financial transaction is executed.

🗂️ Repository Structure · بنية المستودع
Path	Purpose
notebooks/	Cumulative Colab notebook and cell map
src/rafeeq/	Typed state, graph, agents, memory, retrieval, guards, tracing, assessment
mcp_server/	Dependency-free educational MCP stdio server
data/public/	Versioned synthetic learner datasets
tests/public/	Learner-visible contract and safety tests
tests/schemas/	JSON contracts
scripts/	Doctor, gates, assessment, demo, validation, safe export
reports/templates/	Bilingual evidence and report templates
reference-results/	Versioned result-only comparison contracts
recovery/	Recovery and checkpoint guidance
docs/	Bilingual learner documentation
📤 Submission & Confirmation · التسليم والتأكيد
Item	Instruction
Deadline	Provided by the instructor during the course
Hand-in	Submit the public repository URL and final commit URL through the instructor-provided private form
Automated verification	Actions → Learner submission quality must show a green check
Receipt	Instructor/form confirmation is the authoritative receipt
Resubmission	Preserve history, repair, regenerate affected evidence through C29, create a new commit, verify Actions, then submit the new commit URL according to the instructor's policy

A green Actions check confirms automated verification; it is not itself the submission receipt.

🆘 Technical Help · المساعدة التقنية

For public, sanitized technical questions:

Open the bilingual Lab Help Issue Form

Do not use public Issues for:

Credentials.

Vulnerabilities.

Private links.

Personal data.

Grade disputes.

Private submission information.

For sensitive matters, follow SECURITY.md and the instructor's private communication channel.

👩‍🏫 Instructor · المدربة
Meaad Al-Marri · ميعاد المري

SDAIA Academy on GitHub
 is provided strictly as an external reference.

This repository does not use an official institutional logo and does not claim institutional endorsement, approval, or ownership.

📌 Educational Use · الاستخدام التعليمي

Educational simulation only · محاكاة تعليمية فقط

Learner reuse is governed by the limited:

COURSE_USE_PERMISSION.md

It is not a broad open-source license.

⭐ Engineering Principles · مبادئ المشروع

Build small. Test every stage. Bound every action. Record only what is needed. Export evidence, not secrets.

ابنِ على مراحل صغيرة، اختبر كل مرحلة، قيّد كل إجراء، سجّل الحد الأدنى اللازم، وصدّر الأدلة دون الأسرار.

هذا هو المبدأ الذي يجمع بين الجانب الهندسي، والأمان، وقابلية التدقيق، وجودة التسليم في Rafeeq Mini.
