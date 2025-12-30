 Civic Scope
AI-Powered Municipal Transparency Platform

> Role: Full-Stack AI Engineer  
> Status: Production-Ready / Live SaaS  

 Project Overview
Civic Scope is a production-ready, serverless SaaS platform designed to automate the ingestion, extraction, and summarization of local government meeting documents. By bridging the gap between dense municipal PDFs and citizen engagement, it provides an accessible, searchable, and unbiased window into local governance.

  Scope & Core Features
The platform manages the entire lifecycle of public record data:
- Automated Ingestion: Fetches PDFs from municipal sources, performing robust file-type validation and deduplication.
- Intelligent Extraction: Uses AI to parse unstructured meeting minutes into structured data (votes, agenda items, financial impacts).
- Neutrality Guardrails: Programmatically flags and rewrites opinionated language to ensure non-partisan reporting.
- Public & Admin Interfaces: Offers a citizen-facing dashboard for discovery and a secure Admin Console for data review.

  Technical Architecture & Sequence

 1. Ingestion Engine (The "Input")
The system begins with an autonomous ingestion pipeline capable of handling messy real-world data.
- Robust Parsing: Implemented PDF parsing with fallback OCR detection (Tesseract.js) for scanned documents.
- Data Integrity: Designed a dual-hashing system (binary vs. text) to allow re-processing of documents without breaking unique constraints.
- Normalization: Standardized municipality identities using FIPS/GNIS codes to prevent duplication.

 2. AI Processing Pipeline (The "Brain")
A cost-optimized, multi-stage AI pipeline processes the raw text.
- Model Fallback System: Engineered a smart router that defaults to `gpt-4-turbo` for complex tasks but falls back to `gpt-4o-mini` for simpler operations, reducing costs by ~60%.
- Semantic Caching: Implemented response caching based on text hashes, ensuring identical queries are never billed twice.
- Structured Outputs: Enforced strict schema validation using Zod to ensure AI outputs match the database model perfectly.

 3. Data Storage & Versioning (The "Memory")
- Database: Built on Google Firestore (NoSQL) for scalable, real-time data sync.
- Versioning: Created a custom "Data Model v2" that tracks document version history and supersedes-chains, allowing for corrections and updates without data loss.

 4. Application Layer (The "Interface")
- Frontend: Built with Next.js 14 (App Router) and TypeScript for server-side rendering and SEO.
- Security: Implemented enterprise-grade security including RBAC (Role-Based Access Control) with custom Firebase claims and edge-based rate limiting via Upstash.

  Technology Stack

| Domain | Technologies |
| Frontend | Next.js 14, React 18, TypeScript, Tailwind CSS, Shadcn/UI |
| Backend | Vercel Functions (Serverless), Node.js, Edge Middleware |
| Database | Google Firestore, Firebase Authentication, Firebase Admin SDK |
| AI & ML | OpenAI API (GPT-4/Turbo/Mini), Tesseract.js (OCR), Prompt Engineering |
| DevOps | GitHub Actions (CI/CD), Upstash (Redis), Cron Jobs |
| Testing | Playwright (E2E), Vitest (Unit), Zod |

  Key Metrics & Highlights
- Performance: Achieved <100ms response times for cached operations and <500ms for complex diff generation.
- Reliability: Built a resilient retry system with exponential backoff (1s, 2s, 4s) for AI tasks to handle API instability.
- Scale: Architecture supports 9 core collections and 12 secured API endpoints with automated audit trails for all admin actions.
- Throughput: Capable of handling high-volume ingestion with rate limiting capped at 10 requests/hour per IP (scalable via Redis).

---
This project demonstrates expertise in building complex, data-intensive full-stack applications with a focus on AI reliability, cost optimization, and system architecture.


 Mindfulness & Growth Platform 
Gamified Wellness & Meditation Application

> Role: Full-Stack React Engineer  
> Status: Production-Ready / Live SaaS  

  Project Overview
This project is a comprehensive Single Page Application (SPA) designed to make personal growth engaging through gamification. By combining traditional mindfulness tools (guided meditations, journaling) with a "virtual pet" evolution system, the platform drives consistent user retention and daily engagement habits.

  Scope & Core Features
