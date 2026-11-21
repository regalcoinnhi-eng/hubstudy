# HubStudy — Investor Brief

*November 2026 · Founder: Cao Duc Chung (Vietnam) · hello@aicollabx.org · [study.aicollabx.org](https://study.aicollabx.org)*

## 1. One line

A voice-first AI study companion that helps Vietnamese students (ages 11–15) do **their own homework**, following their **real school timetable and textbooks**, with parents kept in the loop on Zalo.

## 2. The problem

- Vietnam has **more than 23 million general-education students** in 2025–2026 ([SGGP](https://en.sggp.org.vn/nationwide-unity-marks-start-of-unprecedented-school-year-post120080.html)), and families spend heavily on after-school tutoring ("học thêm").
- After school, most kids study alone between 19:00 and 21:00 while parents work. Generic chatbots:
  - ignore what the teacher actually taught today and drift off the textbook;
  - **give away answers**, so the child stops thinking;
  - are text-heavy, while 11-year-olds want to talk;
  - leave parents with no picture of what was done.
- Human tutors are expensive (often millions of VND per month per subject) and not available every evening.

## 3. The product (working today)

| Module | What it does | Status |
|---|---|---|
| **Notebook intake** | Child snaps a photo of the day's notebook page or the teacher's message; AI extracts "what was taught" and "what was assigned" as a draft the family confirms | ✅ running |
| **Timetable sync** | Study plan follows the class timetable (TKB) and actual lessons, not a fixed 18-week book schedule | ✅ running |
| **Three AI characters** | **Buddy** (chat when tired, curiosity questions on nature & society), **Teacher** (homework by timetable), **Mom** (listens, helps with extra subjects) | ✅ running |
| **Socratic coach** | Opens only when the child asks for help, and gives **one small hint per turn**, never the full answer | ✅ running |
| **Quiz & test prep** | Generates and grades practice questions per lesson; falls back to deterministic grading if AI is down | ✅ running |
| **Voice** | Real-time voice tutor (Gemini Live); **on-device Vietnamese speech-to-text** (sherpa-onnx, 114 s of the child's speech transcribed in 2.2 s, audio never leaves the home) | ✅ running |
| **ESP32 voice device** | A small screen-free speaker the child can talk to; speaks study-time reminders | ✅ prototype |
| **Parent bridge** | Assignments in and progress reports out via Zalo | ✅ running |
| **AI-outage resilience** | Queue with backoff and circuit breaker; core study flow keeps working when an AI provider fails | ✅ running |

**Engineering:** ~34k lines (Python, JavaScript, ESP32 firmware). Multi-model: Gemini (voice, vision), Claude, GPT. Built by one founder working with AI coding agents, coordinated through our second product, [HubWork](https://github.com/tarochi0001-stack/hubwork).

## 4. Why it works / what's different

1. **Grounded in the real class**, not generic: the source of truth is today's notebook and the school timetable.
2. **Pedagogy-first:** one hint at a time, and assigned work is kept separate from AI-suggested extra practice. Parents trust it because it doesn't do the homework for the child.
3. **Voice + hardware:** works for kids who can't type fast, and works without a screen (less screen time is a selling point to parents).
4. **Vietnam-native:** Vietnamese STT running locally, Zalo as the parent channel, MOET textbooks.
5. **Low cost to run:** local STT plus a fallback design keep per-child AI cost low.

## 5. Traction (honest)

- In **daily use for ~3 weeks** with a 6th-grade student at home (pilot started November 2026).
- Covers grade-6 math reading plans and the full intake → plan → coach → quiz → parent report loop.
- No revenue yet. No outside funding (bootstrapped).

## 6. Business model (planned)

| Stream | Price hypothesis | Notes |
|---|---|---|
| Family subscription | 99k–199k VND/month | Well below a single human tutor |
| ESP32 voice device | One-time hardware sale or bundled | Differentiator; low BOM |
| Schools / tutoring centers | Per-seat license + teacher dashboard | Later phase |

## 7. Market & timing

- Vietnam edtech is estimated at **~USD 1.1B (IMARC) to USD 3.7B (GlobalData) in 2025**, with K-12 the largest segment (GlobalData: 81.6%) ([IMARC](https://www.imarcgroup.com/vietnam-edtech-market), [GlobalData](https://www.globaldata.com/store/report/vietnam-edtech-market-analysis/)).
- **Timing:** Vietnam is moving to a unified textbook set for 2026–2027 ([SGGP](https://en.sggp.org.vn/vietnam-races-to-prepare-unified-textbook-set-for-20262027-school-year-post124897.html)). One curriculum makes deep textbook grounding cheaper to build nationwide.

## 8. Roadmap & use of funds / credits

| Next 6 months | Milestone |
|---|---|
| Month 1–2 | Grade 6–7 core subjects; onboarding without the founder's help |
| Month 3–4 | **10-family closed beta** (HCMC/Hanoi); measure weekly active study sessions and parent retention |
| Month 5–6 | Paid pilot, ESP32 v2, teacher view |

Credits and grants go to: AI inference (voice and vision), cloud hosting, voice synthesis for the three characters, and ESP32 device batches for beta families.

## 9. Risks & mitigation

| Risk | Mitigation |
|---|---|
| Child data and privacy | Local STT, allowlisted Zalo threads, no raw phone numbers stored, parent confirms every extracted item |
| AI cost and outages | Multi-provider design, deterministic fallbacks, local speech |
| Curriculum changes | Intake reads the actual notebook, so it adapts to any textbook |
| Solo founder | HubWork lets one founder run many AI agents. Hiring a curriculum lead is the first hire |

## 10. Ask

Cloud and AI credits, plus accelerator support, to run the 10-family beta. Open to pre-seed conversations.
