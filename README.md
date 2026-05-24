# Shashank C M

I’m a software engineer focused on building reliability into systems that use LLMs. Instead of relying on fragile prompt engineering, I spend my time designing deterministic scaffolding, state-enforced runtimes, and predictable data pipelines.

---

### Architectural Focus:

* **Orchestration Runtimes:** Designing multi-agent loops with automated execution tracking, strict state verification hooks, and localized error handling to stop agents from spiraling.
* **Context & State Management:** Handling token boundaries, implementing dynamic window scaling, and mitigating context drift during long-running tasks.
* **Source Ingestion:** Building chunking strategies and structural extraction pipelines that preserve the narrative flow and hierarchy of massive technical documents.
* **Evaluation & Testing:** Building headless benchmarking harnesses and control-run frameworks to catch regressions in agent behavior before code hits production.

---

### Projects:

#### [claude-power-loom](https://github.com/shashankcm95/claude-power-loom)
A dual-layer multi-agent runtime environment built to keep complex execution cycles reliable and drift-free.
* **The Architecture:** Separated into a low-level **Substrate** layer and a high-level **HETS** (Hierarchical Engineering Team Simulation) layer. 
* **The Mechanics:** The Substrate layer manages environment reliability using a "hooks before, persistence around, verification after" model. The orchestration layer utilizes a 21-pattern library to coordinate specialized agent personas (such as Builders and Auditors) bound by formal execution contracts.

#### [TextBook_to_Tutorial_Converter](https://github.com/shashankcm95/TextBook_to_Tutorial_Converter)
A full-stack, automated parsing and compilation web application that restructures dense technical textbooks into modular, interactive documentation.
* **The Stack & AI Pipeline:** Built using Next.js 14 (App Router) and TypeScript. It utilizes a hybrid AI layout—orchestrating `gpt-4o` for streaming narrative synthesis and `gpt-4o-mini` for cost-effective structural parsing, interactive quiz generation, and fidelity scoring.
* **Data & Persistence Architecture:** Features an S3-compatible object storage integration paired with a custom SHA-256 caching layer to eliminate redundant PDF ingestion. State tracking is managed locally via SQLite and Drizzle ORM, wrapped in a lightweight, HMAC-SHA256 authenticated session infrastructure.

#### [Portfolio-Website-Builder](https://github.com/shashankcm95/Portfolio-Website-Builder)
A utility that maps structured data schemas against real-time version control states to automatically generate and compile synchronized developer profiles.

#### [AADI (Arrival-Aware Dine In)](https://github.com/shashankcm95/AADI)
A contextual service orchestration system designed to synchronize distributed event queues with real-time telemetry data.

---

### Connect:
* **Portfolio:** [shashank-cm.dev](https://shashank-cm.dev/)
* **LinkedIn:** [in/shashank-c-m](https://www.linkedin.com/in/shashank-c-m)
* **Email:** shashankcm95@gmail.com