- Gamified Progression: Users evolve a virtual pet through multiple visual stages by maintaining consistent meditation streaks.
- Content Delivery: secure streaming of premium guided audio sessions and mindfulness exercises.
- Subscription Management: Robust gating system for premium content using secure backend validation.
- Analytics & Tracking: Real-time visualization of user progress, activity history, and "mindfulness minutes."

  Technical Architecture & Sequence

 1. Application Layer (The "Interface")
Built as a responsive SPA to ensure a seamless, app-like experience across devices.
- State Management: Engineered a complex global state system using React Context API (`PetStateProvider`). This exposes intuitive APIs like `nextPetStage` to the UI, effectively separating the complex gamification logic from the presentation components.
- Component Architecture: Developed modular, reusable UI components styled with CSS Modules to prevent style leakage and ensure maintainability.

 2. Gamification Engine (The "Logic")
The core engagement loop is driven by a decoupled logic layer.
- Configurable Rules: Extracted hard-coded game rules into a separate configuration layer (`evolutionConfig.js`). This allows for tuning evolution thresholds and accessory unlocks without rewriting component code.
- Event-Driven Updates: User actions (completing a session) trigger state updates that programmatically check against these configurations to award achievements or evolve the avatar.

 3. Serverless Backend (The "Core")
Leveraged Firebase to minimize DevOps overhead while maximizing security and scale.
- Authentication & Security: Implemented Firebase Authentication for secure user profiles and strictly enforced Firestore Security Rules to protect sensitive user journals and progress data.
- Server-Side Logic: Utilized Cloud Functions to handle privileged operations—such as calculating premium subscription status—off-client, ensuring users cannot bypass paywalls.

 4. Quality Assurance (The "Guardrails")
Implemented a dual-layer testing strategy to ensure reliability during rapid development.
- End-to-End (E2E) Testing: Built a scalable Cypress test suite covering critical user journeys (Login → Meditate → Evolve). Utilized `data-cy` attributes to make tests resilient to UI/CSS changes.
- Unit Testing: Used Jest and React Testing Library to validate individual components and utility functions in isolation.

  Technology Stack

| Domain | Technologies |
| Frontend | React 18, Context API, CSS Modules, HTML5, JavaScript (ES6+) |
| Backend | Firebase Authentication, Cloud Functions, Node.js |
| Database | Google Cloud Firestore (NoSQL), Firebase Storage |
| Testing | Cypress (E2E), Jest (Unit), React Testing Library |
| DevOps | CI/CD Pipelines, Git, npm/yarn |

  Key Highlights
- Architecture: Successfully decoupled game logic from UI components, making the codebase cleaner and easier to extend.
- Reliability: Established a "Test-First" culture with a clear distinction between Unit tests for logic and Cypress tests for user flows.
- Engagement: Designed a "Pet Progression" system that serves as a sticky feature, measurably increasing user session frequency.
- Maintainability: Secure, serverless architecture reduces operational costs and maintenance time to near-zero.

---
This project demonstrates the ability to build engaging, interactive front-end experiences backed by secure, scalable serverless infrastructure.

 EthicaLog 
AI-Powered Philosophical Education Platform

> Role: AI Engineer & Full-Stack Developer  
> Status: Production-Ready  

  Project Overview
EthicaLog is an educational platform that bridges the gap between classical philosophy and modern ethical challenges for students. Unlike standard content sites, EthicaLog utilizes an autonomous Python-based AI pipeline to programmatically generate, validate, and publish age-appropriate ethical dilemmas, transforming complex philosophical concepts into relatable narratives.

  Scope & Core Features
- AI Content Generation: Autonomous pipeline generating 103+ unique ethical scenarios rooted in the teachings of philosophers like Aristotle and Confucius.
- Safety & Alignment: "Safety Tweaks" and "Alignment Evaluators" ensure all AI-generated content is safe for children (COPPA/GDPR-K compliant) and pedagogically sound.
- Interactive Learning: Rich, interactive content delivered via MDX, featuring dynamic filtering by theme, difficulty, and philosopher.
- Quality Assurance: Automated "Batch Health" monitoring to detect repetitive motifs or hallucinations in AI outputs before publication.

  Technical Architecture & Sequence

 1. AI Generation Pipeline (The "Engine")
