# Innovorix

## Executive Product Document

## Institute Management Platform

Innovorix is a complete institute management platform built to run the daily, monthly, and yearly operations of an educational institute from one connected system.

It is designed for institutes that want to replace scattered manual work, disconnected staff coordination, repeated data entry, paper-heavy fee handling, and weak parent visibility with one organized digital workflow.

This document is intentionally written for:

- institute owners
- principals
- directors
- campus heads
- branch managers
- operations teams
- admissions teams
- finance teams
- marketing teams
- sales teams
- implementation teams

This is not only a technical README.

This is also a product understanding document.

It explains:

- what Innovorix is
- what modules are included
- what each role gets
- what each page does
- what hidden strengths exist inside the workflows
- what makes the product attractive for institutes
- what makes it practical for daily operations
- what makes it useful for parents, teachers, finance staff, and institute leadership
- what makes it strong on desktop and mobile

---

## One-Line Positioning

Innovorix is an all-in-one institute ERP and operations platform for academics, fees, attendance, communication, results, promotion, library work, leave handling, and multi-role day-to-day management.

---

## Short Product Pitch

An institute does not only need software that stores records.

It needs software that helps people work faster, make fewer mistakes, follow clearer processes, and communicate better.

Innovorix is built around that practical goal.

Instead of giving every department a disconnected tool, it connects the major operational areas of an institute:

- admissions
- student records
- guardian records
- staff records
- class and timetable planning
- attendance
- assessments
- exams and marks
- marksheets
- fees and payment proof review
- fee defaulters
- promotion
- communication
- library circulation
- notifications
- mobile access

The WhatsApp Gateway used by the Baileys service also reuses the shared SMTP flow for signup verification and password reset emails, so gateway users can recover access without a separate mail path.
The gateway signup and reset screens now both require password confirmation so the user can catch typos before submitting.

<details>
<summary><b>Public website: search indexing and advertising</b></summary>

The sitemap lists public content only. MCQ category URLs come from the published public question bank, so an unseeded category is not advertised to crawlers. Authentication, partner account pages, payments and institute app pages stay outside the sitemap and are blocked in robots.txt. Public pages use a single HTTPS canonical on innovorix.com, including separate canonical URLs for paginated MCQ questions.

The shared page layout loads analytics but does not load AdSense. Future advertising belongs only on blog articles and public MCQ content pages. Pricing, signup and payment flows have no advertising loader or placement in the repository. External Google Tag Manager tags and AdSense account settings need a separate owner review.

</details>

<details>
<summary><b>New institutes: short signup and the Get Started guide</b></summary>

Signup asks for five things only: school name, your name, mobile, email and password. After the email code, the new admin is signed in straight away and lands on **Get Started**; there is no second login page. The address, school phone, type of institute, time zone and fee currency are filled in on the first step of Get Started. Time zone and currency are guessed from where the person signed up and shown as a one-line summary with a **Change** button.

The sign-in form follows the natural keyboard order: Email, Password, password visibility, then Forgot Password. The recovery link appears below the password field.
Parallel session checks cannot replace the security cookie used by a sign-in. If
the token changes, sign-in refreshes it once automatically. Persistent failures
explain that cookies must be allowed and leave the form ready to try again.

Get Started has five setup steps: create your account, add institute details, add teachers, add classes and sections, and add students. Each step ticks itself from what the school actually has (for example, at least one class), so a step done from its own page shows as done here too. Hovering a tick says why it is ticked. Only the next step is open, with one button; a step that needs an earlier one says so and links to it. Adding teachers can be skipped and put back. Fee creation and attendance are ordinary operational tasks and are not required for setup. Every step has a **Show me how** link that opens its Help Center guide in the side panel.

While the guide is on, the admin dashboard shows the same list in place of the Institute Health score, the menu shows only the setup pages with the rest folded under **More tools** (sorted under the same headings as the full menu), and a page opened from a setup step shows a **Back to setup steps** bar. When every step is done or skipped the list says the school is ready and offers a button to dismiss it. **Hide this list** switches it off early; it can be reopened from the Help Center guide _First-Time Setup Order_.

Only institutes that sign up get the guide (the school preference `onboarding.showSetupGuide` is set to true at signup). Schools that existed before it, and branches added later, never see it unless an admin opens Get Started on purpose.

</details>

<details>
<summary><b>The menu: groups by kind of work</b></summary>

