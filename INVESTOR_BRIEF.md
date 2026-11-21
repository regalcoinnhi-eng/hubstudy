# HubStudy — Investor Brief

*v2 · 21 Nov 2026 · Founder: Cao Duc Chung (Vietnam) · hello@aicollabx.org · [study.aicollabx.org](https://study.aicollabx.org)*

> **Stage, stated plainly:** an internal pilot with **one student (n=1) for about 3 weeks**. Pre-revenue, bootstrapped, no legal entity yet. This brief describes what works today, what we haven't proven yet, and how we plan to prove it.

## 1. One line

A voice-first AI study companion that helps Vietnamese students (ages 11–15) do **their own homework**, following their **real school timetable and textbooks**, with parents kept in the loop on Zalo.

## 2. The problem

- Vietnam has **more than 23 million general-education students** in 2025–2026 (news report, [SGGP](https://en.sggp.org.vn/nationwide-unity-marks-start-of-unprecedented-school-year-post120080.html)). After school, many study alone in the evening while parents work.
- Generic chatbots don't know what the teacher taught today and tend to **hand out answers**. They are text-heavy for an 11-year-old and give parents no visibility.
- Human tutors work well but cost a lot and can't be there every evening.

*Hypothesis to validate in beta:* parents will pay for an evening helper that keeps the child on the school's actual lessons **without** doing the homework for them.

## 3. Product status (what is live vs. prototype)

| Module | What it does | Status (21 Nov 2026) |
|---|---|---|
| Notebook intake | Photo of the notebook page or teacher message → AI drafts "taught / assigned" → family confirms | **Running in internal pilot** |
| Timetable sync | Plan follows the class timetable and actual lessons | **Running in internal pilot** |
| Three characters | Buddy (chat, curiosity), Teacher (homework by timetable), Mom (talks with the child, extra subjects) | **Running in internal pilot** (web) |
| Socratic coach | Opens only when the child asks; gives one small hint per turn | **Running in internal pilot** |
| Quiz / test prep | Generates and grades practice questions; deterministic fallback when AI is down | **Running in internal pilot** |
| Web voice tutor | Real-time voice (Gemini Live) | **Running in internal pilot** |
| Local Vietnamese STT | sherpa-onnx on the home server; audio stays local | **Running.** Internal benchmark: one 114 s clip of the child's speech in 2.2 s on the home Mac (single sample, see `docs/LOCAL_STT.md` in the private repo) |
| iPad / iPhone | Web app used on iPad | **Internal use only** |
| ESP32 voice device | Screen-free speaker with study reminders | **Prototype**, not beta-ready |
| Zalo parent bridge | Assignments in, progress out | **Partially wired.** Allowlist design done; delivery to parents not yet live |

Multi-model by design: Gemini (voice, vision), Claude, GPT. Source code is private and a demo is available on request.

## 4. Differentiation (claims we still need to test)

1. **Grounded in today's class:** the source of truth is the notebook and the timetable, not a generic syllabus.
2. **Pedagogy-first:** one hint at a time; assigned work is kept separate from AI-suggested practice.
3. **Voice and screen-free hardware** for kids who can't type fast.
4. **Vietnam-native:** Vietnamese local STT, Zalo, MOET textbooks.

## 5. Competition

| Alternative | Type | How we differ (hypothesis) |
|---|---|---|
| Human tutors / "học thêm" | Direct substitute | Cheaper, every evening, but less personal. Must prove it's trustworthy |
| VioEdu, HOCMAI | VN K-12 content & practice | They provide content. We follow *today's* class and coach by voice |
| Azota | Assignment & grading for teachers | Teacher-side. We are the child and parent side at home |
| Khanmigo (Khan Academy) | AI tutor, English-first | Vietnamese curriculum, Vietnamese voice, Zalo |
| Gemini / ChatGPT for learning | General assistants | They aren't tied to the class schedule and give answers too easily |

## 6. Business model (hypotheses, not validated)

| Stream | Hypothesis | To validate |
|---|---|---|
| Family subscription | 99k–199k VND/month | Willingness-to-pay in beta |
| ESP32 device | One-time sale or bundled | BOM, fulfillment and support cost |
| Schools / centers | Per-seat license | Later |

We do not have unit economics yet. Before a paid pilot we will measure **AI and voice cost per family per month**, device cost, and gross margin.

## 7. Market

Vietnam edtech estimates for 2025 range from **USD 1.1B (IMARC)** to **USD 3.7B (GlobalData)** because the two use different definitions. GlobalData puts K-12 at 81.6% of its total ([IMARC](https://www.imarcgroup.com/vietnam-edtech-market), [GlobalData](https://www.globaldata.com/store/report/vietnam-edtech-market-analysis/)). The bottom-up SAM/SOM will come from beta conversion data. Timing: a unified textbook set from 2026–2027 ([SGGP](https://en.sggp.org.vn/vietnam-races-to-prepare-unified-textbook-set-for-20262027-school-year-post124897.html)) makes deep textbook grounding cheaper.

## 8. Next 6 months — KPIs decided in advance

| Phase | Milestone | Success threshold |
|---|---|---|
| M1–2 | Self-serve onboarding; consent and data-policy flow | A family onboards without the founder |
| M3–4 | **10-family closed beta** | ≥3 study sessions per child per week; ≥60% of families active in week 4; ≥70% of assignments completed |
| M5–6 | Paid pilot | ≥30% of beta parents willing to pay; cost-to-serve per family measured |

## 9. Child safety & data — done vs. planned

| Done | Planned before beta |
|---|---|
| Local speech-to-text (voice stays at home) | Parent consent and withdrawal flow |
| Allowlisted Zalo threads only | Data inventory, retention and deletion policy |
| Parent confirms every AI-extracted item | Encryption at rest, access log |
| No raw phone numbers in the data contract | Vendor terms review (AI providers, Zalo); incident response |

## 10. Team

Solo founder, Cao Duc Chung, building with AI coding agents coordinated by [HubWork](https://github.com/tarochi0001-stack/hubwork). *(Founder background: to be added.)* First hire or advisor: curriculum and pedagogy lead.

## 11. Ask (per program)

- **ElevenLabs:** voice credits for 3 Vietnamese character voices plus spoken reminders for a 10-family beta.
- **AWS Activate:** credits to host the Study Hub API and voice pipeline for the 6-month beta, and Bedrock (Claude) for tutoring.
- **SIHUB / accelerators:** mentoring on child-data compliance, school partnerships and go-to-market.