Migrated a monolithic research script into a modular, production-ready Python application.
- Deterministic AI: Solved the "black box" problem of LLMs by implementing seeded RNG and deterministic IDs. This ensures that re-running the pipeline with the same parameters yields identical results, allowing for debugging and regression testing.
- Dynamic Prompting: Engineered a "Dynamic Instructions Builder" that constructs prompts on the fly, injecting specific "Guardrails" to prevent hallmark repetition and enforce specific educational learning objectives.

 2. Validation & Safety (The "Gatekeeper")
Content is strictly vetted before it ever reaches the frontend.
- Automated Grading: Implemented programmatic validators (e.g., `principle_echo.py`) to score generated content on its fidelity to the source philosophy.
- Compliance Checks: Built specific sub-routines to scan for and rewrite content that violates educational safety standards or neutrality requirements.

 3. Application Layer (The "Interface")
A high-performance web application designed for accessibility and engagement.
- Modern Stack: Built with Next.js 14 (App Router) and Headless UI for a fully accessible, keyboard-navigable experience.
- Content Engine: Designed a custom MDX processing layer with Zod schema validation, ensuring that all 100+ generated files maintain strict structural integrity and type safety.

 4. CI/CD & DevOps (The "Standard")
Established a "zero-breakage" deployment culture.
- Parallel Workflows: configured GitHub Actions to run 5 parallel checks on every push, including Unit Tests (Jest), End-to-End Tests (Playwright), and Linting.
- Accessibility Enforcement: Integrated Lighthouse CI to block any deployment that drops below a 90/100 accessibility score, ensuring WCAG 2.1 AA compliance.

  Technology Stack

| Domain | Technologies |
| AI & Pipeline | Python 3.8+, OpenAI API, LangChain (Concepts), Pydantic |
| Frontend | Next.js 14, React 18, TypeScript, Tailwind CSS, Headless UI |
| Content | MDX, Zod (Schema Validation) |
| Testing | Playwright (E2E), Jest (Unit), Pytest, Lighthouse |
| DevOps | GitHub Actions, Vercel, Docker |

  Key Highlights
- AI Determinism: Successfully engineered a way to make Generative AI outputs reproducible, a critical requirement for maintaining educational standards.
- Pipeline Architecture: Transformed a manual creative process into a scalable software pipeline, capable of generating hundreds of coherent, high-quality modules in minutes.
- Educational Rigor: Built a system that doesn't just "write text" but actively "teaches," verifying that specific philosophical principles are correctly instantiated in the narrative.
- DevOps Maturity: The project features a CI/CD suite comparable to enterprise SaaS products, ensuring high reliability and accessibility.

---
This project demonstrates deep expertise in AI Engineering—specifically in controlling and validating LLM outputs—alongside modern full-stack web development.

 InfluenceMD 
Data-Driven Physician Reputation Platform

> Role: Full-Stack Engineer  
> Status: Production-Ready  

  Project Overview
InfluenceMD is a reputation management analytics platform designed for healthcare professionals. It aggregates disparate federal healthcare data—including Medicare utilization and Open Payments—into a unified, proprietary "Influence Score." This score allows physicians to benchmark their professional footprint against peers and identify opportunities for career growth.

  Scope & Core Features
- Public Footprint Aggregation: Automatically compiles a physician's publicly available federal data into a single, easy-to-read dashboard.
- Identity Verification: Secure claiming of professional profiles using real-time validation against the NPI (National Provider Identifier) Registry.
- Dynamic Scoring: A weighted algorithm that normalizes clinical volume, research output, and industry payments into a quantifiable metric.
- Admin Intelligence: Comprehensive dashboard for administrators to analyze population health trends and provider distribution.

  Technical Architecture & Sequence

 1. Data Pipeline & ETL (The Foundation)
The system is built on a robust data engineering backbone capable of handling high-volume federal datasets.
- Automated ETL: Architected pipelines to ingest, clean, and normalize millions of records from complex CMS (Centers for Medicare & Medicaid Services) datasets.
- Data Warehousing: Utilized Supabase (PostgreSQL) to structure this data, enabling complex relational queries between physician profiles and their historical payment/claims data.

 2. Verification System (The Gatekeeper)