A long menu folds into groups so a principal is not faced with 26 links: **Attendance** (student and staff attendance, leaves), **Academics** (classes, assessments, exams, marksheets, MCQs, promotion), **Reports** (academic progress, merit list, risk detection), **Fees** (fees, who hasn't paid, payment proofs, instalment requests), **People** (students and guardians, staff) and **Messages** (WhatsApp, communications). Dashboard and Calendar stay at the top. **Help Center** and **Report an Issue** sit at the bottom beside **Settings**.

Page controls keep a fixed footprint on desktop. Hover or keyboard focus reveals their wording without moving neighbouring buttons or wrapping the toolbar. Touch screens keep the wording visible. Attendance uses a compact date control and puts Download report at the right edge; its help is available from the top bar. Cards use compact P/A/L counts when leave is present, and empty classes stay visible without opening a register. Save confirmations distinguish saved attendance from guardian messages that are still waiting.

Desktop headers place the title on the left and their controls on the right of the same row when space permits. Students and Guardians keep the title, flexible search and actions beside each other. The campus studio keeps its own layout, and phone headers retain their existing arrangement. Risk Detection offers 7 days, 30 days, 90 days and 6 months when available, without a Year button.

- **Short menus stay flat.** Folders appear only when someone has 15 or more pages. Teachers, students, guardians, accountants and librarians have fewer, so their menu is a plain list.
- **The same groups on every plan.** A plan, a switched-off module or a missing permission only removes pages. A group left with one page shows as that page, and an empty group disappears, so upgrading adds pages to groups the principal already knows instead of moving anything.
- **Open groups are remembered** per person in that browser. Landing on a page inside a closed group opens it, and a closed group holding the current page is highlighted. Only the closest menu entry is highlighted (Who Hasn't Paid, not Fees as well).
- **Folded sidebar:** a round handle on the sidebar's right edge folds it to icons and back (so do the header button and Ctrl+B). Folded, each group shows as its icon, its tooltip lists what is inside, and clicking it opens the sidebar on that group.
- **Phone:** the Menu page shows the same groups as headed sections, then a **Help and support** section.
- **Tablet (768 to 1023 px wide):** the sidebar starts folded to icons so pages get the width their layouts expect. Opened, it floats over the page instead of squeezing it, and it folds away again after picking a page or tapping beside it. Widening the window to laptop size opens it again.
- **Settings > Roles & permissions** sorts its pages under the same groups.
- **Settings > WhatsApp messages** is the one place for what goes out on WhatsApp: absences, card attendance, new fees, fee reminders and timetable changes.
- **Minimum attendance** on Settings > Attendance is one number used by the low attendance badges, Risk Detection and student warnings.
- **Settings > Advanced settings** holds the finer controls most institutes never change, grouped as Attendance, Messages, Student warnings and WiFi attendance. Each group has **Reset to recommended**, each changed setting shows a **Changed** label with the recommended value, and the usual pages link to the right group. A setting that needs another one stays visible but off, and names the setting it needs. Upload timing for card scans and the WiFi matching numbers are chosen by the app; "How strict the room check is" (Relaxed, Normal, Strict) sets the WiFi numbers.

The groups are defined once in `src/lib/access/page-groups.ts`.

</details>

<details>
<summary><b>Urdu (اردو): the menu and the Help Center</b></summary>

Anyone signed in can read the app's explanations in Urdu. **اردو میں دیکھیں** in the account menu (and in the top bar on Help pages, where the Help button would be) switches; **View in English** switches back. The choice is saved on that device for a year, and the server renders the chosen language, so nothing flips after a page loads.

**In Urdu:** the menu on every screen size (sidebar, the phone's bottom bar, the Menu page, menu hints, counts and the Trial tag), the header's Help button, account menu and role badge, every Help Center guide (all 44) and the Help side panel on each page.

**Parent and student pages in Urdu:** the dashboard (greeting, pending fees and leaves, each child's attendance and results, tips), the fees page (vouchers, statuses, instalment plans, the payment proof form and its messages) and attendance (each child's card, the calendar with Urdu month and weekday names, monthly and overall totals, the student's WiFi check explanations). Dates read as 10 دسمبر 2026; names, fee titles and class labels the institute typed stay as typed.

**Still English:** staff pages (forms, tables and buttons for admins, teachers and accountants), printed vouchers and report cards, notifications, WhatsApp messages and the public website. That is why the Urdu guides name buttons in English, exactly as the screen shows them, and menu entries in Urdu, exactly as the Urdu menu shows them. For example, the attendance guide says: `طلبہ کی حاضری` کھولیں ... `Take attendance` دبائیں۔ A note at the top of the Help Center explains this to the reader.

**How it reads:** the Urdu Pakistani offices actually use, not a word-for-word translation: رزلٹ کارڈ for marksheets, فیس واؤچر (چالان), ڈیٹ شیٹ, کلاس ٹیچر, پیریڈ, سیٹنگز. Digits stay 0-9 and dates use Urdu month names (3 دسمبر 2026). Urdu is set in Nastaliq (Noto Nastaliq Urdu, self-hosted, downloaded only when Urdu is on screen). The phone's bottom bar uses shorter names where a slot is narrow (ریکارڈ, ہوم ورک).

**Right to left:** in Urdu the whole signed-in app reads right to left: the sidebar sits on the right, rows, tables, forms, dialogs, menus and toasts mirror, and forward and back arrows point the other way. Layout that is data stays left to right: the timetable grid (pixel-identical in both languages), charts, printed vouchers and student cards, and the 3D campus building. English that is not translated yet keeps its own letter order, so punctuation and phone numbers stay readable, and lines up on the right with the rest of the page; emails, phone numbers and passwords are typed left to right. The public website stays English and left to right. English mode was checked pixel for pixel against screenshots taken before the change.

**The English guides were corrected at the same time.** They had drifted from the screens: renamed buttons (Take attendance, Generate new fee, Send notifications, View Voucher, Print or save PDF), renamed menu entries (Student Attendance, All Fees, Who Hasn't Paid, Move to Next Class), renamed Settings sections (Institute details, Login emails and IDs, Reminders and late fees, Student and staff tags) and wrong statements about subjects (they have Manage subjects), sections (a new class takes A, B, C at once), the attendance rule (class teacher first, first-period teacher only as fallback) and part payments.

Words live in `src/lib/i18n` (language, menu, header) and `src/lib/help/ur` (guides). `urdu-help-content.test.ts` fails when an Urdu guide has a different number of steps from English, drops a button or menu name the English quotes, or quotes a name that is neither a real Urdu menu entry nor on the English screen.

</details>

<details>
<summary><b>Class teachers, smarter student imports and counter receipts</b></summary>

**Class teachers.** Each class card on the Classes page shows who the class teacher of each section is ("Class teachers: 1 of 2 sections", with the names on hover) and a **Pick class teacher** / **Change** button. The class teacher takes that section's attendance. A section without one falls back to the old rule: the teacher of its first period in the timetable. A teacher who is class teacher of nothing sees "You're not a class teacher yet" on Attendance, with what to ask the principal.

**Student import.** The importer takes the school's own Excel (.xlsx) or CSV list. Usual headings such as Student Name, Father Name, Class, Section and Contact No are understood, so the file no longer has to be rebuilt in the sample format. A class written as "5" joins an existing "Class 5" instead of creating a second one. Validation says up front when the plan's student limit will stop some rows, and those rows create no guardian. The same father name with two different phone numbers is treated as two people, and the same name with the same phone as one family, so neither is asked about; the remaining questions can be answered all at once with **Mark all as different people** or **Mark all as the same family**. When the background import finishes, the person who started it gets a notification with how many were added and the main reasons for any that were not.

**Required student gender.** Gender stays selected when a newly admitted student is edited immediately. Spreadsheet imports require a gender for every student. Missing or unrecognized values appear with the row number and student name so an administrator can choose each value during validation, including a file with no gender column. Confirmed choices are preserved in background processing and retries; names never determine gender.

**Name-only guardians.** Standalone guardian creation, admission and Add Guardian in student editing share the same checks. Only the name is required; phone, national identity number and personal email are optional. Adding a new guardian while editing creates and links that person together, preserves any previously linked guardian, and updates both lists immediately. New logins come from saved institute records, including deleted accounts whose addresses remain reserved.

**Fees.** After a payment is recorded, the message names the amount and the student and has a **Print receipt** button (a one-page receipt, printed as text). **Who Hasn't Paid** is in the menu for admins and accountants, and its headline counts unpaid vouchers and the students they belong to. A student's fee history now includes the admission fee set when they were added (it used to read Rs 0). An empty Fees page says what to do next, including "Add your classes first" when there are none.

**Smaller fixes.** New Class accepts several sections at once ("A, B, C") and always shows Save, with a reason when it is off. Saving attendance says what was saved ("Attendance saved for 10 - B: 6 present, 0 absent"). Adding staff shows their login email. The accountant dashboard shows shortcuts instead of "coming soon". Result cards have an empty class teacher's remark box instead of fixed praise. Parents with one child go straight to that child's fees, see fees owed first on their dashboard, and have Attendance and Fees in the phone tab bar.

</details>

<details>
<summary><b>Administrators: import review, purchase receipts and fee announcements</b></summary>

Staff and class spreadsheets show validation and duplicate problems before processing. Staff review checks contact details, supported roles and institute capacity. Class review checks teacher matches and scheduling conflicts, preserves sections and defaults to merging timetable entries. Imports continue in durable background jobs with row outcomes in import history.

Completed subscription purchases queue a detailed receipt for the purchaser. Returning to the payment page can recover a missing receipt without resending one already delivered. Remaining trial days carry into a paid subscription once. The payment page keeps Back and Go to Dashboard together, and the shorter plan chooser offers a full comparison when needed.

Fee campaign and session cards show a notification bell until their first recorded announcement. Sending requires confirmation and saved fees; an empty campaign explains what to create first. Repeated requests do not queue the same announcement again. Notifications sent before campaign tracking was introduced cannot be reconstructed reliably.

</details>

<details>
<summary><b>Owner: plan prices, limits and institute agreements</b></summary>

Open **Admin Portal > Plans and agreements** to change the monthly and annual price in PKR and USD, student, class and branch limits, and included pages. Plans do not limit teacher accounts. Choose **Future plan defaults** to update new agreements. Choose an institute to change its saved agreement, set separate purchase prices for any tier, or explicitly apply another plan. Saving prices alone does not activate a different plan. Image storage has separate controls for future registrations and the selected institute. Existing institutes keep their accepted base prices and access when defaults change, and a payment already started retains its saved rules.

New Starter registrations are free for 100 students. New Growth agreements hold 500 students and Pro 1,500; larger institutes talk to us about Enterprise. The catalogue defaults list Growth at Rs 10,999 and Pro at Rs 19,999 a month, with a year costing 10 months. WhatsApp and bug/feature requests remain visible with a lock and are refused by the server. Background WhatsApp sends also check the agreement. Imports and create actions enforce capacity under a database lock, so simultaneous submissions cannot pass the limit. Dashboard, account settings and help remain available; role permissions and institute switches continue to apply.

Changing plans explicitly accepts that plan's current rules. Renewing the same plan uses the institute's saved base prices; temporary offers apply separately to each purchase. Free plans activate without checkout. SafePay and bank-transfer proofs carry the server-selected rules into activation. If the price changes before a payment is started, the buyer must refresh and review the total.

Applied promotion codes travel with the confirmed price into SafePay checkout and bank-transfer payment proofs. A credit promotion sets the final purchase price to its saved amount; percentage promotions apply their saved discount. The server validates the code again before payment, and the payment button waits for the confirmed total.

On a new database, the seed initializes the catalogue and saved agreements. For an existing database, run `npx prisma db push` followed by `node --import tsx scripts/initialize-plan-catalog.ts`. The initializer does not overwrite existing agreements or edited defaults. The campaign starting count of 491 and previously granted lifetime places are preserved.

**Launch offer.** While the switch on **Admin Portal > Free campaign** is on, new institutes get Starter free and Growth costs Rs 6,999 or Pro Rs 12,999 a month; a year costs 10 months at that price. The offer stays on until the owner switches it off, whatever the counter says. Public pages say "A few places left" and never show a count. The pricing page states each saving against paying the usual monthly price for 12 months, and hovering the figure shows the sum. Public prices are always in rupees, because every purchase is charged in rupees; a visitor outside Pakistan also sees an "about $X" estimate at the fixed rate in `src/lib/pricing/estimate.ts` (Rs 280 to $1), and the page says their bank converts the real charge. The USD prices in the plan editor are no longer shown on public pages. Setup and moving records are free on yearly plans; on monthly plans our team collects Rs 3,999 (Growth) or Rs 7,999 (Pro) by hand, since checkout does not add it.

</details>

<details>
<summary><b>WhatsApp Gateway: safe sending, spreadsheet uploads and developer tools</b></summary>

**Institute usage and allowances.** The WhatsApp page reads actual successful sends from the gateway, using the selected institute’s local day. A linked account starts at zero until a message is actually sent. Queued messages appear separately and reserve the remaining allowance; failures are not counted as sent. Usage refreshes every 20 seconds while visible, and an unavailable gateway shows an error and retry rather than a false zero. New institutes start with 100 messages per day. Only the platform owner can increase a selected institute’s allowance on WhatsApp, or increase and decrease it in Plans and agreements. Changes are audited and synchronized with gateway delivery limits; the gateway’s existing safety ceilings can still delay sending.

For this release, deploy the gateway usage endpoint before Academia, then run `npm run whatsapp:limits:upgrade` through the authorized release process. It upgrades the previous default of 5 in bounded batches, synchronizes gateway allowances and records a one-time release marker. Existing non-default limits are preserved. Later owner reductions to 5 are preserved by that marker.

**Sending is queued, never instant.** When a message is submitted the gateway stores it and answers immediately, then delivers it a few seconds later. Messages leave one at a time per linked number, with a random pause in between and a firm limit on how many go out per minute, per hour and per day. This is deliberate: a burst of identical instant messages is what gets a WhatsApp number banned. An institute can submit a thousand messages at once and they will simply go out safely over time. Nothing is lost if the service restarts, because the waiting messages are stored in the database rather than in memory. If the number disconnects mid-run, the remaining messages wait for it to come back instead of failing.

**Send to a list from a file.** The gateway dashboard accepts a CSV, TSV or Excel file with one person per row: a phone number, optionally a name, and either a message column or one message written once for everybody. A message can be personalised per person by writing a column name in double braces, for example `Hi {{name}}, your fee for {{month}} is due`. Local numbers written as `03001234567` are converted automatically. Before anything is sent, the page shows how many rows are usable, which rows will be skipped and why, duplicate numbers, the exact text the first few people will receive, and how long the whole run will take. Once it is running, progress can be watched and the rest can be cancelled at any time. A sample file is downloadable from the same card.

**Control over each number.** Every linked number shows how many messages are still waiting and roughly how long they will take. Each can be paused and resumed without losing anything, have its waiting messages cleared, or be set to a slower sending speed. Speeds can only be made slower than the service default, never faster, so no setting can put a number at risk. A "Very slow" option exists for numbers that were linked recently.

**Developer tools.** The dashboard has a one-click Postman collection download with the institute's own API key and gateway address already filled in, so it can be imported and used immediately without configuration, alongside the live API documentation. The same pacing applies to anything sent from Postman or from custom code, so experimenting with the API cannot get the number banned.

**Where the waiting messages live.** Waiting messages are held in two places at once: the database records what was sent, to whom and what happened to it, and Redis handles the timing, the retries and the waiting. If either one is interrupted the other repairs it, so a server restart, a crash, or a wiped cache never loses a queued message and never sends one twice.

</details>

<details>
<summary><b>How the WhatsApp services are kept running and up to date</b></summary>

The WhatsApp sender and the incoming-message handler run as their own small services alongside the main system, rather than inside it, so a problem in one cannot slow down or take down the rest of the platform. One copy of each serves the whole machine.

Keeping them current is automatic. Every time the platform starts, it checks whether each service is running and whether it is running the current version. Missing services are started, out-of-date ones are updated in place, and anything already current is simply reused. Where two copies of the platform run side by side on one server, the more recent version wins and the other attaches to it instead of fighting over it. Only the service that actually changed is restarted, so updating the incoming-message handler never interrupts a live WhatsApp connection.

Both services also report their own health, including whether the database and the queue behind them are reachable, so a problem can be seen directly rather than inferred from failed messages.

</details>

<details>
<summary><b>What a head of school can ask over WhatsApp</b></summary>

Messaging the school's WhatsApp number from a registered admin's phone opens a short numbered menu. Every answer covers that admin's own institute only.

- **Today's attendance** — present, absent and on leave across the school, the resulting percentage, and how many students nobody has marked yet.
- **Absent students today** — the first few by name and class, with a count of the rest.
- **Fees** — collected so far this month, what is still outstanding, how much of that is overdue and how many bills that is, and anything waiting for a payment to be reviewed.
- **Leave requests to approve** — how many are waiting, who they are for and when they were raised, oldest first.
- **School at a glance** — students, staff and classes on the books.

Attendance follows the same rule as the rest of the platform: approved leave is shown as its own figure and never counted against the school, and a day on which every marked student was on leave says so rather than showing a misleading percentage.

Entering marks and changing school settings stay in the app, because both need the full record in front of you; asking for them over WhatsApp explains that rather than leaving you waiting for a reply.

</details>

The result is a platform that is useful not only for management, but for daily execution.

---

## What Type Of Institutes Can Use Innovorix

Innovorix is suitable for:

- schools
- colleges
- academies
- coaching centers
- tuition networks
- training institutes
- branch-based education businesses
- private institute groups

In this document, the preferred word is `institute`.

Where a workflow is common in a traditional classroom-based institute, the same workflow still applies here.

---

## Core Product Promise

Innovorix helps an institute:

- centralize records
- reduce repeated data entry
- improve operational discipline
- increase parent transparency
- speed up fee management
- improve attendance handling
- simplify academic workflows
- formalize leave approvals
- organize communication
- support staff on mobile
- create cleaner year-end promotion workflows

---

## Major Benefits For Institute Leadership

### Better Control

Leadership gets clearer visibility into students, staff, attendance, fees, exams, and operational progress.

### Less Dependency On Informal Systems

Instead of relying on:

- paper registers
- personal WhatsApp groups
- manual fee notebooks
- spreadsheet fragments
- separate result files

the institute can work from one connected platform.

### Faster Daily Work

Bulk actions, templates, auto-fill logic, duplication tools, and role-based pages reduce the effort needed for repetitive work.

### Better Parent Trust

Guardians can see attendance, fees, marksheet, and communication history more clearly.

### Better Staff Accountability

Leave reviews, exam progress, attendance entries, fee approvals, and communication flows all become more structured.

### Better Mobile Usability

A strong part of the product experience is designed around practical mobile use for staff, parents, and students.

---

## Modules At A Glance

Innovorix includes the following major modules:

- Dashboard
- Staff Management
- Student Management
- Guardian Management
- Classes & Sections
- Timetable Management
- Attendance
- WiFi Attendance (staff check-in and QR sessions)
- Leaves
- Assessments
- Exams
- Marksheet
- Fees & Payments
- Fee Defaulters
- Payment Proof Review
- Library
- Promotion
- Communication
- Notices & Calendar
- Settings & Institute Configuration
- Notifications
- Mobile App Experience

---

## Roles Covered In This Document

This document covers these roles in detail:

- Admin
- Teacher / Staff
- Student
- Guardian
- Accountant
- Librarian

Super admin capabilities exist in the platform as well, but this document focuses on the operational roles that matter most in regular institute use and sales conversations.

---

## Quick Role Summary

| Role       | Main Purpose In The Institute                                                                |
| ---------- | -------------------------------------------------------------------------------------------- |
| Admin      | Runs institute setup, records, fees, academics, communication, and promotions                |
| Teacher    | Runs class-level teaching workflows such as attendance, assessments, marks, and leave review |
| Student    | Views own learning, attendance, fees, results, timetable, and leave status                   |
| Guardian   | Tracks child progress, fees, attendance, marksheet, leave requests, and conversations        |
| Accountant | Runs the fee collection side, fee follow-up side, and payment proof review side              |
| Librarian  | Manages books, issue-return flow, overdue books, and library fine handling                   |

---

<details>
<summary><strong>Platform Overview, Product Value, Setup Journey, And General Product Story</strong></summary>

## Why Innovorix Is Attractive From A Product Perspective

Many institute systems can list students.

Many can record fees.

Many can create timetables.

Many can show marks.

But the stronger value comes when those modules work together.

Innovorix is attractive because it does not stop at simple record storage.

It includes operational logic.

It includes hand-holding inside workflows.

It includes shortcuts that reduce staff effort.

It includes review states so actions are not lost.

It includes role-specific views so people are not overwhelmed.

It includes mobile usability, which is essential for real institute adoption.

---

## Product Philosophy

Innovorix is not meant to be used only by an IT person.

It is meant to be used by:

- an admin officer
- a finance operator
- a teacher
- a class in-charge
- a librarian
- a parent
- a student

That is why the platform is built around practical operational pages rather than technical complexity.

---

## Main Product Stories

The easiest way to understand Innovorix is to see the types of stories it solves.

### Story 1: Admission To Daily Learning

An institute admits a student.

The student gets linked to a class.

The guardian can be linked during admission.

Admission fees can be suggested automatically.

Student and guardian credentials can be generated automatically.

The student then appears in attendance, assessments, exams, marksheet, fees, and leave workflows without needing repeated record creation in each module.

### Story 2: Timetable To Teacher Work

The institute creates classes and timetable slots.

Teachers are assigned during timetable setup.

Those assignments then support:

- teacher timetable views
- teacher class views
- attendance workflows
- communication workflows
- class-based academic workflows

### Story 3: Fee Planning To Fee Recovery

The institute creates fee sessions and fee campaigns.

Fees are generated in bulk.

Students and guardians can view their challans.

Payment proofs can be uploaded and reviewed.

Defaulters can be isolated on a dedicated page.

Reminders can be sent.

Fees can be marked paid.

Next fee cycles can be duplicated from earlier sessions to reduce effort.

### Story 4: Exam Creation To Result Visibility

The institute creates exam sessions and exam slots.

Teachers enter marks.

Progress bars help track grading completion.

Students and guardians later see datesheets, marks, and marksheets in role-appropriate pages.

### Story 5: Student Leave To Approved Record

A student requests leave.

Guardian approval can happen first.

Teacher approval can happen next.

Attachments, comments, bypass reasons, and status history stay visible.

The institute gets a cleaner leave process than informal message-based handling.

### Story 6: End Of Session Promotion

At the end of an academic cycle, the institute can:

- promote selected students from one class
- or run bulk promotion across many classes

The system records promotion history by academic session so the institute keeps better long-term records.

---

## Product Value For Marketing Teams

If a marketing team needs to explain Innovorix clearly, these are strong talking points:

- one platform for the full institute operation
- better control for management
- less manual duplication for staff
- stronger fee collection workflows
- parent transparency through guardian access
- teacher productivity through role-based pages
- mobile-friendly daily usage
- structured approvals and audit trails
- modern communication features
- result and fee visibility in one system

Another good selling angle is this:

Innovorix is not just a record system.

It is an operating system for an institute.

---

## Product Value For Sales Conversations

When presenting to a prospect, the strongest practical points are often:

- how the fee system reduces repeated work
- how the parent side improves transparency
- how the teacher side stays focused and simple
- how mobile usage makes adoption easier
- how attendance and exam data connect naturally
- how the promotion workflow saves year-end operational time
- how communication becomes more controlled

---

## Product Value For Implementation Teams

An implementation team can use this document to understand:

- which modules must be configured first
- which roles must be trained first
- which workflows are interconnected
- which quick wins the institute will notice early

---

## Suggested First-Time Institute Setup Journey

New institutes are walked through the essentials of this in the app by **Get Started**. Classes do not need teachers first: teachers can be added later and put into timetable slots. An ideal rollout journey inside Innovorix can follow this order:

### Step 1: Institute Setup

- create institute profile
- set contact details
- set domain
- set timetable display mode
- set timezone
- configure preferences

### Step 2: Staff Setup

- add staff
- add teachers
- define who is operationally active
- create credentials where needed

### Step 3: Class Setup

- create classes
- create sections
- assign teachers
- create subjects
- build timetable

### Step 4: Student And Guardian Setup

- add students
- link guardians
- import data if needed
- create credentials
- confirm class placement

### Step 5: Financial Setup

- configure admission fee rules
- configure late fee rules
- configure sibling discount if needed
- create first fee session
- create fee campaigns

### Step 6: Academic Workflow Start

- start attendance
- create assessments
- create exams
- train teachers on marks entry

### Step 7: Parent Visibility Start

- enable guardian visibility
- train office on payment proof review
- train guardians on fee and leave workflows

### Step 8: Year-End Flow

- results and marksheet review
- promotion planning
- single or bulk promotion execution

---

## Desktop And Mobile Experience

Innovorix is not only a desktop dashboard.

The product experience is clearly designed to work in mobile use cases too.

That matters because in real institute environments:

- parents often use phones, not laptops
- students often use phones, not laptops
- teachers often check schedules, notices, and updates on phones
- admin and finance staff may need quick mobile confirmation and visibility

---

## Mobile App And Mobile Experience

Innovorix includes strong mobile-readiness and native mobile support.

### What This Means In Practical Terms

- the interface is designed to remain usable on mobile screens
- the product includes a mobile-oriented navigation flow
- the layout adapts for role-based usage on smaller devices
- important workflows such as attendance, fees, communication, and notices are available in mobile-friendly presentation
- push notification handling is built into the product
- Android app packaging exists through a native wrapper workflow
- the system can also operate as a standalone installed web app experience

### Native Mobile App Direction

The project includes Android build support through a native mobile packaging setup.

This means the product can be delivered not only as a browser platform, but also as a mobile app experience for institutes that prefer app-based usage.

On Android 15 and newer the app fills the whole screen, edge to edge, behind the status bar and the gesture bar. For every role, the dashboard header, the public site and signup headers, the bottom menu, the sidebar on tablets, side panels, dialogs, toasts, the help panel and the landing page's floating buttons keep clear of the clock, the camera notch and the gesture bar. The help panel on phones also stops above the bottom menu. The strip behind the status bar takes the page colour, and the status bar icons follow the theme chosen in the app (dark icons on the light theme, light icons on the dark theme) even when the phone's own dark mode differs. Short pages such as sign-in fit the screen without scrolling. All of this is switched on only inside the Android app; browsers, including on iPhones, are unchanged.

Opening the site while signed in takes you straight to your dashboard. To read the home page anyway, click Home from any other public page, such as Pricing.

Rest the pointer on any menu entry to see what its page is for (on a phone, the Menu page shows it under each name). Numbers beside Payment Proofs, Instalment Requests and Leaves show what is waiting for you. In Settings, type what you are looking for, such as "late fee", into the search box under the heading. The Trial badge in the header shows the days left; tap or hover it to see what happens when the trial ends. Menu entries tagged Trial are not in your plan and lock when the trial ends.

Picking a plan on the Pricing page carries it into sign-up. You set up first on Starter, then Get Started and the dashboard offer to activate the plan you picked.

The 30-day free trial of every feature does not start at sign-up. The dashboard offers it, and it starts only when an administrator presses **Start my 30-day trial** (once per institute). **No thanks** hides the offer; Unlock new features can still start it later. The dashboard warns three days before the trial ends and says so once after it ends; your records are always kept. A free Starter institute sends no WhatsApp messages. Enterprise has no calculated price: its quote screen gives the team's WhatsApp number and email, and a short form.

What each plan includes comes from the saved plan list, the same on the Pricing page, the plan cards and the payment card in the upgrade window. Risk detection, MCQ practice, the campus workspace, monthly fee automation, exam customization, staff engagement and student history are Pro features for new agreements; agreements saved before campus had a plan switch keep it. Scan results, the library, staff WiFi check-in and chat between teachers and guardians start at Growth for new agreements; notices stay on every plan, Starter included. Agreements already saved keep what they allow until the owner edits them. While the full-feature trial runs, each menu entry the plan alone would lock shows a Trial tag. Every plan can report bugs from Report an Issue; asking for new features needs a plan that includes feature requests, and the request tab says so when it is locked.

The app and the public site open in the light theme. Anyone can switch to Dark, or to System (follow the device), from the account menu in the dashboard header or the moon button on the public site, and the choice is remembered on that device.

### Mobile Strengths That Matter For Adoption

- quick access to dashboard and menu items
- better experience for guardians checking child progress
- easier fee and payment proof interaction from phones
- easier communication handling from phones
- easier notice consumption from phones
- better teacher access to timetable and attendance on the go

### Mobile Notifications

The platform supports notification-oriented workflows and mobile permissions handling.

This helps the institute reach users more directly for operational updates.

### Mobile Design Value In Marketing Terms

For a marketing team, this matters because many prospects do not ask only:

`What can the product do?`

They also ask:

`Will people actually use it regularly?`

Mobile readiness improves the answer to that question.

### Mobile Experience Positioning

A good product positioning line can be:

Innovorix is built for real institute life, not only for office desktops.

---

## Notices, Communication, And Visibility

One of the stronger product stories in Innovorix is visibility.

An institute often struggles because information is available, but not visible to the right people at the right time.

Innovorix improves that through:

- role-based dashboards
- noticeboard visibility
- fee visibility
- attendance visibility
- marksheet visibility
- communication threads
- mobile access
- notifications

This is especially helpful in institutes where parents repeatedly call the office for information that should already be visible digitally.

---

## Detailed Role And Module Breakdown

The following sections describe what each role gets and what each page is meant to achieve.

---

</details>

<details>
<summary><strong>Admin Role, Admin Pages, And Admin Workflows</strong></summary>

# Admin Role

## Admin Role Summary

The Admin role is the main operational leadership role inside the institute.

This role is not only about data entry.

It is about running the institute digitally.

Admin controls the daily backbone of the product:

- staff setup
- student and guardian records
- class and timetable planning
- fee lifecycle
- attendance management
- leave review
- academic planning
- marksheet access
- fee recovery
- parent visibility
- promotion execution
- institute settings

If someone asks, `What is the main control role inside Innovorix?`

the answer is:

`Admin`

---

## Admin Dashboard

### Purpose

The dashboard gives the admin a central operational overview instead of forcing the admin to open many modules one by one.

### Institute Health Score

The first thing Admin/SuperAdmin sees is an executive **Institute Health** panel — a single 0-100 score blended from six operational metrics, each shown as a trend card with its change versus the previous period:

- **Attendance** — present vs absent (leave excluded)
- **Fee Recovery** — amount collected vs billed
- **Student Performance** — average grade percentage
- **Teacher Compliance** — class days with attendance marked
- **Leave Resolution** — leave requests resolved vs pending
- **Parent Engagement** — active guardians in messaging

It includes an attendance trend chart and a current-vs-previous comparison chart. The time range adapts to how long the institute has existed (Last 7 Days, 30 Days, 90 Days, 6 Months, Last Year, or a custom range), and the comparison period adjusts automatically. Metrics with no data show **N/A** and are excluded from the score, so a newly-created institute still gets a fair reading. The whole panel loads from a single backend request and refreshes in one request when the range changes.

### What The Admin Sees

- total students
- total classes
- total sections indirectly through class structure
- active teachers
- upcoming exams
- notices and calendar

### What The Admin Can Do From Here

- understand current institute scale
- quickly notice if class structure or staff scale is growing
- post notices
- review upcoming academic activity
- use the dashboard as a command center before entering deeper modules

### Why This Matters

A dashboard should not be decorative.

It should reduce uncertainty.

For an admin, that means being able to quickly understand:

- how many students exist
- how many teachers are active
- whether exam periods are approaching
- whether notices need to be pushed

### Posting A Notice

A notice is aimed at roles and, optionally, at classes.

- pick the roles that should hear it, exactly as before
- leave the class picker empty and the notice goes to the whole institute
- pick one or more classes, or individual sections, and the notice is limited to them

When classes are chosen, a notice reaches the students in those classes, the guardians of
those students (a guardian is matched through the children they have there, not through a
class of their own), and the teachers assigned to those classes. Admins, accountants and
librarians run the whole institute, so a class filter never hides a notice from them.

Every notice in the list carries a small line showing its roles and either "All classes" or
the classes it was aimed at, so a school-wide announcement is distinguishable from a
class-specific one at a glance. Hovering that line explains who received it and why.

### Nice Points

- dashboard cards are practical, not abstract
- notices and calendar are integrated
- role-specific dashboard behavior exists in the platform, so the admin experience stays distinct from the teacher and guardian experience

---

## Admin Staff Page

### Purpose

This page manages the people who work inside the institute.

### Main Capabilities

- add staff
- edit staff
- view staff details
- disable staff accounts
- permanently delete staff records
- import staff from CSV
- export staff to CSV
- sync staff records with login/auth accounts
- send notifications to staff
- use tags for organization
- open teacher timetable directly from the staff page

### What The Admin Can Maintain In A Staff Record

- name
- role
- email
- mobile number
- joining-related information
- password where relevant
- tags
- assigned teaching visibility via timetable and classes

### Operational Benefits

- staff onboarding becomes structured
- role-based staff creation becomes easier
- the institute does not lose control over active versus disabled accounts
- admin can review a teacher’s schedule without leaving the module

### Hidden And Useful Points

- the platform supports staff that may not need a normal login, using the `Other` role
- bulk account handling reduces repetitive office work
- timetable visibility from the staff page helps in workload review, conflict review, and internal planning
- import/export makes migration and periodic auditing easier

### Why A Principal Or Director Should Care

A strong staff page is not only a database.

It helps the institute answer questions like:

- who is active
- who is teaching what
- whose account should be disabled
- whether staff records are complete
- whether teacher timetable assignment looks balanced

---

## Admin Classes Page

### Purpose

The classes page controls the structural academic design of the institute.

This is where class organization becomes usable across the system.

### Main Capabilities

- create classes
- create sections (several at once, separated by commas)
- pick the class teacher of each section, who takes its attendance
- edit full class records
- edit a single section inside a class
- assign teachers
- assign subjects
- build weekly timetable
- import timetable data
- export class data
- switch between grid and list views
- view timetable by class
- view timetable by section
- delete classes
- delete sections when safe

### What This Page Connects To

This page does not work in isolation.

It directly influences:

- teacher timetable
- student placement
- attendance module
- exam planning
- communication context
- timetable viewing pages

### Timetable Creation Experience

The timetable builder allows the admin to define:

- start time
- end time
- subject
- teacher
- repeat days

### Important Smart Workflow

One of the nicest workflow points in the project exists here.

When the admin adds the first lecture slot and then clicks to add another one:

- the system can reuse the previous selected days
- the next slot can start from the previous end time
- the duration pattern continues

This speeds up routine timetable building significantly.

For institutes that build many periods in one go, this is a real time saver.

### Section Handling Strength

The section system is practical rather than shallow.

The admin can:

- manage multiple sections inside the same class
- open only a particular section for editing
- see student counts per section
- remove a section only when it is operationally safe

### Safety Controls

The page protects the institute from accidental structural damage.

For example:

- a section with assigned students cannot simply be removed without action
- timetable-linked sections warn before deletion

### Notifications

When timetable changes are made, the admin can control notifications to:

- staff
- students
- guardians

### Why This Matters

For many institutes, timetable editing is one of the most painful repetitive tasks.

Innovorix makes it easier through:

- repeated-day reuse
- next-slot continuation
- section-aware editing
- direct teacher assignment
- subject creation inside the flow

### Marketing-Friendly Angle

This is a good section to position as:

`Less timetable effort. More control. Fewer mistakes.`

---

## Admin Students And Guardians Page

### Purpose

This page manages the central records of the institute: students and the guardians linked to them.

### Structure

The page separates:

- Students
- Guardians

This is important because institutes need both linked records and independent management.

### Student-Side Capabilities

- add student
- edit student
- view student
- disable student
- permanently delete student
- import students
- export students
- change class in bulk
- send notifications
- open communication actions
- view attendance percentage
- assign tags

<details>
<summary>Bulk student card downloads</summary>

In Bulk Student Actions, use the highlighted **Select all classes** option or select specific classes and sections, then choose **Download Student Cards**. Individual student checkboxes narrow the download further.

Choose a ZIP of separate PDF cards, a ZIP of images, or an A4 PDF. ZIP files contain class and section folders. A4 printing supports 1 to 10 full-size cards per sheet, shows a live preview, and starts each class and section on a new page. Print at actual size (100 percent). Downloads show progress and can be cancelled. Missing student identifiers, classes or roll numbers must be completed first; unavailable photos use initials and produce a warning.

</details>

### Guardian-Side Capabilities

- add guardian
- edit guardian
- view guardian
- disable guardian where needed through account logic
- permanently delete guardian
- sync guardian login records
- track linked children

### Admission Workflow Strength

This page is stronger than a basic registration form because the student record and guardian record can be handled together.

During admission, admin can:

- create the student
- link an existing guardian
- create a new guardian
- auto-generate credentials
- connect the student to class placement
- support the admission fee workflow

### Hidden And Useful Point: Roll Number Handling

Innovorix includes stronger roll number handling than many simple systems.

When a roll number conflict happens, the admin does not have to solve it manually outside the platform.

The platform supports:

- swapping roll numbers between students
- auto-resolving conflicts by shifting the conflicting record to the next available number

This is a small-looking feature with very high operational usefulness.

### Hidden And Useful Point: Credential Automation

The platform can auto-generate:

- student IDs
- guardian IDs
- student passwords
- guardian passwords

based on institute-defined patterns.

This is especially useful for institutes that want:

- cleaner record standards
- less manual credential creation
- a predictable institutional format

### Hidden And Useful Point: Optional Guardian Support

Not every student record in every institute comes with a clean guardian login setup from day one.

Innovorix supports that practical reality.

Student records can still exist even if guardian setup is not complete yet.

### Attendance Visibility

Admin can see attendance percentage alongside student records.

This makes the student page more informative than just a profile list.

### Tags And Segmentation

Tags help the institute categorize students for internal workflows.

This can support:

- special follow-up groups
- internal academic categories
- administrative grouping
- future segmentation for communication or reporting

### Why This Matters

This page becomes the living core of the institute record system.

If student and guardian management is weak, every other module becomes harder to run.

Innovorix makes this page operationally strong through:

- linked admission handling
- smart credential generation
- bulk operations
- roll number conflict resolution
- class-change support
- communication access

### Marketing-Friendly Angle

This can be positioned as:

`A complete student and guardian record system that actually supports admissions and day-to-day institute work.`

---

## Admin Attendance Page

Today’s completion counts only class sections that have enrolled students. Empty sections remain available for navigation and history, with a neutral No students label instead of an overdue attendance warning. A class without sections counts as one attendance group.

### Purpose

This page is where daily attendance becomes organized, visible, and reportable.

### Main Capabilities

- open any class or section
- mark attendance
- review earlier attendance by date
- edit attendance where needed
- download reports for one class
- download reports across multiple classes
- export date-range attendance to CSV

### Class-Day Restriction

Attendance can only be marked on days the selected class actually meets, based on its timetable. The date picker disables non-class days (weekends and any weekday the class has no timetable slots) and highlights valid class days, with a "Class days" hint listing them. The same rule is enforced on save, so admins and teachers cannot record attendance for a non-class day even via the API. A class with no timetable configured is left unrestricted so it is never locked out of attendance.

### Absence Alerts That Say What Was Missed

When a child is marked absent, the alert their guardian receives (in the app, on the phone and on WhatsApp) checks what that child's own class and section had booked for the day. If an exam paper, a quiz or a homework deadline fell on it, the alert names it, so the guardian learns their child missed the Physics paper rather than just that they were away. If several things fall on one day, the alert names the most serious one: an exam first, then a quiz, then a homework deadline. Work set for another section of the same class is never mentioned, because that child did not miss it. On a day with nothing booked the alert reads exactly as it always has, and either way only one message is sent.

### Role Strength

Even though teachers commonly mark attendance, the admin role can still manage attendance operationally.

This is useful when:

- the institute wants office oversight
- attendance must be corrected
- reports must be prepared centrally
- the office must verify whether attendance was marked

### Bulk Report Handling

The page includes a bulk report workflow that can:

- choose multiple class-sections
- choose a date range
- export combined attendance data

This is helpful for:

- audits
- parent meetings
- management reviews
- compliance summaries

### Daily Usefulness

The admin can see how many class-sections were marked today.

That gives a simple but useful operational signal.

### Smart Controls

- invalid future attendance dates are prevented
- filtered class/section selection keeps the page practical
- date-range exports are available without needing outside spreadsheets first
- The first absence defaults to an in-app guardian alert, including a missed test or quiz when one is scheduled. Switching off WhatsApp alerts does not switch off in-app alerts. WhatsApp is selected only when the configured consecutive-absence threshold is reached (two days by default).
- Attendance stays saved if an alert fails. The register shows the delivery error and remains open for retry; retrying the same day's alert for the same children does not create duplicate in-app records.

### Why This Matters

Attendance is one of the most frequently used workflows in any institute.

If attendance data is hard to enter or hard to extract, staff confidence drops quickly.

Innovorix improves this by combining:

- daily marking
- date-based review
- report generation
- class-based organization

### Marketing-Friendly Angle

`Easy daily attendance, strong reporting, and better administrative control.`

---

## WiFi Attendance (Smart Attendance)

### Purpose

Attendance that proves presence instead of trusting it. The institute saves the WiFi surroundings of its own building, and every check-in is compared against them: staff check in with one tap when they arrive, and students mark themselves present by scanning a QR code the teacher shows in class. The comparison happens on the server, so a record cannot be faked by editing what the phone sends.

### How Verification Works

- The admin walks to each spot where check-ins should work and captures the nearby WiFi networks into a named location. Several capture points merge into one location, so a large campus is covered by capturing from a few good spots.
- A check-in matches a location when at least two of its saved networks are audible and the strongest one is loud enough. One network disappearing is normal; two rules out coincidence.
- Every verdict shown in the app explains itself on hover: which networks matched, how strong they were, and which threshold decided the outcome.

### Staff Check-In

- Staff see a check-in card on their dashboard. One tap when they arrive, one tap when they leave.
- Arriving after the configured day start plus grace period marks the day Late instead of Present.
- No internet in the building corner where they checked in: the tap is saved on the phone and sent automatically once the connection returns, with the original time and the original WiFi evidence, which the server re-verifies on arrival.
- Admins get a staff attendance page per date: who is in, who is late, who is missing, and how each check-in was verified.

### Student QR Sessions (Beta)

- The teacher starts a QR session for their class; the code on screen changes every half minute, so a screenshot sent to a friend stops working almost immediately.
- Each student scans the code inside the app. The phone quietly reads the strongest nearby WiFi networks and sends them with the scan.
- The server compares every student's surroundings with the rest of the class. A student sitting at home matches nothing and is flagged instantly. A student sitting just outside the room hears the same networks noticeably weaker and is marked suspect for the teacher to decide.
- The teacher watches a live counter of scanned and missing students, reviews the flagged list, and closes the session, which writes the normal daily attendance record, respects approved leaves, and notifies guardians of absences the same way manual marking does.
- Phones that cannot read WiFi (older app versions, or a plain browser) still check in; they are simply labelled unverified so the teacher knows the scan carried no proof.

### Per-Lecture Mode For Universities

- The institute type (School, College, University, Academy, Madrasa) is now editable in settings, and universities and colleges are pointed at a per-lecture attendance mode.
- In per-lecture mode every teacher runs a QR session for their own lecture, and the daily record is derived from those sessions: a student who attended at least half of the day's lectures counts present for the day, so every existing report and guardian alert keeps working unchanged.
- Leave requests adapt with the mode: the student is told the request will be visible to all teachers who take their class, all of those teachers can review it, and approval notifications reach the same set.

### Honest Limits

WiFi evidence is strong but not absolute, which is why the student flow carries a Beta tag. The corridor-outside-the-room case is surfaced as suspect rather than silently accepted or rejected, and the teacher always has the final word. Reading WiFi requires the Android app with location permission granted; the feature asks for it with a plain-language explanation before the system prompt appears.

### Marketing-Friendly Angle

`Attendance that proves people were actually there.`

---

## Admin Leaves Page

### Purpose

This page organizes student leave handling in a more disciplined way than message-based approvals.

### Main Capabilities

- view pending leave requests
- view leave history
- open request details
- review attachments
- approve leaves
- reject leaves
- add reviewer comments
- understand guardian approval status

### Leave Workflow Depth

Staff see separate Waiting for review, Waiting for guardian and Decided tabs. Guardian-stage requests remain visible with details only and cannot skip guardian approval. Counts and lists share the same search and class filters. The dashboard resolution percentage includes every stage. Demo seed data includes requests ready for staff review as well as requests awaiting guardians.

This is not a flat yes/no leave page.

It supports more realistic leave handling such as:

- guardian approval first
- teacher approval next
- bypass cases
- attachment support
- leave type behavior
- comments and review identity

### Why This Is Useful

Institutes often face confusion in leave handling because requests are split across:

- WhatsApp messages
- call records
- verbal instructions
- notebook notes

Innovorix gives the institute a cleaner record with:

- status
- date set
- reason
- attachment
- reviewer
- comments
- guardian context

### Nice Operational Point

Bypassed guardian approvals are still visible.

That means the institute does not lose approval context even when the workflow needs flexibility.

### Another Strong Point

Advance notice requirements can be configured by leave type.

This supports different institute expectations for:

- casual leave
- planned leave
- emergency leave
- document-required leave

### Why Leadership Should Care

A formal leave workflow improves:

- discipline
- clarity
- auditability
- parent trust

---

## Admin Assessments Page

### Purpose

This page manages smaller academic evaluation work such as assignments and quizzes.

### Main Capabilities

- create assignments
- create quizzes
- filter by class
- filter by subject
- filter by type
- edit assessments
- delete assessments
- review submissions

### Why The Assignment And Quiz Separation Matters

Some systems mix everything into one simple item list.

Innovorix separates assessment types more clearly.

This helps with:

- cleaner academic understanding
- better teacher workflow
- more meaningful student visibility
- better reporting language

### Role-Based Visibility

The page is role-aware.

That means:

- admin sees broadly
- teacher sees assigned relevance
- student sees only what belongs to them

### Why This Matters

This keeps the system from feeling overloaded while still staying powerful.

### Marketing-Friendly Angle

`Assignments and quizzes managed in a cleaner, more structured academic workflow.`

---

## Admin Exams Page

### Purpose

This page manages the larger formal academic evaluation cycle.

### Main Capabilities

- create exams
- create exam sessions
- assign classes and sections
- define subject slots
- define dates
- define timings
- define total marks
- manage grade entry
- track grading completion
- view datesheets
- archive exams into history
- archive entire exam sessions into history
- restore archived sessions

### Session-Based Organization

Exam sessions are a major strength.

Instead of creating disconnected exam items forever, the institute can group them into named sessions such as:

- monthly test cycle
- mid-term
- term exams
- annual exams

This keeps the page much more organized over time.

### Datesheet Building

Save stays available while required fields are incomplete. An attempted save highlights missing session, name, class selection and paper details in red, focuses the first missing field and shows a reminder. Correcting a field clears its highlight.

Only the first paper of an exam is typed out in full. Every paper added after it
is proposed from the one above: the next subject that has no paper yet, the same
start and end time, the same total marks, and the next date.

The gap between dates repeats whatever gap was last set by hand, counted in
teaching days. Setting the second paper two days after the first puts the third
two days after the second.

Teaching days come from the timetables of the classes actually sitting the exam,
so a day those classes do not meet is never proposed. Weekends are skipped;
classes with no timetable fall back to Monday to Friday.

Every proposed value can be overwritten, and the change feeds the next proposal.
Once every subject taught in the selected classes has a paper, no more can be
added and the button says so.

### Grade Entry Workflow

Obtained marks accept zero and decimals such as 10.5, up to the subject total. Negative numbers, signs and exponent notation are refused. Paper totals remain positive whole numbers. The server checks these limits before saving a batch.

Marks are entered inside a structured grade-entry dialog.

The system helps protect data quality by validating marks.

If marks exceed total marks, the system does not silently accept bad values.

### Progress Tracking

Section-level progress indicators show how much grade entry is complete.

Choosing which section to mark opens a searchable list showing, for each one,
how many of its marks entries are filled and how many are expected, and how many
sections are finished overall. It stays inside the screen however many classes
the exam covers.

This is very helpful during active exam periods when the institute wants to know:

- which sections are complete
- which teachers may still have pending work

### History Handling

The system supports moving:

- a single exam
- or a whole exam session

into history.

This keeps the active exam area cleaner without deleting long-term records.

### Why This Matters

Exam clutter becomes a real issue in growing institutes.

Session grouping plus history management helps the institute stay organized year after year.

### Datesheet Benefit

Students can access datesheet-oriented visibility, making the exam experience more practical for end users too.

### Marketing-Friendly Angle

`Formal exam management with cleaner session control, grade validation, and progress visibility.`

---

## Admin Marksheet Page

### Purpose

This page turns stored marks into result visibility.

### Main Capabilities

- search students by name or ID
- browse by class
- open marksheet views
- support report-card style result access
- support transcript-style result access

### Why This Matters

Marks entry has little operational value if the institute cannot later open and use the results clearly.

This page helps bridge that gap.

### Practical Office Use Cases

- result checking
- parent meeting preparation
- quick office verification
- result viewing support

### Strong Usability Point

Search makes result retrieval fast.

That matters a lot for office staff during busy result periods.

### Marketing-Friendly Angle

`From marks entry to clear marksheet access with less search effort and better result presentation.`

---

## Admin Fees And Payments Page

### Purpose

This is one of the most commercially important modules in Innovorix.

It handles fee planning, fee generation, fee visibility, fee status, and fee continuity.

### Main Capabilities

- create fee sessions
- create fee campaigns
- add multiple fee components
- assign campaigns to classes
- generate fees in bulk
- mark fees as paid, one student or a whole class at a time
- manage draft sessions
- activate sessions
- delete individual fees
- delete fee campaigns
- open and print challans
- use templates
- receive template-based suggestions
- review fee status

### Reading The Fee Status Screen For One Class

Once a class is picked, the screen opens with the class's own breakdown across the top:
how many challans exist in total, how many are paid, how many are still due and how many
have gone past their date, each with the money that group is worth, and a bar showing the
share of the billed money that has actually come in. Those four cards are also the filter:
tapping one narrows the list underneath to that group, and the counts stay class-wide so
they keep their meaning while a filter is on. Hovering a card says what puts a challan in
that group, including why a part paid challan stays under Due or Overdue rather than
moving to Paid.

### Collecting From A Whole Class At Once

When a class pays together, the fee list lets an admin or accountant tick the students
concerned and record all of those payments in one step, instead of opening each row on its
own. Ticking rows reveals a "Mark as paid" button, and before anything is written a
confirmation names how many students are involved, the total being recorded and every
student with their class, section and amount. Challans that are already paid are shown but
left alone.

The whole batch is written together, so if anything fails no student in that class is left
half-recorded, and the result reports how many were marked paid and how many were skipped.
Only an admin, accountant or super-admin can do this; the check happens on the server, and
every selected challan is re-checked against the caller's own institute before it is
touched.

### What A Fee Session Means

A fee session is a broader collection container for one fee cycle or period.

For example:

- January 2026
- Spring Session
- Admission Cycle
- Monthly Fee Batch

### What A Fee Campaign Means

Inside a fee session, the institute can create one or more campaigns.

A campaign may represent:

- monthly tuition
- lab fee
- transport-related fee
- composite fee set

### What A Fee Contains

A generated fee may include:

- student
- class targeting source
- session
- campaign
- fee components
- due date
- total amount
- payment status
- late fee logic

### Draft Session Strength

This is a major operational feature.

Admin can prepare a fee session as draft first.

That means:

- planning can happen before going live
- review can happen first
- accidental notices can be avoided
- the institute can work more carefully

### Hidden And Very Attractive Point: Duplicate For Next Session

This is one of the strongest “less double work” features in the project.

The platform includes a multi-step next-session duplication wizard.

The admin can choose an earlier fee session and create the next one using that previous structure as the base.

The wizard can pre-fill:

- new session name
- fee campaign structure
- fee component amounts
- class selections
- due date suggestions

Then the admin only reviews and confirms.

This is very useful for recurring fee cycles.

Instead of rebuilding routine monthly fee structures from scratch every time, the institute can move faster with more consistency.

### Hidden And Useful Point: Save As Template

Campaigns can be saved as templates.

These templates then help drive future suggestions and reduce repeated configuration.

### Hidden And Useful Point: Duplicate Protection With Flexibility

The system protects against accidental duplication.

But it also allows intentional duplication when the institute genuinely needs multiple campaigns with the same name for the same class context.

That balance is practical.

### Late Fee Visibility

Late fee rules connect into the challan experience.

This improves clarity for students and guardians.

### Why Institute Leadership Should Care

This page is not just about fee creation.

It affects:

- cashflow discipline
- fee record consistency
- staff workload
- parent transparency
- error reduction

### Marketing-Friendly Angle

`A fee system built not just for record keeping, but for recurring fee operations, review control, and faster monthly execution.`

---

## Admin Fee Defaulters Page

### Purpose

This page isolates overdue fee follow-up into a dedicated workflow.

### Main Capabilities

- choose a fee session
- see total defaulters
- see overdue amount
- see affected classes
- filter by class
- filter by overdue days
- filter by amount range
- export defaulters to CSV
- mark selected fees as paid
- mark individual fees as paid
- send reminders

### Reminder Handling

The reminder workflow can use:

- WhatsApp
- in-app notifications
- or both

<details>
<summary>Automatic reminders and reminders for the whole overdue list</summary>

The settings gear on Fee defaulters opens **Settings > Fee management > Automatic fee reminders**. Automation starts disabled. Administrators can choose the start date, school-local time (initially 8:00 in the morning), recipients and delivery methods. Send on the due date, one day before, or two days before. The background worker checks schedules every minute; reminders require the worker and Redis to be running.

**Remind everyone** targets the current filtered list. Its confirmation shows the actual number of distinct guardians and students, with sibling vouchers combined into one guardian summary. Payment balances and eligibility are checked again before delivery. If the list changes before confirmation, review the updated counts before sending.

When automation is enabled, the page shows the last successful reminder, pending deliveries and failures with a retry action. Settings are saved in the database. Retries preserve completed delivery channels and avoid repeated in-app notices.

</details>

### Recovery Insights

A second tab on the same page turns the overdue list into a recovery picture, using the payment ledger that records when each instalment actually arrived. For every student who still owes something it shows how many challans were paid on time, paid late or missed, the average number of days late, what is outstanding and how long it has been overdue, plus a behaviour band: **Always Pays On Time**, **Occasionally Late**, **Frequent Late Payer** or **High-Risk Defaulter**. A month-by-month strip shows the last twelve months at a glance, and students with repeated defaults or delays that are growing are flagged.

A recovery score out of 100 estimates how likely the outstanding money is to come in. The formula is printed on the page, every contributing signal is shown next to the score, and hovering or focusing any band, score or month cell explains why that student has that value.

Two limits are stated rather than papered over. A challan the office closed before itemised payments existed carries no payment date, so whether it was late is unknowable: those are counted separately as "timing unknown" and never assumed on time. And a student with only one or two concluded challans gets no band and no score at all, because two months is not a pattern. The sample size sits next to every judgement.

Because this exposes how individual households handle money, the tab is limited to administrators and accountants of that institute.

### Why This Is Strong

Many systems force staff to find defaulters manually inside a long fee list.

Innovorix gives the institute a proper recovery-focused page.

### Operational Benefits

- finance staff can focus only on overdue cases
- class-wise follow-up becomes easier
- the office can isolate higher-risk dues faster
- reminders can happen from the same context

### Hidden Strength

Reminder handling runs in the background, so the office does not need to stop all work while notifications are being processed.

### Marketing-Friendly Angle

`A dedicated fee recovery page, not just a generic fee list.`

---

## Admin Payment Proof Review Page

### Purpose

This page handles proof-based payment confirmation.

It is especially useful for institutes where payment may happen externally and the user later submits evidence.

### Main Capabilities

- view pending payment proofs
- review uploaded proof details
- approve proof
- reject proof
- add review notes
- notify the student
- review past decisions in history
- filter history by class
- filter history by fee session
- filter history by approval status

### Why This Matters

Without this workflow, many institutes face one of two problems:

- office staff mark fees paid informally without a controlled review flow
- or students keep sending screenshots manually with no traceable process

Innovorix improves this through:

- pending review queue
- approval and rejection handling
- review history
- notification feedback

### Approval Behavior

When a proof is approved:

- the fee can be marked paid
- the review history becomes part of the fee workflow

### Rejection Behavior

When a proof is rejected:

- notes can explain why
- the student is informed

### Why A Principal Or Owner Should Care

This workflow reduces confusion between:

- proof received
- proof reviewed
- payment accepted
- payment rejected

That is especially valuable in institutes with growing student volume.

### Marketing-Friendly Angle

`Controlled payment proof review that brings discipline to off-platform fee collection scenarios.`

---

## Admin Library Page

### Purpose

This page handles the institute’s library circulation and book record workflows.

### Main Capabilities

- maintain book catalog
- add books
- edit books
- delete books
- issue books
- return books
- view circulation
- track overdue books
- manage fine collection logic
- view total books, issued books, overdue books, and total members

### Catalog And Circulation Split

The page is structured around meaningful library work areas such as:

- catalog
- circulation
- fines

This makes the role easier to use.

### Overdue Fine Strength

Library fine rules are connected into the circulation workflow.

That means fines are not just a side note.

They become part of return handling.

### Operational Benefits

- books are not just stored, but tracked
- overdue follow-up becomes clearer
- book return handling becomes more formal
- fines become more visible and more consistent

### Marketing-Friendly Angle

`A real library operations page, not only a static book inventory.`

---

## Admin Promotion Page

### Purpose

This page handles one of the most sensitive academic year-end workflows: student promotion.

### Main Capabilities

- choose academic session
- choose source class-section
- choose target class-section
- select eligible students
- confirm promotions
- see already-promoted students
- use single-class promotion
- use bulk promotion across many classes

### Single Promotion Mode

This is useful when the institute wants careful, class-by-class promotion control.

Admin can:

- choose the current class-section
- choose the target class-section
- select students
- confirm movement

### Bulk Promotion Mode

This is useful when the institute wants larger-scale execution.

Admin can:

- work across many class-sections
- set a target for all students in one class block
- or select different targets student by student

### Important Hidden Strength

Bulk promotion is not only class-aware.

It is section-aware too.

That matters because real institutes often promote not only to the next class, but also to the correct next section structure.

### Protection Against Duplicate Promotion

Students already promoted for the selected academic session are clearly identified.

This reduces mistakes during year-end operations.

### Promotion History Value

Promotion history stays attached to session context.

This improves longitudinal record quality.

### Marketing-Friendly Angle

`Smart promotion handling for both careful class-by-class movement and large year-end promotion cycles.`

---

## Admin Communication Monitoring

### Purpose

This gives administrative oversight over institute communication flows.

### Main Capabilities

- review communication environment
- monitor structured conversations
- use message supervision functions

### Why This Matters

When communication moves into the system, the institute gains:

- structure
- visibility
- less dependency on personal message trails

### Marketing-Friendly Angle

`More controlled institute communication, with less dependence on scattered informal channels.`

---

## Admin Settings Page

### Purpose

This page is the configuration backbone of Innovorix.

### Main Areas Included

- profile
- password
- security
- institute information
- admission fee setup
- fee management setup
- sibling discount setup
- library fine setup
- email and ID pattern setup
- tag management
- notifications
- appearance

### Recovery Email

A verified administrator with no separate recovery address automatically uses the verified sign-in email, including its original verification date. A different personal address is preserved. Other roles still require their own separately verified personal email. Verified accounts show a compact status, while verification actions sit beside the relevant text or code field. Loading failures offer Retry.

### Institute Information Setup

Admin can maintain:

- institute name
- institute email domain
- contact information
- timezone
- address
- timetable display mode

### Admission Fee Configuration

Admin can define admission fee rules by class group.

This is useful because admission handling is often not the same across all classes.

The platform can then use these rules to support the admission process.

### Late Fee Configuration

Admin can define:

- late fee rules
- grace period for newly admitted students
- default due date behavior

This is a strong operational feature because new admissions often happen mid-cycle, and the platform avoids immediately treating such students unfairly as overdue.

### Sibling Discount Configuration

Admin can enable structured sibling discount logic based on guardian-linked children.

This is useful for institutes that want policy consistency in discounts.

### Library Fine Configuration

Admin can define overdue fine rules centrally so library handling follows policy rather than informal staff judgment.

### ID And Password Pattern Configuration

Admin can configure institutional identity standards for:

- students
- staff
- guardians

This includes pattern preview and password source logic.

This is one of the stronger professionalization features in the product.

### Security And MFA

Security settings help the institute use stronger account protection.

### Notifications

Notification preferences and mobile permission handling connect into the broader communication experience.

### Why This Matters

A strong ERP becomes more valuable when it is configurable without becoming chaotic.

Innovorix gives admin control over important institutional behavior without making daily users deal with configuration complexity.

### Marketing-Friendly Angle

`Strong operational settings that help the institute standardize how it works, not just store data.`

---

## Admin Role Summary In Plain Sales Language

The Admin role in Innovorix gives an institute a digital operating center for:

- people
- classes
- timetables
- fees
- attendance
- leave control
- exams
- results
- parent visibility
- promotion
- institutional standards

That is why the Admin role is one of the strongest product stories in the platform.

---

</details>

<details>
<summary><strong>Teacher Role, Teacher Pages, And Teacher Workflows</strong></summary>

# Teacher Role

## Teacher Role Summary

The Teacher role is designed to stay practical.

It is not overloaded with institute-wide controls.

Instead, it focuses on what teachers need most often:

- class visibility
- attendance
- assignments
- exam marks
- leave review
- timetable
- communication

This keeps teacher adoption easier.

---

## Teacher Dashboard

### What The Teacher Sees

- number of assigned classes
- number of own students
- number of assignments waiting for grading
- next exam visibility
- notices
- timetable summary

### Why This Matters

The teacher dashboard helps a teacher understand daily workload quickly.

It is a focused dashboard rather than a management dashboard.

### Strong Points

- class count stays clear
- student count stays clear
- grading workload stays visible
- schedule stays visible

---

## Teacher Attendance Page

### Main Capabilities

- mark attendance for assigned classes
- review previous attendance
- edit when needed
- download reports for own class context

Attendance can only be marked on the class's scheduled days; the date picker disables weekends and any weekday the class does not meet (and the rule is enforced on save).

### Useful Workflow Detail

Low attendance visibility helps teachers notice students who may need attention.

### Parent-Related Value

Attendance data later supports guardian visibility, which makes teacher work more meaningful institution-wide.

---

## Teacher Assessments Page

### Main Capabilities

- create assignments
- create quizzes
- edit assessments
- delete assessments
- review submissions

### Why Teachers Benefit

This keeps smaller academic evaluation work organized without needing separate tools.

### Strong Product Point

Teachers are not forced to work through an admin-heavy workflow to manage class tasks.

---

## Teacher My Students View

### Main Capabilities

- see students from assigned classes
- review class-linked student lists

### Why This Matters

This is especially useful for day-to-day teaching workflows where teachers need focused access without institute-wide exposure.

---

## Teacher Leave Requests

### Main Capabilities

- review leaves pending teacher approval
- see attachments
- see guardian approval state
- see comments and context
- approve or reject with comments

### Why This Matters

Teachers often become the final operational approver of student leave in a class-level workflow.

The product supports that directly.

---

## Teacher Exams Page

### Main Capabilities

- enter marks for assigned students
- work within relevant subject scope
- use structured grade entry
- benefit from mark validation
- see completion progress

### Why Teachers Benefit

Marks entry becomes cleaner and more guided.

### Important Quality Point

The system protects against invalid marks beyond allowed totals.

---

## Teacher Communication

### Main Capabilities

- communicate with guardians
- start conversation from class context
- read and reply in structured threads
- mute/unmute conversations

### Why This Matters

Teacher-parent communication becomes more institutional and less dependent on informal scattered messages.

---

## Teacher Timetable

### Main Capabilities

- view personal timetable
- see consolidated schedule across assigned classes

### Why This Matters

A teacher does not have to inspect each class manually.

The platform brings schedule visibility together.

---

## Teacher Settings

### Main Capabilities

- profile management
- password management
- security settings
- notification settings
- appearance settings

### Why This Matters

Teacher usability improves when account control is self-service instead of office-dependent.

---

## Teacher Role Summary In Plain Sales Language

The Teacher role in Innovorix helps teachers focus on teaching operations rather than admin clutter.

It gives them:

- the right academic tools
- the right class visibility
- the right communication access
- the right timetable access

without exposing them to unnecessary institute-wide controls.

---

</details>

<details>
<summary><strong>Student Role, Student Pages, And Student Experience</strong></summary>

# Student Role

## Student Role Summary

The Student role is designed around personal visibility.

It helps the student see:

- what they must do
- where they stand
- what is due
- what is scheduled
- what has been recorded about them

This reduces uncertainty and improves engagement.

---

## Student Dashboard

### Main Value

The student dashboard is a personal learning and record view.

### What The Student Can Understand Quickly

- notices
- timetable
- recent academic visibility
- attendance-related context

### Why This Matters

The student is not forced to depend on office staff or teachers for every basic update.

---

## Student Assessments Page

### Main Capabilities

- view assignments
- view quizzes
- submit assignment work where applicable
- understand due work in a structured way

### Why This Matters

The student side is not only about passive viewing.

It also supports participation in academic workflows.

---

## Student Attendance Page

### Main Capabilities

- view personal attendance history
- understand attendance status more clearly

### Why This Matters

The student can monitor their own record instead of waiting for result-time surprises.

---

## Student Leaves Page

### Main Capabilities

- apply for leave
- choose leave type
- choose date range
- provide reason
- attach documents where required
- route request into the proper approval flow

### Hidden And Useful Point

The leave system can support guardian approval before teacher approval.

That makes the student workflow more institutionally safe.

### Another Useful Point

Advance timing rules help prevent invalid late submission for planned leave types.

---

## Student Exams Page

### Main Capabilities

- view exams
- view datesheet
- see marks visibility

### Why This Matters

The student is not disconnected from the formal exam cycle.

They can see what is relevant to them.

---

## Student Marksheet Page

### Main Capabilities

- open own result view
- see report-card style outcome
- see transcript-oriented result access where supported

### Why This Matters

Result visibility becomes direct and easier.

---

## Student Fees Page

### Main Capabilities

- view challans
- view payment history
- see fee status
- upload payment proof where allowed

### Strong Product Point

The student fee page is more than a passive balance page.

It is part of a broader fee workflow connected to:

- payment proof review
- late fee logic
- status handling

### Useful Visibility

Statuses like:

- Due
- Overdue
- Paid
- Pending Review

help the student understand where the record currently stands.

---

## Student Timetable

### Main Capabilities

- view personal weekly timetable

### Why This Matters

Schedule visibility on the student side is a practical everyday need.

---

## Student Settings

### Main Capabilities

- profile
- password
- security
- notifications
- appearance

### Why This Matters

Students can manage core account behavior without depending on office help for everything.

---

## Student Role Summary In Plain Sales Language

The Student role makes Innovorix useful at the learner level, not only at the admin level.

It helps students:

- stay informed
- stay organized
- stay aware of attendance
- stay aware of fees
- stay aware of exams and results

---

</details>

<details>
<summary><strong>Guardian Role, Guardian Pages, And Parent Visibility</strong></summary>

# Guardian Role

## Guardian Role Summary

The Guardian role is one of the most commercially attractive sides of the platform.

Why?

Because parent visibility is a major buying driver for many institutes.

Guardians want more than fee messages.

They want meaningful visibility into the child’s institute life.

Innovorix supports that through:

- child attendance view
- child marksheet view
- child fees view
- leave approval workflows
- teacher communication
- dashboard summaries

---

## Guardian Dashboard

### What The Guardian Sees

- number of children
- average attendance
- academic performance
- total exams
- child-specific performance cards
- due fee visibility

### Why This Matters

The guardian does not need to explore many pages just to understand the child’s current status.

The dashboard provides useful summary visibility immediately.

### Strong Product Point

When multiple children exist, the guardian experience still remains usable.

---

## Guardian Communication

### Main Capabilities

- message teachers
- choose child context first
- continue structured conversation threads

### Why This Matters

This supports a more professional parent-teacher communication structure.

---

## Guardian Attendance Page

### Main Capabilities

- view attendance child by child
- enter deeper detail for a selected child

### Why This Matters

Attendance is one of the most requested parent-side visibility features in real institute use.

---

## Guardian Leaves Page

### Main Capabilities

- review pending leave requests from child side
- approve or reject child leave requests
- create leave directly on behalf of a child
- see bypass cases
- understand approval state

### Strong Workflow Point

Guardian-created leaves and student-created leaves are both handled meaningfully.

This supports real institute behavior instead of assuming only one submission path.

### Why This Matters

The guardian becomes part of the official leave flow rather than an informal outside confirmer.

---

## Guardian Marksheet Page

### Main Capabilities

- view marksheet for one child
- view marksheet for multiple children
- use latest-result preview before opening deeper marksheet

### Why This Matters

This increases academic transparency for families.

---

## Guardian Fees Page

### Main Capabilities

- view child challans
- view fee statuses
- upload payment proof
- follow dues more clearly

### Why This Matters

This reduces routine office calls about:

- whether a fee exists
- whether it is due
- whether proof has been reviewed

---

## Guardian Settings

### Main Capabilities

- profile
- password
- security
- notifications
- appearance

### Why This Matters

Guardians can maintain their own experience more independently.

---

## Guardian Role Summary In Plain Sales Language

The Guardian role turns Innovorix into a family-visible institute platform rather than an office-only system.

This is important for trust, convenience, and institute professionalism.

---

</details>

<details>
<summary><strong>Accountant Role And Finance-Focused Access</strong></summary>

# Accountant Role

## Accountant Role Summary

The Accountant role focuses on the financial operation side of the institute.

This role is intentionally more focused than the Admin role.

Instead of managing the entire institute, the Accountant role centers on:

- fee visibility
- fee processing workflows
- proof review workflows
- payment status handling

This is useful for institutes that want finance staff to work digitally without giving them broader academic control.

---

## Accountant Dashboard

### Main Value

The dashboard helps the accountant enter the finance side of the product quickly.

Even when a role has fewer modules than admin, a dedicated access path still matters for usability.

---

## Accountant Fees Page

### Main Capabilities

- access fee records
- review fee campaign outcomes
- handle collection-side visibility
- mark fee records as paid where role permissions apply
- review challans and statuses

### Why This Matters

For many institutes, the person handling fee collection should not also need full access to:

- class creation
- staff management
- institute settings
- promotion

The Accountant role solves that by staying finance-focused.

### Useful Finance Value

The Accountant can work inside a proper fee system that already supports:

- fee sessions
- fee campaigns
- challans
- statuses
- review-based payment updates

This is stronger than manually tracking collection updates in spreadsheets.

---

## Accountant Payment Proof Review Page

### Main Capabilities

- view pending proofs
- approve proofs
- reject proofs
- add notes
- review history
- filter reviewed records

### Why This Matters

For institutes using external or semi-external payment flows, this gives the finance side a proper approval station.

### Practical Benefits

- clearer accountability
- fewer “I already sent screenshot” disputes
- better review history
- cleaner paid versus pending distinction

---

## Accountant Role Summary In Plain Sales Language

The Accountant role gives finance staff a more disciplined digital collection workflow without opening up unrelated institute management areas.

That makes it easier to assign finance work safely inside the same platform.

---

</details>

<details>
<summary><strong>Librarian Role And Library Operations</strong></summary>

# Librarian Role

## Librarian Role Summary

The Librarian role focuses on running the library side of the institute cleanly.

Instead of giving librarians broad admin access, the role stays aligned to:

- book catalog handling
- circulation
- issue-return workflows
- overdue handling
- fine handling

This keeps library work efficient and secure.

---

## Librarian Dashboard

### Main Value

The dashboard acts as the entry point into the library workflow.

For a focused operational role, that matters because the role can move quickly into the relevant module without distraction.

---

## Librarian Library Page

### Main Capabilities

- manage book catalog
- add books
- edit books
- remove books
- issue books
- return books
- see currently borrowed books
- see overdue books
- use fine-aware return workflows
- manage circulation from one place

### Why This Matters

In many institutes, library work is either:

- barely digitized
- or managed in a tool disconnected from the main institute system

Innovorix improves that by keeping the library connected to the same broader environment.

### Fine Handling Value

Library overdue fine rules are not separate theory.

They connect into actual circulation handling.

That helps the librarian apply policy more consistently.

### Practical Benefits

- easier overdue tracking
- cleaner issue-return records
- more structured fine handling
- better member-level circulation awareness

---

## Librarian Role Summary In Plain Sales Language

The Librarian role gives an institute a real circulation workflow instead of a passive library register.

That strengthens the product’s image as a complete institute operations platform.

---

</details>

<details>
<summary><strong>Roles &amp; Permissions: Delegating Work A Job Role Does Not Cover</strong></summary>

# Roles &amp; Permissions

An institute's job roles are fixed, and the role a member of staff is created
with cannot be changed afterwards. Real institutes do not work that way: one
teacher runs exams for every class, another collects fees alongside the
accountant, a third is trusted to admit students and keep guardian records
straight. Before this there were only two answers, and both were wrong - make
the person an Admin and hand them everything, or leave them locked out.

**Settings → Roles &amp; Permissions** (Admin and SuperAdmin only) is where an
admin creates a **permission role**: a named bundle of extra abilities, such as
"Exam Controller" or "Fee Desk", that can then be given to whoever is doing that
work.

## The rule that makes it safe

A permission role **only ever adds**. It can never take an ability away from
anyone, so nothing that works today can stop working because a role was created
or assigned. Somebody holding one keeps everything their own job role allows and
gains what the role lists on top.

## Creating one

1. **What is it for** - a name staff will recognise, and a one-line description.
   The description is not decoration: it is what the person reads when a page
   they have never had before appears in their menu.
2. **What can it do** - a page-by-page grid, grouped into People, Academics,
   Money, Operations and Communication, with View / Create / Update / Delete
   boxes per page. Search, select-all and per-group counts keep it usable at
   twenty-one pages, on a phone as well as a desktop.

Every module carries a badge saying how much a tick is really worth:

- **Fully enforced** - Students &amp; Guardians, Fees and Exams. Every tick is
  checked on the server.
- **Page access only** - everything else. The tick adds the page and the menu
  entry; the buttons on that page still follow the person's own job role.

## Giving it to somebody

Two doors onto the same records, so they can never disagree:

- **Settings → Roles &amp; Permissions → Members** on the role itself, which also
  shows who else holds it.
- **Staff → edit a member of staff → Extra permissions**, right under the job
  role, which is locked after the account is created.

Only staff accounts can hold one. Students and guardians are refused on the
server, not only hidden in the picker, because giving a family the roster would
show them every other family's records.

**Pausing** a role (the Active switch) stops it granting anything while keeping
the list of who held it, so a delegation can be suspended for a term and handed
back untouched. **Deleting** one says how many people lose how many pages before
it does anything, and offers pausing instead.

## What the person sees

Pages their job role does not include appear in their own **Delegated to you**
block at the foot of the menu, with a key icon and an amber accent. Hovering one
says which role granted it and exactly what it allows - "Your administrator gave
you the Exam Controller role, which adds this page: full access. Your own Teacher
role does not include it."

Where they already had the page, nothing is duplicated; the page simply widens.
A teacher given Exams stays on the same Exams page but now sees every class in
the institute, can create an exam for any of them, and gets the datesheet and
history controls that were previously administrator-only. What they may **type
marks into** is unchanged: running an exam for a class is not the same as marking
a subject you do not teach.

A grant reaches the person within five minutes without them signing out, and is
withdrawn just as quickly.

## In the demo institute

- **Exam Controller** → Demo Teacher (`teacher@demo.innovorix.com`)
- **Fee Desk** → Nadia Aslam, working alongside the real accountant
- **Front Desk** → the librarian, admitting students
- **Exam Controller (last year)** → paused, so the paused state has an example

---

</details>

<details>
<summary><strong>Student Risk Detection, Early Warnings, And Child Wellbeing</strong></summary>

# Student Risk Detection

## Purpose

A dedicated early-warning page that proactively flags students who may need intervention, instead of leaving staff to notice problems by hand once they're already serious.

---

## How Risk Is Measured

Each student gets a 0-100 risk score blended from three factors, each weighted:

- **Attendance Risk (40%)** — low or declining attendance
- **Academic Risk (35%)** — low or falling grades, failed assessments
- **Financial Risk (25%)** — overdue fees and late payments

The score is banded as 0 No Risk, 1-24 Low, 25-49 Medium, 50-74 High, 75-100 Critical, shown with green through red badges.

A factor with no data is shown as "Insufficient data" and left out of the score, with the remaining factors reweighted, so missing data never inflates or lowers a student's risk.

Attendance follows the institute-wide rule: approved leave is excluded from the calculation entirely, so a student who was legitimately away is never counted as absent and is never flagged for it. A student with no countable attendance days simply has no attendance risk rather than a misleading zero.

The time range is adaptive (Last 7 Days / 30 Days and so on, based on institute age), and a previous-period comparison drives **alerts**: _Needs intervention_, _Newly flagged_ (became a concern this period), and _Escalating_ (risk rising).

---

## How A Reader Understands The Numbers

The page states the full formula in plain English above the table, and every risk badge explains itself on hover or keyboard focus: the band it falls in, the numeric range of that band, and the exact signals that produced it for that student.

---

## Who Sees What

- **Admin / SuperAdmin / Accountant / Librarian** — all students school-wide, in a filterable, sortable table (filter by class, section, risk level, and minimum score) with alert summary cards.
- **Teacher** — only students in their assigned classes, same table view.
- **Guardian** — only their own children, in a supportive card view ("Doing well" / "Needs attention") with a short "what you can do" hint per child, with no alarming wording.

The role used for that scoping is taken from the signed-in session, never from the browser, so no one can request a wider view than their role allows.

The whole page loads from a single backend request and refreshes in one request when the range changes.

---

</details>

<details>
<summary><strong>Merit List And Topper Management</strong></summary>

# Merit List

## Purpose

The toppers of an exam, worked out the way medals are actually awarded on result day: inside each class and section, inside each class, or across the whole exam, instead of comparing class marksheets by hand.

---

## How It Works

Pick an exam and the page brings up the classes that exam is linked to, every one ticked to start with. Untick a whole class or a single section to leave it out, then press **Generate**.

**Award positions** decides what a place is measured within:

- **Per class and section** (the default) gives every class-section box its own first, second and third place. This is what result day needs: with ten classes you no longer have to pick one class, generate, read the top three, and repeat ten times.
- **Per class** ranks inside each class with all of its sections together.
- **Whole exam** is the single combined leaderboard across everything ticked.

Every group is shown at once, each with its own ranking restarting at 1, and each heading explains on hover exactly what its places are measured within. Students in a class with no section assigned get a group of their own rather than disappearing.

**Places that count as a medal** is a box, three by default. It controls both the highlighting on screen and what goes into the download. Students level on score share a place, so a tie for second produces two second places.

**Download toppers** produces a printable sheet of the medal winners, grouped exactly as shown, ready to print and hand out. Each group is kept whole on a page rather than being cut in half across two.

---

## How The Ranking Is Calculated

A student's score is the marks they obtained across the exam's papers, out of the marks those papers were worth, and the list runs from the highest percentage down.

- **Missing papers are never scored as zero.** The percentage covers only the papers the student actually sat, and every row shows "papers sat of papers their class sat". Because three papers out of eight cannot be compared fairly with eight out of eight, those students are left out of the ranking by default; a switch brings them back in, flagged **Incomplete**, with the missing paper names on hover.
- **"Their class's papers"** means the papers that class actually sat in this exam, so a junior class taking fewer subjects is never wrongly marked incomplete against a senior one.
- **Ties share a rank and the next rank skips** (1, 2, 2, 4). Nothing breaks a tie; tied rows are simply listed by name.
- **Students admitted after the exam's last paper never appear at all** — they were never enrolled for it, so they are not ranked and not counted as absent.

Every one of those rules is printed in plain English above the table, and hovering or focusing a rank or a score explains that student in particular: their total, out of what, over how many papers, and the exact gap to the students above and below them.

---

## Who Sees What

- **Admin / SuperAdmin / Teacher / Accountant** — the full merit list for their own institute (SuperAdmin across institutes).
- **Student / Guardian / Librarian** — no access; the page exposes every listed student's marks.

The role and the institute are read from the signed-in session, never from the browser, so a request for another institute's merit list returns nothing.

The page is read-only: it never creates or changes a mark. Building a list costs a fixed number of database queries whether the exam has five students or five hundred.

---

</details>

<details>
<summary><strong>MCQ Arena: Daily Quizzes, Titles, Streaks And The Public Question Bank</strong></summary>

# MCQ Arena

## Purpose

A free practice ground using the saved multiple choice question bank (General Knowledge, Pakistan and World Current Affairs, Pak Study, Islamic Studies, Everyday Science, Computer, English, Past Papers), playable by anonymous visitors on the public site and by every signed-in role in the dashboard. Solving is a game: XP, an eight-step title ladder from Newcomer to Legend, and a daily streak that resets when a day is missed.

---

## The Public Side

The **MCQs** item in the site navigation opens the free practice pages. Every subject can be read through page by page with answers behind a "Show answer" reveal, or played as a ten-question quiz with no account. Visitors can leave an email to receive one reminder each afternoon, with a one-click unsubscribe link in every mail. Subjects whose content goes stale (General Knowledge, Current Affairs) are marked **Dated content** and show when their bank was last updated, because office holders and records change.

---

## The Dashboard Side (MCQ Arena)

Every role gets the arena page: solve quizzes by subject, watch a thirty-day chart of questions per day and accuracy, and see the school's student leaderboard. Signed-in users can switch on a daily reminder and pick the hour; it arrives as an app notification only on days they have not solved yet.

- **Students** earn XP and titles; the title and live streak appear next to their name on the attendance page, on their profile, and to their guardian.
- **Guardians** see each child's title, streak and activity chart first, with a nudge to trade social media minutes for one quiz a day. Guardians can solve too.
- **Teachers and admins** additionally see school participation numbers and can upload their own subject's questions as a CSV (a sample file is provided). Uploads stay private to the school and mix into that school's quizzes only.

---

## Monitoring And Moving To A New Machine

Super admins open **MCQ monitoring** in the platform menu to see all subscriptions, active questions, the last worker check and 30-day quiz activity. Institute admins open the same item in their institute menu and see only linked users and activity from their own institute. Search, subscription status and pagination make individual subscribers easy to find. Reminder checks record sent, skipped, unavailable and failed counts; individual failures include a subscription identifier in the server logs.

Reminders pause when no accessible category can supply ten active questions. Public email signup also pauses when the shared bank cannot supply a full quiz. The worker checks at startup and hourly, and emails active super admins at most once per recipient per Pakistan calendar day after a successful alert. Failed alerts remain eligible for retry. `/api/health` also checks the question bank and recent worker activity, so a connected but empty database cannot pass the MCQ health check.

MCQ reminder, welcome and alert emails use **Innovorix <mcqs@innovorix.com>**. Set `MCQ_FROM_EMAIL` to override that address and `MCQ_FROM_NAME` to override the display name. Add this address to Cloudflare Email Routing and verify it as a sending alias for the configured SMTP account before sending emails from it. Other email senders retain their existing settings.

The repository carries the real question source files in `prisma/data/mcqs/`. Each CSV uses `Question,Option A,Option B,Option C,Option D,Correct Answer`, with the correct answer as A, B, C or D. Keep questions containing commas inside quotes. The expected filenames are `general_knowledge_mcqs.csv`, `pakistan-current-affairs-mcqs.csv`, `world-current-affairs-mcqs.csv`, `pak-study-mcqs.csv`, `islamic-studies-mcqs.csv`, `everyday-science-mcqs.csv`, `computer-mcqs.csv`, `english-mcqs.csv` and `past-papers.csv`. Send these files together as a ZIP from the old machine. The restored bank contains 21,041 validated unique questions. Another 94 source rows with invalid or missing answers are preserved in `prisma/data/mcqs/rejected-rows.csv` for review and are excluded from seeding. Do not guess their answers; correct them from the original source before adding them back to the matching category CSV.

Run `npm run db:seed:mcqs` to add missing shared questions without changing users, subscriptions or quiz history. The full seed uses the same importer and validates the bank before changing demo data. Empty or invalid source files produce a clear failure rather than a misleading success. Question hashes and database duplicate checks make repeated imports safe. Existing questions are preserved; inactive or institute-private duplicates may need review before they can serve as shared questions. Commit the source files with the project so they travel to the next machine.

Open Trivia Database questions are downloaded with `npm run mcqs:fetch:opentdb`. The background worker saves each batch into category JSON files under `prisma/data/mcqs/opentdb/`, so a stopped job resumes from saved progress. It waits 10 seconds between API requests, retries temporary connection failures, and writes a master export, manifest and log when complete. Fetching does not change the database. When the download is complete, run `npm run mcqs:seed:opentdb` to import the saved questions, or add `--refresh` to `python3 scripts/fetch-opentdb.py` to check the API bank again later. The API allows up to 50 questions per request, limits each IP to one request every five seconds, and licenses its question data under CC BY-SA 4.0. The category pages carry the source and license credit; keep the downloaded source files and manifest together when backing up the project.

---

## How Scoring Works

Each correct answer earns 10 XP and a perfect quiz adds 20 XP. Only the first three quizzes a day earn XP; after that, play is unlimited but unscored. Solving at least one quiz a day grows the streak; a missed day resets it to zero. Titles are unlocked at fixed XP thresholds and every derived number on the page explains itself on hover.

---

## Why Copying Does Not Work

Every attempt draws its own random questions from the bank and shuffles the answer order, and the grading happens on the server against the served set. Two students sitting together get different quizzes, so reading a neighbour's results is pointless, and the daily XP cap means one afternoon of grinding (or solving on a sibling's profile first) cannot buy a rank. An attempt started by one account can never be submitted by another.

</details>

<details>
<summary><strong>Student Fee History, Previous Balance, And Arrears Carried Forward</strong></summary>

# Student Fee History And Previous Balance

## Purpose

A student's page ends with a full fee ledger, so "what does this family still owe, and what have they already paid?" is answered on the student rather than by scanning the whole institute's fee list.

---

## What It Shows

Every fee challan ever issued to that student, oldest first, with the amount billed, the amount paid and the date it was paid, what is still owed on it, and a running **balance carried forward** so arrears from earlier months are visible at a glance.

Above the table sit four totals: total billed, total paid, outstanding balance, and the share collected. An overdue flag appears when an unpaid challan has passed its due date.

The section is read-only. It never creates, recalculates or settles a fee.

---

## Part Payments

A challan can now be paid in instalments. Each payment the office receives is stored on its own, so the "paid" figure on a row is the sum of the payments actually recorded against that challan and the row shows what is still owed. A part-paid challan is labelled **Part paid** and deliberately stays Due or Overdue, so it keeps appearing in defaulter follow-up until it is covered in full.

Challans settled before instalments existed carry no itemised payments and still count as paid in full, so nothing in this ledger changed for them.

A payment a family has reported but the office has not yet confirmed is still shown as owed, together with its reference number.

---

## How A Reader Understands The Numbers

The formula is stated in plain English under the heading: "paid" on a row is the sum of the payments recorded against that challan, so a challan can be part paid; it counts as fully paid only once those payments cover it or the office marks it paid outright, and waived when the school writes it off; outstanding balance is total billed minus total paid minus total waived; a challan turns overdue once its due date has passed and something is still owed.

Hovering or keyboard-focusing any total, badge or balance explains that specific value: which challans contributed, how much each still owes, and for an overdue one how many days past its due date it is.

---

## Who Sees What

- **Admin / Accountant** any student in their own institute.
- **SuperAdmin** across institutes.
- **Student** only their own ledger.
- **Guardian** only their own children.
- **Teacher / Librarian** no access, matching the fact that neither role has a Fees page today.

The role, the identity and the institute all come from the signed-in session on the server, and the requested student is re-checked against the caller before any figure is returned. Students and guardians keep the existing rule that challans belonging to a draft fee session stay hidden.

The whole section costs two database queries, never one per challan.

---

</details>

<details>
<summary><strong>Fee Instalments And Recording Part Payments</strong></summary>

# Paying A Fee In Instalments

## Purpose

Families often pay a challan in pieces. Before this, a challan could only be fully paid, fully waived, or fully owed, so an office taking half the money had nowhere to put it and had to either mark the whole challan paid or pretend nothing had arrived.

---

## How It Works

A challan still records what is **owed** and never changes. Every payment received against it is recorded separately with its amount, the date it came in, the method (cash, bank transfer, cheque, card, online, other), an optional reference or receipt number, and who in the office entered it.

"Paid so far" is always the sum of those payments, so there is no second total that can drift out of step with the receipts.

A challan is marked **Paid** only once the payments cover it in full. A part payment never settles a challan: it stays Due or Overdue so it keeps showing up in defaulter reports and reminders, and it gains a **Part paid** label so nobody mistakes it for untouched. A waived challan takes no payment at all, and a challan that is already settled refuses further payment.

Paying more than the challan is accepted and recorded in full, shown as an over-payment rather than a negative balance.

---

## Where To Do It

On the fee list for a class, the row menu (or the card button on a phone) has **Record Payment**. It opens the challan's payment history, shows the challan amount, what has come in and what is left, and pre-fills the amount with the outstanding balance so settling the rest is one click and an instalment is just a smaller number typed over it.

The fee list itself shows the split on any part-paid challan, so the state is visible without opening anything.

---

## How A Reader Understands The Numbers

The rule sits in plain English at the top of the dialog, and hovering or keyboard-focusing any figure explains that specific value: how much came in across how many payments, why the remaining amount is what it is, and why the challan has or has not moved to Paid.

---

## Who Can Do It

Admin, Accountant and SuperAdmin only. The role and the institute are read from the signed-in session on the server, never from the page, and every challan is re-checked against the caller's own institute before anything is written. Recording a payment and updating the challan happen together, so one can never land without the other.

Money is handled in whole paisa throughout, so no rounding error can leave a challan looking a paisa short of settled.

---

</details>

<details>
<summary><strong>Mobile App, Mobile Experience, And Notification Readiness</strong></summary>

# Mobile Experience In More Detail

## Why Mobile Matters So Much

A platform can have excellent features and still fail in day-to-day adoption if mobile usability is weak.

That is especially true in education environments because:

- teachers move around
- guardians prefer phones
- students often use phones first
- institute staff may need quick updates from outside office desks

Innovorix addresses this reality directly.

---

## Mobile Navigation

The product includes mobile-specific navigation behavior so users can reach the most important areas more quickly on smaller screens.

This is important because mobile usage should not feel like a shrunken desktop dashboard.

It should feel intentionally usable.

---

## Mobile Role Experience

### Student Mobile Experience

Students get fast access to:

- dashboard
- timetable
- assessments
- settings
- mobile menu

### Guardian Mobile Experience

Guardians get quick mobile access to:

- dashboard
- attendance/children view
- leaves
- menu
- settings

### Teacher Mobile Experience

Teachers get quick mobile access to:

- dashboard
- timetable
- attendance
- menu
- settings

### Admin And Operational Mobile Experience

Admin and operations-focused roles still benefit from a mobile-friendly dashboard and responsive layout even when they do more complex work on desktop.

---

## Mobile Notifications And Permissions

The project includes mobile permission and push-notification-aware flows.

This helps the product function as a more active institute app rather than a passive website.

Examples of where this matters:

- message alerts
- fee-related updates
- institute notices
- communication reminders

---

## Native Android App Direction

The platform includes Android build support with a native packaging flow.

This gives institutes a stronger app-story in sales and delivery discussions.

It means the product can be positioned not only as:

- a website
- or a browser dashboard

but also as:

- a native-style Android app experience

---

## Progressive App-Like Experience

The product also includes standalone application-style behavior through installed web experience support.

This helps users experience the system more like an app and less like a traditional tab-heavy website.

---

## Mobile-Friendly Product Positioning

For marketing teams, a strong positioning line can be:

`Innovorix is built for real institute usage across office desks, teacher routines, and guardian phones.`

Another good line can be:

`It is not only rich in features. It is usable in the places where institute work actually happens.`

---

</details>

<details>
<summary><strong>Hidden Strengths, Institute Value, Use Cases, Marketing Angles, And Sales Support</strong></summary>

# Hidden Product Strengths Worth Mentioning In Marketing

The following points are especially useful in marketing or sales explanation because they show the product is thoughtfully built.

## Hidden Strength 1: Fee Session Duplication

Recurring fee cycles can be duplicated from earlier sessions.

This reduces repeated setup work.

It is one of the most practical “double work reduction” features in the system.

## Hidden Strength 2: Draft Fee Sessions

Fees can be prepared first and activated later.

That gives the institute more control before making fee cycles live.

## Hidden Strength 3: Payment Proof Review Flow

The platform supports a controlled proof review process instead of leaving finance work to screenshot chaos.

## Hidden Strength 4: Fee Defaulter Recovery Page

Overdue recovery is not hidden inside general fee tables.

It has its own working page.

## Hidden Strength 5: Timetable Auto-Continuation

When adding timetable slots, the system can continue the next slot from the previous time structure.

This saves effort in repetitive timetable creation.

## Hidden Strength 6: Roll Number Conflict Resolution

The product supports both swap and auto-resolve logic.

This is a high-value operational convenience feature.

## Hidden Strength 7: Section-Aware Bulk Promotion

Promotion is not only class-level.

It supports section-level destination control too.

## Hidden Strength 8: Linked Institute Logic

Classes, teachers, attendance, exams, fees, and communication are connected.

This reduces repeated manual mapping across modules.

## Hidden Strength 9: Strong Parent Side

Guardian access is not an afterthought.

It includes fees, leaves, attendance, results, and communication.

## Hidden Strength 10: Institutional Credential Standards

The institute can define credential patterns for students, staff, and guardians.

This helps scale cleanly.

---

# Institute Value By Department

## Value For Institute Leadership

- better operational visibility
- stronger digital discipline
- better parent-facing professionalism
- more centralized oversight

## Value For Admissions Teams

- cleaner student creation
- linked guardian setup
- admission fee support
- credential generation

## Value For Academic Teams

- class and timetable structure
- assessment management
- exam workflow
- marksheet visibility
- promotion workflow

## Value For Finance Teams

- fee sessions
- fee campaigns
- challans
- payment proof review
- defaulter workflow
- late fee logic

## Value For Teachers

- class-focused pages
- attendance
- academic work handling
- marks entry
- timetable visibility

## Value For Guardians

- transparency
- easier follow-up
- child progress visibility
- communication access

## Value For Librarians

- circulation workflow
- overdue awareness
- fine-aware returns

---

# Institute Journey Through The Product

This section describes how an institute may naturally live inside Innovorix over time.

## At The Start Of The Session

- staff is created
- classes are set
- subjects are defined
- timetable is built
- students are admitted
- guardians are linked
- fee cycles are prepared

## During Daily Operations

- attendance is marked
- assignments are given
- fees are viewed
- notices are posted
- communication happens
- leaves are reviewed

## During Exam Periods

- exam sessions are created
- datesheets are visible
- marks are entered
- progress is monitored
- marksheets are later viewed

## During Fee Collection Periods

- challans are issued
- statuses are tracked
- payment proofs are reviewed
- defaulters are filtered
- reminders are sent

## During Year-End Transition

- results are checked
- promotions are prepared
- promotions are executed
- history remains attached to records

This is one of the easiest ways to understand the depth of the product:

it supports the institute across the whole operational cycle, not just one isolated office task.

---

# Practical Use Cases

## Use Case: A Monthly Fee Cycle

The institute creates a monthly fee session.

If it already created a previous month, it can duplicate that earlier session.

Campaign names, components, class selections, and due dates can already be suggested.

The institute then:

- reviews
- confirms
- activates if needed
- lets students and guardians view challans
- reviews payment proofs
- follows up on defaulters

This is a very strong sales story because it shows both planning and execution value.

## Use Case: Parent Asking About Child Progress

Instead of the office manually checking:

- attendance register
- fee note
- exam file

the guardian can often view:

- attendance
- fees
- marksheet
- leave status

directly.

This reduces friction.

## Use Case: Teacher Managing Daily Work

The teacher logs in and quickly sees:

- classes
- students
- timetable
- attendance
- grading work

The teacher does not need to navigate an admin-heavy environment.

## Use Case: Office Managing Promotions

At year end, the office can:

- run class-to-class promotions carefully
- or manage larger promotion operations in bulk

This saves time compared with manually editing student records one by one.

## Use Case: Library Running More Formally

The librarian can:

- issue books
- return books
- track overdue cases
- apply rule-based fine logic

This makes the library function look more professional and controlled inside the same institute system.

---

# Why The Product Feels More Mature Than A Basic ERP

There are many reasons, but these stand out:

- role-based clarity
- workflow states
- mobile thinking
- fee duplication logic
- proof review logic
- defaulter handling
- section-aware promotion
- guardian involvement
- integrated communication
- configurable identity standards

This means the product feels closer to an operational platform than a simple record database.

---

# Positioning Statements For Marketing Content

The following lines may help a marketing team create brochures, website copy, or pitch decks.

## Positioning Line 1

Innovorix helps institutes run academics, fees, communication, and daily operations from one connected platform.

## Positioning Line 2

Innovorix is built for institute management that is practical, parent-visible, and mobile-ready.

## Positioning Line 3

From admissions to promotion, Innovorix supports the full institute workflow.

## Positioning Line 4

Innovorix reduces paper work, repeated setup work, and scattered communication through one disciplined digital system.

## Positioning Line 5

It is not only an admin panel. It is a working digital ecosystem for institutes.

## Positioning Line 6

Innovorix gives management control, teachers focus, finance structure, and guardians transparency.

---

# Sales Talking Points By Feature Theme

## Theme: Efficiency

- recurring fee sessions can be duplicated
- timetable slots can be built faster with continuation logic
- import/export workflows reduce migration friction
- bulk actions reduce repetitive staff effort

## Theme: Transparency

- guardian visibility is meaningful
- fee statuses are clearer
- proof review states are clearer
- leave approval states are clearer

## Theme: Control

- role-based access
- draft and active fee states
- review history
- promotion tracking
- settings-driven institutional behavior

## Theme: Professionalism

- structured communication
- structured marksheet access
- structured approval flows
- structured library circulation

## Theme: Adoption

- mobile-friendly usage
- role-based simplicity
- focused pages for each operational user

---

# If Someone Asks “What Makes Innovorix Different?”

A strong answer would be:

Innovorix is different because it combines broad institute coverage with practical workflow intelligence.

It is not only broad.

It is operationally thoughtful.

That shows up in features like:

- duplicate next fee session wizard
- draft fee sessions
- proof review and defaulter handling
- timetable slot continuation
- section-aware promotion
- roll number conflict resolution
- guardian-integrated leave handling
- institutional ID and password pattern control

---

# If Someone Asks “Who Uses It Day To Day?”

The day-to-day users can include:

- admin officers
- branch operations staff
- teachers
- class in-charges
- finance staff
- librarians
- students
- guardians

This broad role support strengthens the business value of the platform because it drives use across the institute ecosystem.

---

# If Someone Asks “What Problems Does It Replace?”

Innovorix helps replace or reduce dependence on:

- paper fee registers
- manual result files
- scattered WhatsApp communication
- disconnected guardian follow-up
- repetitive monthly fee setup
- unclear leave approval processes
- weak class-level student visibility
- manual year-end promotion handling
- separate book issue notebooks

---

# If Someone Asks “What Is The Best Module To Demo First?”

That depends on the prospect.

## For Management

Start with:

- dashboard
- students and guardians
- fees
- promotion

## For Finance-Focused Prospects

Start with:

- fees
- payment proofs
- defaulters

## For Parent-Transparency-Focused Prospects

Start with:

- guardian dashboard
- child attendance
- child fees
- child marksheet
- communication

## For Academic-Focused Prospects

Start with:

- classes and timetable
- attendance
- assessments
- exams
- marksheet

---

# Expanded Summary Of Every Main Module

The following summaries are intentionally more descriptive for teams that want a longer reading version.

## Dashboard Summary

The dashboard is the first operational layer of the product.

It is where users land and where they understand the shape of their work.

Instead of presenting one generic dashboard to all roles, Innovorix adjusts the dashboard according to role context.

This matters because:

- management needs oversight
- teachers need class focus
- students need personal visibility
- guardians need child visibility

That role sensitivity improves usability and adoption.

## Staff Summary

The staff area is where institute personnel become digitally organized.

The institute can onboard teachers and non-teaching staff, maintain active and inactive states, and keep records centrally.

Because teacher timetable and class assignment become visible around this area, the page does not feel like a dead record table.

It stays operationally useful.

## Student And Guardian Summary

This is the heart of the user-side data structure.

A strong institute ERP needs more than student names.

It needs:

- linked family relationships
- class placement
- admission logic
- credential logic
- lifecycle updates

Innovorix supports that in a practical way.

## Classes And Timetable Summary

This is where academic structure is turned into usable institute operation.

Without this area being strong, teacher views, attendance, and exam logic all become weaker.

Innovorix strengthens it through section-aware logic, direct assignment, timetable building, and import/export support.

## Attendance Summary

Attendance is one of the highest-frequency workflows in any institute.

It must be:

- quick
- clear
- reportable
- role-aware

Innovorix gives the institute all of those.

## Leaves Summary

Leave handling is often messy in educational environments.

Innovorix formalizes it without making it rigid beyond practicality.

That is an important balance.

## Assessments Summary

Assignments and quizzes often create daily academic noise if not structured properly.

Innovorix gives teachers and students a cleaner workflow around them.

## Exams Summary

Formal evaluations need strong structure.

Session grouping, progress handling, grade validation, and datesheet visibility all make this module more credible and mature.

## Marksheet Summary

Results only become useful when they can be retrieved clearly.

Searchable marksheet access helps office teams, students, and guardians.

## Fees Summary

This is one of the strongest product areas.

The fee module is not only a payment list.

It is a true fee operations module.

That distinction matters in product quality.

## Library Summary

The library area extends Innovorix beyond mainstream basic institute ERP claims.

It helps the product feel more complete.

## Promotion Summary

Promotion support is a very important year-end capability that many institutes care about operationally.

Single and bulk modes make the product more practical.

## Communication Summary

Communication becomes more institutional and less fragmented.

That is valuable for discipline, record keeping, and professionalism.

## Settings Summary

A strong settings area turns a product into an institution-ready platform.

Innovorix gives the institute meaningful control over policies and patterns, not just cosmetic preferences.

---

# Recommended Marketing Themes For Innovorix

The marketing team can build campaigns around the following themes.

## Theme 1: Full Institute Control

Use when targeting leadership.

Suggested message:

Run admissions, academics, fees, communication, and year-end promotion from one connected institute system.

## Theme 2: Better Parent Transparency

Use when targeting family-oriented institutes.

Suggested message:

Give guardians clear access to attendance, fees, leave updates, marksheets, and communication.

## Theme 3: Less Repeated Office Work

Use when targeting admin-heavy pain points.

Suggested message:

Reduce double work through bulk actions, fee duplication workflows, templates, and smarter setup flows.

## Theme 4: Strong Mobile Experience

Use when targeting modern adoption.

Suggested message:

Innovorix is built for day-to-day institute use on desktop and mobile, not just back-office screens.

## Theme 5: Better Fee Discipline

Use when targeting finance pain points.

Suggested message:

From challans and payment proofs to defaulters and reminders, Innovorix helps institutes manage fees with more control.

---

# Recommended Sales Demo Order

If a full demo is too long, the strongest compact path may be:

1. dashboard
2. students and guardians
3. classes and timetable
4. fees
5. payment proofs
6. defaulters
7. guardian side
8. promotion
9. mobile story

If the audience is more academic, use:

1. classes
2. attendance
3. assessments
4. exams
5. marksheet
6. guardian visibility

If the audience is more finance-led, use:

1. fees
2. duplicate next session flow
3. payment proofs
4. defaulters
5. accountant role

---

# Final Product Understanding

Innovorix is best understood as a connected institute operating platform.

It is strong because it covers the major institute workflows across:

- management
- academics
- finance
- family visibility
- operations

It is attractive because it includes not only broad module coverage, but workflow intelligence.

It is practical because it supports:

- daily execution
- role-based usability
- mobile usage
- structured approval flows
- recurring operational tasks

It is commercially interesting because it gives a marketing team many real product stories to tell:

- institute control
- parent transparency
- teacher productivity
- fee discipline
- mobile readiness
- academic structure

And it is operationally meaningful because it can support the institute from:

- setup
- to daily usage
- to fee recovery
- to result handling
- to year-end promotion

That combination is what makes Innovorix more than a basic institute record system.

It makes it a working digital environment for institute operations.

---

## Closing Positioning Line

Innovorix helps an institute manage people, academics, finance, communication, and progress in one disciplined, mobile-ready, role-based platform.

</details>

<details>
<summary>Public landing and registration</summary>

Public pages show the current offer terms without a seeded registration total or counter implementation explanation. The internal campaign calculation and eligibility remain unchanged. Plan cards show current allowed pages, with Growth and Pro listing additions to the preceding tier only when all its pages are included. Student, teacher, class and location capacities come from the catalogue. Existing institutes retain their saved agreement. Starter is presented as free without a lifetime marketing promise. The pricing page has a student-count finder, monthly and yearly prices, a horizontal Enterprise option and the full access comparison. Pakistan visitors see rupees and other visitors see dollars. A supplied country header takes priority; when absent, the browser time zone resolves the initial currency before prices appear. Visitors can change the currency, and the selected currency and billing length follow them into signup or institute settings. A branding playground previews the institute name and colour on sample cards and challans; its aligned custom colour picker shares the preset row, and the real QR code opens https://innovorix.com without a visible website caption. Both samples use M Haroon Hamid. Pro highlights white labelling, 24/7 support and document branding, while Enterprise remains an explicitly named horizontal plan. The public page does not advertise data exports or unverified retention and backup promises. A location capacity of zero means unlimited throughout plan saving, branch creation and pricing displays. New Enterprise definitions use unlimited locations; saved agreements retain their explicit values. The About heading renders its complete wording immediately, with one heading element before and after hydration. The comparison page uses a feature matrix with linked vendor sources, a highlighted Innovorix column, current plan availability and horizontal scrolling within the table on phones. Demo and pricing actions stay beside each other at matching heights.

</details>

<details>
<summary>Loading feedback for account actions</summary>

Login, signup, the live demo and the contact form erase their own button labels while waiting; verification and password recovery also show loading feedback. Signup and login buttons rotate reassuring messages without claiming a completion percentage. Failed or stalled requests restore a retry, and navigation feedback clears on arrival, browser return or timeout.

</details>

<details>
<summary>Public institute guides and software comparisons</summary>

The public comparison at `/compare` links to official eSchool, EduOffice, Skoo and Academia UMS sources reviewed on 29 October 2026. It distinguishes vendor descriptions from demonstrated capabilities and reads Innovorix prices, allowed pages and capacities directly from the current catalogue. Existing institute agreements are preserved.

The blog includes eight original Pakistan guides for school, college and university buyers, fee recovery, admissions, attendance, parent communication and BISE/FBISE preparation. Each body contains more than 1,500 words. Titles, summaries and body word counts produce the displayed reading estimate at 200 words per minute. The shared article route provides a unique canonical, article metadata, BlogPosting and breadcrumb data, related guides and links to current pricing and public MCQ practice. The sitemap includes only published public routes. Unknown article slugs return 404.

Public navigation links to Blog and Compare, with a mobile menu below the width needed for the desktop links. The blog index no longer claims an unverified number of institute customers. Signup welcome messages read the accepted agreement and do not give a non-expiring plan a trial deadline.

Query research, sources, publication URLs, the ChatGPT follow-up prompt and owner indexing steps are in `docs/pakistan-seo-content.md`. Ranking, indexing and AdSense approval remain Google decisions. No ads or ad invitations were added to pricing, signup, checkout or comparison pages.

</details>

<details>
<summary>Help button in the header</summary>

Admins and super admins see a **Help** button in the header of every signed-in page: an icon with an accessible label on a phone, icon and text on a larger screen. It opens the Help Center side panel with the guides for the page they are on, so Fees opens the fee guides and Exams the exam guides. A page with no guides of its own opens the general getting-started set (the first-time setup order and what the system does). The Help Center pages do not show the button, because they are the guides.

The pages that already had a "Need help?" button keep it. Those buttons can be specific to a tab, while the header button covers the whole page. Other roles do not see help, as before. The page-to-guides list is `src/lib/help/route-help.ts`.

</details>

<details>
<summary>Import while creating students and staff</summary>

Both Basic and Advanced creation forms keep an Import button at the left of their footer. It opens the existing file validation and import workflow without discarding the form underneath. Export stays in the main page menu. Institute permissions still apply; when bulk operations are disabled, the form action explains why it is unavailable.

</details>

<details>
<summary>Confirm class destinations before importing students</summary>

The student import preview shows each file class and section, its student count, and the saved destination. Change the destination before importing when needed. Similar names match existing classes when the match is clear; ambiguous names and sections require a selection. New classes are disabled by default and require explicit selection and permission. Queued imports and retries keep the chosen destination. Existing duplicate classes are not merged automatically.

</details>

<details>
<summary>Enter historical fees without automatic notifications</summary>

Fees outside the school's current month and year are saved without automatically notifying students or guardians, including future months. A named monthly session identifies the billing month; other sessions use each saved voucher's due-date month. Draft sessions stay quiet. The creation form and session page explain this default, and a confirmed **Send notifications** action lets an administrator announce the saved session explicitly. Existing school delivery preferences and notification delays still apply.

</details>

Dependency security remediation and the complete alert inventory: [Dependabot remediation](docs/dependabot-remediation.md).

<details>
<summary>Terms, privacy and cancellation pages</summary>

The three legal pages share a responsive reading layout, section navigation, links between documents and contact access. Their displayed dates remain December 1, 2025. Free-plan terms cover changing limits, optional sponsorship, at least thirty days of notice for material commercial changes, payment authorization, protection of recorded institute agreements and renewal pricing. Privacy wording excludes sensitive educational records from behavioural advertising and preserves age-appropriate safeguards. These provisions do not install advertising or create automatic charges.

</details>

<details>
<summary>Owner layout controls</summary>

The image-storage label, explanation and toggle share one row. The registered-institutes title, searchable filter and Add action also share one row, including narrow screens. The Add action opens the existing institute-creation page.

</details>

SuperAdmin can manage full-feature trials under **Plans and institute agreements**. Choose
future defaults to set trial days (30 by default, 0 disables new automatic trials), or select
any institute to save an exact end date, add six calendar months to the draft date, or end its
trial. Temporary module access expires automatically and returns to the saved agreement. Trial
changes do not alter paid validity, prices or capacity limits.

<details>
<summary>College workspace, principal monitoring and student enquiry</summary>

The optional college workspace combines floor-scoped staff access, invitation
onboarding, teaching-day monitoring, configurable admissions, complete student
history and institute branding. Teachers can check in, hand over or take over
lectures when enabled by the administrator; conflicts and corrections are
recorded. Principal reports separate original assignments and actual conducted
lectures for payment review. Existing permission roles can be managed from the
college settings.

Classes also offers an editable campus view with twelve shapes (single row, double
row, L, U, V, round, T, H, E, closed courtyard, plus and a custom grid), live room
details, filtered activity and a floor editor with an immediate preview. Arrange
rooms lets an administrator drag a room to an empty place or onto another room to
swap them, paint new classrooms, stairs, offices, canteens and open spaces, rename
rooms and floors, link a class or section and undo each step before one save.
Customise shape freely turns any template into a grid whose floor outline follows
the rooms. Room labels show the linked class with its section on a second line,
the room name or a room number, and are also set in Settings, Floors and classes.
Full screen keeps filters, menus, dialogs and Campus activity working. The studio
needs a screen at least 1,024 pixels wide; phones keep the class cards and explain
why when Building view is pressed. Building view and Class view buttons
transition between the two views and preserve unsaved building drafts. The
building title, viewing tools and grouped editing actions share the available
desktop width. Saved attendance uses the same local date as the Attendance page,
including across midnight. Records refresh every 30 seconds. **Real-time logs**
starts off and checks every 3 seconds when enabled; **Refresh records** checks
immediately. Checks pause in a hidden tab and refresh when you return, without
interrupting slower requests. Room details and the room list show saved attendance,
and Campus activity includes attendance saves grouped by class, section and status.
Only applicable tools are shown. The building
is loaded on demand and can become the institute's default view.
Horizontal dragging turns the front of the building with the pointer; left and
right arrow keys follow the same direction.
Sidebar SVG icons make a brief movement on hover or keyboard focus, respecting
reduced-motion preferences without adding an animation package.

See [the Punjab College change record](docs/pu/changes.md) for workflows,
permission boundaries, Android requirements and portable preview setup. The
isolated preview starts with `npm run pu:init`, `npm run pu:db`,
`npm run pu:seed`, and `npm run dev:pu`.

</details>

<details>
<summary>Student enquiries and institute customisation from the main pages</summary>

Administrators open **Students & Guardians**, view a student, and choose
**Student history** beside **Profile** and **Fees**. Record behaviour and parent
meetings, search notes, filter dates and follow-ups, review academic results,
attendance, admission and correction history. Visibility rules still apply.

Main **Settings** includes floors/classes, college staff access, admission stages,
teaching/student rules and **Branding, loading and menus**. Choose the institute
PNG or standard loading animation and review the live preview. Existing roles
remain editable under **Roles & permissions**.

The Classes building view offers coloured floors, detached room callouts with
connector lines, multiple-class activity filters and room positions that extend
the floor on save. Sidebar icons animate their own parts on hover or keyboard
focus, with reduced motion respected.

See [the interface review](docs/pu/ui-review.md) for changes and validation.

</details>

<details>
<summary>Shared date navigation and fee action history</summary>

All date calendars use the shared Calendar navigation. Attendance uses the same
DatePicker field as staff attendance, fee reminders and other forms, keeping
class-day restrictions and future-date limits. Browsing months or years does
not change the selected day; selecting a day closes the picker.

Open a voucher's **Payment history and audit** to see who marked it paid,
recorded a payment, changed its status or reviewed a payment proof. Each event
keeps the acting account identifier, name and role at the time of the action.
Delegated staff actions show that staff member. Earlier events without a saved
recorder are not attributed to an administrator retrospectively.

The building's Campus activity panel has **Include fee activity**, off by default.
It is available to management with fee-view access and combines with class and
floor filters. Successful fee audit events go to the configured observability
provider under `operation: fees.audit`, including in production.

This adds the indexed `fee_audits` table. On an existing isolated pu preview, run
`npm run pu:db` before starting `npm run dev:pu`. For another local database,
apply `npm run db:push` and `npm run db:generate` against that local environment.

</details>

<details>
<summary>Student portal policy, activity history and request security</summary>

Schools now default to student records without login credentials. Guardians continue
working independently. Edit a class to allow its student accounts, then use Students
and guardians, Bulk actions, Create student accounts for existing records. Existing
accounts are skipped without resetting their password.

Admins can open Activity history for recorded actions from the last three calendar
months. Paid challans also have Payment history and audit. Financial events in the
building activity panel remain off until selected by someone with fee viewing access.

The platform owner's Access and request security page shows real request counts,
temporary IP controls and dormant school student logins. Authenticated attendance
bursts are observed without automatic volume blocks. Cloudflare is the trusted
client-IP source for the owner's confirmed private-origin deployment.

The existing worker runs college monitoring and notification outbox delivery.
Older audit records remain stored; the three-month history filter does not delete them.
Deployment preparation also preserves legacy tables and stops on data-loss warnings.
Lesson edits take effect tomorrow and preserve recorded
lecture history. See [the numbered production review](docs/pu/production-review.md)
for fixes, retained policy decisions, deployment details and validation.

</details>

<details>
<summary><b>Institute management and setup help</b></summary>

The owner can search and filter registrations, sort newest first, pin institutes across devices and review actual recorded member activity. Automatic jobs and owner management do not count as institute usage. Earlier untracked visits remain unknown.

New institutes receive migration contact links during initial setup, before fourteen days and through twenty student records. Classes opens with cards, with Building view beside Search. Shared actions expand their wording without making the toolbar wrap. The top-bar Help provides the current page's guides.

</details>

<details>
<summary><strong>Administrators and fee staff: scheduled monthly challans</strong></summary>

Open **Settings > Monthly fees**, or **All Fees > Monthly fees**, to choose the source session and campaigns, the first billing month, preparation time, review lead and payment due day. Selecting a source suggests its next month and the day from its latest saved deadline. Preparation starts off and requires an explicit save. The default review notice is three days before the month starts; administrators can choose five or another lead. Administrators, accountants and staff with active fee permissions receive an in-app review notice after the draft is saved.

Automatic guardian sending starts off. Enable it to suggest the third of the month, or choose day 1 through 28. In-app notices are the default. WhatsApp additionally needs a connected institute account, enabled fee announcements and recipient consent. Automatic sending must be on or before the payment due day. An outage that carries a draft past its deadline leaves it for staff review and manual sending. Manual publication stays available while automatic sending is off. Each guardian gets one summary covering their children's saved challans, with unpaid balances and family links checked again at delivery. The history shows pending, sent, skipped and failed notices and lets authorized staff retry failures.

Payment deadlines clamp to the last day of a short month, then move Saturday or Sunday forward to Monday, including across month boundaries. Information icons explain the rule and actual date. A first manually created session suggests the current institute month through the fifteenth and next month from the sixteenth. Dates remain editable.

Generation uses current active students in the source class and section coverage, current fixed fees, individual discounts and sibling discounts. Payments, old fines and admission charges are not copied. Current unassigned attendance fines follow normal billing rules. Drafts remain hidden from families. Editing an automatic draft preserves its session and scheduled send, and refuses to discard payment or proof history. Source or due-day setting changes apply to later drafts. Existing sessions with the target name are left unchanged for review; historical months are never announced automatically.

PostgreSQL retains each monthly run and each recipient's delivery progress. BullMQ checks every minute and recovers pending work after Redis or server interruptions. Successful channels are recorded independently, and stable in-app notification identifiers make retries safe. Structured server and Redis lifecycle events use the existing Datadog logging provider. The normal application worker starts this schedule; the isolated pu preview uses `npm run workers:pu` alongside `npm run dev:pu`, with its separate database and Redis connection.

English and Urdu guides are available in the Help Center under **Prepare monthly fees and schedule guardian notices**.

</details>

<details>
<summary><strong>Exam duties, private papers and scheduled results</strong></summary>

Exam duties start switched off for a new exam, so a regular datesheet does not require teacher assignments. Switch on **Assign exam duties** to customize it. Unconfirmed assignments expand automatically and Save explains which confirmation is needed. Validation messages remain readable in production; unexpected failures show a reference that support can find in the server logs.

Administrators and staff delegated exam creation or updating can assign a paper creator and a marker for each selected class, subject and section while making a datesheet. A shared paper across sections is the starting point; a class panel can split it into separate section papers. Each section can retain its own marker. The creator starts as the marker, and both remain editable.

Teacher suggestions use actual timetable assignments. A single teacher covering every selected section receives a green field outline. Ambiguous suggestions use a valid recorded creator from a past exam when available, otherwise a teacher suggestion with a yellow outline and a short reason. Every suggestion must be confirmed. Teacher options rank class-and-subject teaching first, subject teaching elsewhere second, and other eligible teachers last, with explanatory green, yellow and red dots. Historical marks without an author never establish a previous paper creator.

**Exam duties** gives controllers the preparation and marking status, private submission versions, reassignment requests and event history. Teachers use **My exam duties**. Creators can save written drafts or submit text and a private PDF, DOCX, text or image attachment of up to 2 MB. Controllers can return a submission, change either assignee, reopen section marks and record a request decision. Original submissions and actual actors remain in history. Only the assigned marker or a controller may save customized-exam marks. A recorded zero counts as entered, while a blank stays missing. Final section submission checks every eligible student in the active roster, excluding admissions after the exam.

Paper deadlines start off. Enabling them supplies an editable number of days before the paper, deadline time and reminder time. Selecting a result date suggests release at 00:00 on that date, marks due at 23:59 on the previous day, and a reminder at 00:00 two days before release. For 23 October release, these are 22 October at 23:59 and 21 October at 00:00. All values use the institute time zone and remain editable. Students and guardians cannot read scheduled results before release through dashboards, student grade reads or marksheets. Exams without a publication schedule retain their visibility.

A durable notification ledger combines actual subjects and sections for each recipient, rechecks pending work and current assignments, records errors and supports controller retries. A minute sweep queues independent exam reviews and deliveries through Redis and BullMQ with four workers; one large exam does not block the scheduler. Overdue responsibilities and unresolved requests are escalated to controllers. Private paper text and file contents are excluded from job payloads and operation logs.

</details>

<details>
<summary><strong>Staff engagement: timetable, punctuality and exam history</strong></summary>

**Staff engagement** is a report with **Timetable**, **Punctuality** and **Exam duties** tabs. Administrators and staff delegated staff viewing can select any staff member and a week or month, move between periods and export the lecture evidence. Other staff see **My work report**. The roster also links directly to each person's work report.

The report separates original assignments, completed lectures, partial lectures, confirmed missed lectures, cancellations, attendance-only entries and unrecorded outcomes. An ended lecture with no recorded outcome is unrecorded; it is never silently counted as an absence. Original and current teachers stay distinct, and intermediate handovers remain in the transfer history. The assigned teacher can pass an upcoming lecture to another active, available teacher with a reason; the server rechecks conflicts and permissions. Only staff with updating authority can correct lecture records.

Scheduled hours are current scheduled lecture minutes divided by 60, excluding cancelled and historical attendance-only entries. Verified teaching hours are recorded entry-to-departure minutes for completed or partial lectures, clipped to the scheduled interval and divided by 60. Missing timestamps do not become invented teaching time. These are reviewable records, not automatic payroll or a composite performance score. Past campus records and finalized timetable attendance sessions are included; an attendance session proves attendance was taken, not that a full lesson was taught. Forward timetable snapshots preserve future history, while earlier missing schedules are labelled unknown. The future snapshot horizon is 14 days.

Punctuality compares recorded lecture entry against the scheduled start and the administrator's grace period, initially 5 minutes. The staff WiFi daily attendance register is shown separately with its saved verification verdicts. System engagement counts actual saved actions in the chosen period by module, with the latest recorded sign-in shown as a separate fact. Reading a page is not counted as a saved action. Exam lead time is the elapsed time between final submission and result publication, divided by 24 hours; negative days indicate a late submission.

Staff report settings control the allowed arrival delay, teacher check-in and lecture handovers. Campus-specific restrictions continue to apply. A background sweep preserves lecture snapshots every 10 minutes, and reading a report also refreshes its evidence. The explicit demo institute includes clearly labelled example outcomes, transfers, papers and missing marks, with dates relative to today.

</details>

<details>
<summary><strong>Plan access, university fees and the first-month trial</strong></summary>

Monthly fee automation, exam customization and duties, staff engagement, and student history have four independent switches in the Super Admin plan catalogue and individual institute agreements. New catalogue defaults include them in Pro and Enterprise; Super Admin can enable or disable them on any plan or institute. Explicit saved choices are retained. Agreements saved before the three new automation and reporting switches existed receive their plan type’s defaults; older student-history access keeps the earlier campus entitlement until explicitly changed. Fee automation also needs fee access, and exam duties need exam access.

The full-feature trial includes all these switches even if the saved Starter agreement would lock them. The platform trial setting defaults to 30 days. The existing flow offers the trial at registration and lets the administrator start it after setup; branches inheriting the agreement share the parent's trial expiry. At expiry the saved agreement applies again, without deleting records. The trial setting remains editable by Super Admin.

Universities, including university branches, are excluded from the monthly fee scheduler, even during a trial. They keep manual term and subject billing with a chosen deadline; their manual first session does not force a monthly name, date or weekend adjustment. Other institute types retain the automated month choice: current month through the 15th, next month from the 16th. Their monthly due day is editable, clamps to a short month's last day, and moves Saturday or Sunday forward to Monday. The information icon explains the actual date. Guardian sending stays off initially and suggests the 3rd when enabled.

Feature changes must update this README in the same task, including actual behavior, permissions, settings, plan and trial defaults, and material verification limits. This requirement is also in `CLAUDE.md` and `.github/copilot-instructions.md`.

</details>

<details>
<summary><strong>Web and Android lecture notification controls</strong></summary>

Open **Settings > Lecture card** to enable the portal lecture bar for your own account, selected institute and device. It works on the web and inside the app. The Android notification card is a separate explicit choice in that section. Administrators can allow lecture cards, self check-in and handovers in **Settings > Advanced > Staff lecture controls**; campus restrictions also apply. These personal attendance controls are separate from the paid staff report and from daily WiFi attendance.

The first upcoming lecture offers **Check in** and **Pass lecture**. Expanded Android notifications place the action label above the class name, the elapsed timer in the center, checkout on the left and the next class check-in on the right when available. Check-in opens 15 minutes before the scheduled start and closes at its end. The timer uses the server's recorded entry time, so reopening the app does not restart it. The last lecture offers checkout without an unnecessary next-class action.

A normal Android check-in action runs in a background receiver without opening the main app. Passing a lecture opens **My lectures** directly at the available-teacher selector for the correct institute. Entering the next class closes the current session and enters the next in one database transaction. If either step fails, neither is saved. Repeated taps and response retries do not create another transition. Within the first 10 minutes of a session, checkout or a next-class transition requires confirmation showing the recorded duration. Android uses a small confirmation activity for that dialog instead of opening the main portal.

Android notification permission is requested on explicit enabling. Blocked notification channels have an Android settings shortcut. Precise-alarm access is optional and has a separate shortcut; the card falls back to inexact refreshes if it is unavailable or revoked. Android can delay background updates under alarm and battery restrictions. A server failure is shown with a retry path, rather than an optimistic attendance confirmation. The card refreshes on app resume, reboot and application update, and signing out clears it. Cached actions carry the account, institute and record version and are checked against the authenticated server session.

Android layout and permission behavior follow the platform guidance for [Android 12 notification restrictions](https://developer.android.com/about/versions/12/behavior-changes-12) and [exact alarms on Android 14](https://developer.android.com/about/versions/14/changes/schedule-exact-alarms). Android build 3 includes the native changes and must be rebuilt and installed with the real app configuration. The application Java sources and resources compile with Java 21 and Android SDK 36. Verification used a temporary test Firebase configuration, removed after the check; physical-device and real push-delivery testing remain outstanding. A web reload updates the portal controls.

</details>


<details>
<summary><strong>Release versions and support logs</strong></summary>

The version displayed in the application, its health response, browser monitoring, web logs, worker logs and traces uses the same full release, including the build number, such as `0.5.34.2`. Each completed update advances `package.json` through `npm run version:bump` once. Ordinary builds prepare `public/version.json` before compilation and do not advance the release again. A fresh checkout reproduces the same release. Fixed legacy environment version labels no longer override it.

In Datadog US5, use `service:innovorix* env:production status:error` to review application and gateway errors. For one release add `version:0.5.34.2`; for institute exam saves use `service:innovorix env:production @operation:exam.save`, and add `@reference:<displayed reference>` for an individual failure. Select a time range that includes the reported failure. Worker-only searches omit web and browser failures. Counts can contain multiple records of one failure. Browser collection can be blocked by browser or network policy, so exam failures also log on the server.

</details>


<details><summary><strong>Institute identification in diagnostics</strong></summary>

Structured server and browser diagnostics include `school.id`, `school.name` and `school.contact` from the saved institute. The contact is the institute’s saved number, not a message recipient’s number. Server metadata is cached briefly and remains separated between concurrent institutes. When identity cannot be resolved, the identifier and an availability flag remain; anonymous requests are not attributed to an invented institute. Credentials and message contents are excluded.

</details>


### Landing video and direct demo links

The saved YouTube walkthrough appears before the mobile application section. `/#demo` reaches its player and `/#watch-demo` reaches the whole section. Signed-in dashboard and college redirects preserve an explicit video visit. The signup reminder stays off that fragment. The public page receives only the video identifier, canonical link and title, never private platform settings.

SuperAdmin Portal includes the original landing-video controls for replacing or hiding the link and choosing its check interval. The dedicated `landing-video` worker runs a minute sweep, honors that saved interval and records availability checks in Datadog. Confirmed missing/private responses require two provider confirmations; timeouts, throttling and other inconclusive responses retain the previous availability. Confirmed incidents use the existing saved notification behavior, with durable leases and successful-delivery suppression. Deployment must include the player, owner controls, worker and queue wiring together. A healthy root response alone does not verify the video.