Ensures that only the actual physician can claim and manage their sensitive professional data.
- API Integration: Built a direct integration with the NPI Registry API to validate provider identities in real-time.
- Performance Optimization: Implemented a caching layer for verification requests, significantly reducing latency and external API dependency during high-traffic periods.

 3. Scoring Engine (The Logic)
The core value proposition of the platform.
- Weighted Algorithm: Developed a configurable scoring engine that processes disparate inputs (e.g., "Speaking Fees," "Patient Volume," "Publications") and normalizes them onto a standard scale.
- Real-time Recalculation: Scores update dynamically as new data is ingested or as users manually log new achievements (publications, awards).

 4. Application Layer (The Interface)
Leveraged the latest web standards for performance and SEO.
- Next.js 15: Built using the bleeding-edge App Router and Server Components to ensure optimal performance and search engine visibility for public physician profiles.
- Security: Enforced strict data access controls using Supabase Row Level Security (RLS), ensuring users can only edit their own claimed profiles.

  Technology Stack

| Domain | Technologies |
| Frontend | Next.js 15 (App Router), React, Tailwind CSS |
| Backend | Supabase, Node.js, Server Actions |
| Database | PostgreSQL, SQL, Redis (Caching) |
| Data & APIs | CMS Data (Open Payments/Medicare), NPI Registry API |
| Testing | Playwright (E2E), Jest (Unit) |

  Key Highlights
- Modern Architecture: Adopted Next.js 15 early to leverage Server Actions and advanced caching strategies for a highly responsive user experience.
- Data Engineering: Successfully solved the "dirty data" problem of public government datasets, creating a clean, normalized schema for application use.
- Scalability: The database architecture is designed to support millions of provider records without performance degradation.
- Security-First: Implemented bank-level identity verification (NPI) to prevent fraud and unauthorized profile claiming.

---
This project highlights expertise in Data Engineering (ETL) and building complex, data-intensive web applications using the latest React frameworks.


 SmileCharts
Hybrid Digital-Paper Behavior Management Platform

> Role: Full-Stack Engineer  
> Status: Production-Ready SaaS  

  Project Overview
SmileCharts is an EdTech platform designed to bridge the gap between traditional classroom management and modern data analytics. Recognizing that many educators prefer the speed of paper tracking but need the insights of digital tools, this "Hybrid Digital-Paper" system allows teachers to maintain their physical workflows while automatically digitizing data for long-term tracking, parent engagement, and AI-driven behavioral insights.

  Scope & Core Features
- Hybrid Workflow: A seamless interface that integrates physical paper charts with digital data entry, reducing friction for educators.
- AI Analytics Engine: Programmatically identifies behavioral patterns (e.g., "struggles after lunch") and suggests personalized interventions.
- Automated Engagement: System-driven parent updates via email (SendGrid integration) to keep families informed without adding to the teacher's workload.
- Compliance: Built from the ground up to adhere to strict FERPA, COPPA, and GDPR data privacy standards.

  Technical Architecture & Sequence

 1. Application Layer (The Interface)
Built on Next.js (App Router) for performance and SEO, the frontend is designed for high-frequency data entry.
- Modern Architecture: Migrated legacy codebases to a modular `src` directory structure, utilizing React server components and Tailwind CSS for a responsive, maintainable UI.
- Accessibility (A11y): Integrated automated accessibility checks within the CI/CD pipeline, ensuring the platform is usable by all educators and parents.

 2. Serverless Backend (The Engine)
Leveraged a full serverless stack to ensure scalability and minimize maintenance.
- Real-Time Data: Utilized Google Firestore for instant data syncing between the teacher's dashboard and the parent portal.
- Cloud Automation: Implemented Firebase Cloud Functions to handle complex backend logic, such as aggregating weekly behavioral reports and triggering email notifications via SendGrid.

 3. Testing & Reliability (The Infrastructure)
Architected a sophisticated testing environment to ensure stability without incurring cloud costs.
- Emulator Ecosystem: Developed custom scripts (`run-emulator-tests.js`) to spin up Firebase Emulators, create seed data, and run tests in a completely offline, isolated environment.
- End-to-End Testing: Built a comprehensive Cypress suite that verifies critical flows, including user authentication and email delivery verification using MailSlurp.

 4. Advanced Features (The Logic)
- Goal Tracking: Engineered a logic layer that tracks student progress against Individualized Education Program (IEP) goals, auto-generating historical visualizations and "at-risk" alerts.
- Data Security: Implemented robust Role-Based Access Control (RBAC) via secure session management to ensure teachers can only access data for their assigned students.

  Technology Stack

| Domain | Technologies |
| Frontend | Next.js (App Router), React, Tailwind CSS, TypeScript |
| Backend | Firebase (Firestore, Auth, Functions), Node.js |
| Testing | Cypress, Jest, Firebase Emulators, MailSlurp |
| DevOps | GitHub Actions, Vercel Deployment |
| Compliance | FERPA, COPPA, GDPR Standards |

  Key Highlights
- Hybrid UX: Successfully solved the "Digital Transformation" challenge by enhancing, rather than replacing, the preferred paper-based workflows of users.
- Test Engineering: The emulator-based testing setup demonstrates senior-level attention to Developer Experience (DX), reducing flakey tests and cloud costs.
- Privacy First: Engineering decisions were driven by compliance requirements, ensuring the safe handling of sensitive student data.
- Lifecycle Automation: Automated the entire feedback loop from data entry -> analysis -> parent notification.

---
This project demonstrates deep domain knowledge in EdTech compliance and the ability to build complex, hybrid user workflows supported by rigorous testing infrastructure.


 QuestionBud 
AI-Powered Knowledge Base SaaS for Creators

> Role: Python AI Engineer  
> Status: Production-Ready SaaS  

  Project Overview
QuestionBud is a multi-tenant SaaS platform designed to help content creators monetize their intellectual property. It allows creators to upload their digital content (PDFs, YouTube videos) to build a custom, AI-driven knowledge base. Fans can then subscribe to access this "digital brain," asking questions and receiving instant, context-aware answers derived directly from the creator's material.

  Scope & Core Features
- Multi-Format Ingestion: Asynchronously processes PDF documents and YouTube video transcripts into searchable data.
- RAG Engine: Uses Retrieval-Augmented Generation to provide accurate answers grounded in specific source material, preventing AI hallucinations.
- Creator Dashboard: Provides analytics on fan engagement, popular questions, and usage intent.
- Monetization: End-to-end subscription management allowing creators to gate access to their AI bots.

  Technical Architecture & Sequence

 1. Backend & API (The Core)
Designed a decoupled, high-performance architecture using Python.
- FastAPI: Leveraged FastAPI for the backend to take advantage of its native asynchronous support, essential for handling concurrent AI inference requests.
- Async Processing: implemented `async/await` patterns for heavy I/O operations (like fetching YouTube transcripts via `ingest_async.py`), ensuring the main server thread remains unblocked during content ingestion.

 2. RAG Pipeline (The Brain)
Engineered a sophisticated search pipeline to make unstructured data queryable.
- Vector Search: Utilized OpenAI Embeddings to convert text chunks into vector space, storing them in Supabase (pgvector).
- Context Injection: When a user asks a question, the system queries the database using cosine similarity to find relevant chunks, which are then fed into GPT-4 as context to generate a precise answer.

 3. Multi-Tenancy & Security (The Guardrails)
- Data Isolation: Architected the database schema to strictly enforce multi-tenancy, ensuring that a creator's knowledge base is accessible only to their authorized subscribers.
- Authentication: Secured all endpoints using JWT (JSON Web Tokens), protecting both creator dashboards and public-facing bot interfaces.

 4. SaaS Infrastructure (The Business)
- Stripe Integration: Built a self-serve business model by integrating Stripe payments.
- Webhook Automation: Implemented secure webhook handlers to automatically provision or revoke access based on subscription events (payment success, cancellation, failure).

  Technology Stack

| Domain | Technologies |
| Backend | Python 3.8+, FastAPI, Uvicorn, Pydantic |
| AI & ML | OpenAI API (GPT-4), pgvector, LangChain concepts |
| Database | PostgreSQL (Supabase), SQL |
| Frontend | Static HTML/CSS/JS (High Performance) |
| Infrastructure | Railway, Vercel, Docker |

  Key Highlights
- RAG Architecture: Demonstrates practical expertise in one of the most in-demand AI patterns (Retrieval-Augmented Generation).
- Async Optimization: Solved the bottleneck of long-running data processing tasks using modern Python async features.
- SaaS Mechanics: Proven ability to handle "real world" software requirements like multi-tenancy, payment processing, and secure user management.

---
This project highlights advanced backend engineering skills in Python, specifically focusing on Vector Search architectures and SaaS monetization strategies.


 Thinking Routine Recommender 
AI-Powered Pedagogical Strategy Engine

> Role: AI Engineer (Python)  
> Status: Live / Deployed  

  Project Overview
This tool is a specialized semantic search engine designed for educators. It helps teachers find the most effective "Thinking Routines" (active learning strategies) for their specific lesson plans. By replacing keyword matching with vector similarity, the application can "understand" the pedagogical goals of a lesson and recommend strategies that conceptually align, even if they don't share the same vocabulary.

  Scope & Core Features
- Semantic Recommendation: Matches user input (lesson plans) against a library of 77+ educational strategies based on meaning, not just keywords.
- RAG Architecture: Implements a Retrieval-Augmented Generation pattern to retrieve relevant data and feed it into an LLM for processing.
- Contextual Coaching: Instead of just listing strategies, the AI explains why a specific routine fits the submitted lesson and provides step-by-step instructions for implementation.
- Zero-Config Deployment: Built as a lightweight, serverless application for instant accessibility.

  Technical Architecture & Sequence

 1. The Knowledge Base (The Memory)
The system is grounded in a curated dataset of educational strategies (`AllThinkingRoutines.json`).
- Data Structure: Strategies are stored as structured JSON objects, ensuring the AI has access to the routine's name, purpose, and steps.
- Vector Database: (Conceptually) The system treats this JSON corpus as the retrieval target for the embedding engine.

 2. Semantic Search Pipeline (The Retrieval)
This is the core engineering achievement of the project.
- Vector Embeddings: Utilized OpenAI Embeddings API to convert the user's unstructured lesson plan into a high-dimensional vector.
- Cosine Similarity: The system calculates the distance between the user's "Lesson Vector" and the vectors of the 77+ routines, identifying the top 3 matches based on conceptual alignment (e.g., matching a lesson on "empathy" with a routine about "perspectives").

 3. Generative Explanation (The Augmentation)
Once the relevant routines are retrieved, the system uses GPT-4 to generate value.
- Prompt Engineering: Engineered a system prompt that takes the user's lesson and the retrieved routines as context. It instructs the model to act as a pedagogical coach, generating a tailored guide on how to apply that specific routine to that specific lesson.

 4. Application Layer (The Interface)
- Streamlit Framework: Built entirely in Python using Streamlit, enabling rapid development of a reactive, data-driven web interface without writing custom HTML/CSS.
- Secure Deployment: Deployed via Streamlit Cloud with rigorous secret management to protect API keys in a public repository environment.

  Technology Stack

| Domain | Technologies |
| Language | Python 3.9+ |
| Framework | Streamlit |
| AI & ML | OpenAI API (GPT-4), OpenAI Embeddings (text-embedding-3) |
| Architecture | RAG (Retrieval-Augmented Generation), Semantic Search |
| Data | JSON, Vector Similarity |

  Key Highlights
- Semantic vs. Keyword Search: Solved the vocabulary mismatch problem. A teacher looking for "deep thinking" will find routines about "reasoning" and "evidence," which a standard keyword search would miss.
- RAG Implementation: Successfully built a functioning RAG system from scratch, demonstrating the ability to connect LLMs to private/custom data sources.
- Prompt Engineering: The application output is deterministic and structured, preventing the LLM from hallucinating strategies that don't exist.

---
This project demonstrates the ability to build practical, value-driven AI tools using modern patterns like RAG and Vector Search without heavy infrastructure overhead.

