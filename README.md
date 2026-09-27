 🔬 Researcher Outreach Pro

### *A smart system for discovering researchers, finding verified academic emails, and managing personalized research outreach.*

---
<img width="1024" height="1536" alt="ChatGPT Image Sep 27, 2026, 09_27_35 PM" src="https://github.com/user-attachments/assets/0a1e9e72-6daf-4a48-bc1c-619770e2a50d" />

## 📋 Overview

**Researcher Outreach Pro** is a self-contained web application built to help researchers, academic teams, and research-driven organizations **discover relevant researchers, find publicly available and verifiable email addresses, and manage personalized outreach campaigns** from a single workflow.

It is particularly suited to research-intensive fields such as **Bioinformatics, Genomics, Computational Biology, Stem Cell Research**, and related life-science disciplines.

Instead of relying on a single database or manually searching across dozens of websites, the system combines information from multiple scholarly sources and applies verification rules before a researcher or email is considered ready for outreach.

> **Find the right researchers → verify their contact information → personalize the outreach → track the response.**

---

## 🎯 The Problem

Academic outreach often involves several disconnected and time-consuming tasks:

* Finding researchers who actually work on a specific topic.
* Searching across multiple scientific databases and publication platforms.
* Locating the **researcher's own email address** rather than another author's.
* Verifying that an email genuinely belongs to the intended researcher.
* Personalizing messages without writing every email from scratch.
* Tracking replies, bounces, and records that require manual review.

**Researcher Outreach Pro brings these steps together into one research-focused workflow.**

---

# ⭐ Key Features

## 1. Researcher Discovery

The system discovers researchers using **user-defined scientific keywords** across multiple scholarly sources.

### Discovery Sources

* **PubMed / NCBI**
* **Europe PMC**
* **bioRxiv**
* **medRxiv**
* **arXiv**
* **OpenAlex**
* **ORCID**

The platform also supports **paper-based discovery**: relevant publications are searched first, and their authors are extracted as potential researchers.

This means discovery can be based not only on researcher profiles, but on the **research they actually publish**.

---

## 2. Multi-Source Email Discovery

Once researchers are discovered, the system searches multiple public sources for their email addresses.

### Supported Sources

* **PubMed XML**
* **Europe PMC**
* **CrossRef**
* **ORCID**
* **GitHub**
* **CORE**
* **Semantic Scholar**
* **bioRxiv / medRxiv**
* **arXiv**
* **Unpaywall**
* **Open-access PDFs**

The system follows an important rule:

> **Explicitly published evidence is preferred over inferred contact information.**

It does **not** simply construct an email from a researcher's name and university domain.

---

## 3. Researcher Identity & Email Verification

One of the main challenges in academic data collection is **correctly associating an email with the right researcher**.

For example, a publication may contain the email of the corresponding author while the system is currently processing another co-author. That address should not automatically be assigned to everyone on the paper.

The verification layer considers:

* **Name matching**
* **Source reliability**
* **Email ownership evidence**
* **Publication context**
* **Generic mailbox detection**
* **Shared mailbox detection**
* **Duplicate email detection**

Generic addresses such as:

```text
info@
contact@
editorial@
office@
support@
```

are rejected when they represent shared or organizational mailboxes rather than individual researchers.

When the system cannot establish sufficient evidence, the researcher is flagged for:

```text
needs_manual_check
```

This creates a deliberate separation between **high-confidence data and uncertain records**.

---

## 4. Co-Author Discovery

The system can turn relevant co-authors into new researcher records without incorrectly assigning their contact information.

When an email found in a publication belongs to a different author than the currently processed researcher, the system can:

1. Identify the author associated with the email.
2. Create or update that researcher as a separate record.
3. Verify that the publication is relevant to the selected keyword.
4. Preserve the correct researcher-to-email relationship.

This helps prevent one of the most damaging problems in publication-based email extraction:

> **One researcher's email being incorrectly assigned to multiple authors.**

---

## 5. Personalized Outreach

Researchers can be contacted through customizable message templates.

Supported variables include:

```text
{{name}}
{{university}}
{{topic}}
{{paper_title}}
```

The application provides a **Quill.js rich-text editor** and supports:

* Immediate sending
* Scheduled sending
* Delays between messages
* Personalized variables
* Attachments
* Campaign tracking

Up to **4 attachments** can be included in a message.

---

## 6. Outreach & Reply Tracking

The system keeps track of the outreach lifecycle for each researcher.

Typical statuses include:

```text
New
Contacted
Replied
Bounced
Needs Review
```

Incoming responses can be classified as:

* **Positive**
* **Negative**
* **Neutral**
* **Request for More Information**

This makes it easier to distinguish potential research opportunities from messages that simply require no further action.

---

## 7. IMAP Integration

Researcher Outreach Pro can connect to an **IMAP mailbox** to monitor incoming messages.

The system can periodically check for:

* **Replies**
* **Bounces**
* **Delivery failures**
* **Automatic replies**

The scanning interval is configurable and can run, for example, every **5 minutes**.

Incoming messages can then be analyzed and associated with the appropriate outreach record.

---

## 8. Dashboard & Analytics

The dashboard provides an overview of the complete outreach pipeline.

### Statistics

* Total researchers discovered
* Researchers with emails
* Email discovery rate
* Contacted researchers
* Replies
* Bounces
* Researcher sources
* Keyword distribution
* Manual-review records

### Filtering

Researchers can be filtered by:

* Keyword
* Country
* Source
* Email status
* Outreach status
* Reply classification
* Duplicate records

The system also supports:

* **CSV export**
* **CSV / Excel import**
* Duplicate management

---

## 9. Automation

Several parts of the workflow can run automatically.

### Automated Discovery

Run researcher discovery on a predefined schedule.

### Automated Email Discovery

Periodically search for missing email addresses across configured sources.

### Scheduled Outreach

Automatically send messages that have been scheduled for a specific date and time.

This allows the platform to function as a lightweight **research outreach pipeline** rather than requiring every step to be performed manually.

---

# 🔄 Workflow

```text
Configure keywords, sources & API keys
                    ↓
          Researcher Discovery
                    ↓
              Deduplication
                    ↓
             Email Discovery
                    ↓
            Email Verification
                    ↓
              Manual Review
                    ↓
         Personalized Outreach
                    ↓
             Send / Schedule
                    ↓
            IMAP Monitoring
                    ↓
       Reply & Bounce Analysis
                    ↓
           Campaign Tracking
```

The separation between **discovery, verification, review, and outreach** is intentional.

Questionable records do not have to move directly from discovery into the sending pipeline.

---

# 🔗 External Integrations

| Source                        | Purpose                                   | Requirement          |
| ----------------------------- | ----------------------------------------- | -------------------- |
| **PubMed / NCBI E-utilities** | Researcher & email discovery              | API key optional     |
| **Europe PMC**                | Publications, authors & emails            | Public API           |
| **CrossRef**                  | DOI & publication metadata                | Public API           |
| **ORCID**                     | Researcher profiles & public emails       | Public API / OAuth   |
| **bioRxiv / medRxiv / arXiv** | Preprints & contact information           | Public APIs/pages    |
| **GitHub**                    | Researcher/developer email discovery      | Token optional       |
| **CORE**                      | Open-access research metadata             | API key optional     |
| **OpenAlex**                  | Researcher discovery & scholarly metadata | API key optional     |
| **Semantic Scholar**          | Author & publication information          | API key optional     |
| **SMTP**                      | Email delivery                            | Required for sending |
| **IMAP**                      | Reply & bounce monitoring                 | Optional             |

---

# 🛠️ Tech Stack

### Backend

* **Node.js**
* **Express**
* **SQLite**
* **better-sqlite3**

### Frontend

* **Vanilla HTML**
* **CSS**
* **JavaScript**
* Single-page application architecture

### Supporting Libraries

* **Quill.js** — Rich-text email editing
* **Chart.js** — Dashboard visualizations
* **node-cron** — Scheduled jobs
* **Nodemailer** — SMTP email delivery
* **IMAP client** — Mailbox monitoring

### Setup

The application requires **no frontend build step**.

```bash
npm install
npm start
```

---

# 🧠 Data Quality Principles

The system is built around four core principles.

### 1. Verified Evidence Over Prediction

An explicitly published email address is preferred over an address that merely *looks correct*.

### 2. Identity Comes First

An email should belong to the researcher it is assigned to — not simply appear somewhere in the same publication.

### 3. Uncertainty Should Be Visible

When the available evidence is insufficient, the record is sent to **manual review** rather than silently accepted.

### 4. Duplicates Should Be Controlled

The system detects duplicate researchers and shared email addresses to reduce incorrect attribution.

> **Explicit verified evidence beats an unverifiable prediction.**

---

# 🔒 Privacy & Security

Researcher Outreach Pro is designed with responsible academic use in mind.

Key considerations include:

* **No tracking pixels** in outgoing emails.
* Emails are **not generated from names and domains**.
* Contact information is collected from **publicly available sources**.
* SMTP credentials and API keys are managed through the application's settings.
* Database operations use **prepared SQL statements** to reduce SQL injection risks.
* Uncertain records can be routed to **manual review** before outreach.

---

# ✅ Intended Use

Researcher Outreach Pro is intended for **responsible academic and research communication**, including:

* Research collaboration
* Research internship inquiries
* Volunteer research opportunities
* Computational collaboration
* Academic networking
* Conference or workshop invitations
* Sharing relevant research papers or tools

It is **not intended for spam, unsolicited commercial marketing, or activity that violates applicable anti-spam or email policies**.

Users are responsible for ensuring that their use of the platform complies with applicable policies and regulations.

---

# 🗺️ Roadmap

### Completed

* [x] Researcher discovery from PubMed
* [x] Europe PMC integration
* [x] arXiv integration
* [x] bioRxiv integration
* [x] medRxiv integration
* [x] ORCID integration
* [x] OpenAlex integration
* [x] Multi-source email discovery
* [x] Email verification and validation
* [x] Co-author discovery
* [x] Duplicate detection
* [x] Personalized email templates
* [x] Scheduled outreach
* [x] IMAP reply monitoring
* [x] Bounce analysis
* [x] Reply classification
* [x] Dashboard and analytics
* [x] CSV import/export

### Planned

* [ ] LinkedIn researcher profiles
* [ ] Multiple message templates
* [ ] A/B testing
* [ ] Follow-up reminders
* [ ] Advanced researcher identity resolution
* [ ] Improved relevance scoring
* [ ] Evidence-based email confidence scoring
* [ ] ORCID identity enrichment

---

# 💡 Project Philosophy

Researcher Outreach Pro was built around a simple idea:

> **Academic outreach should be targeted, evidence-based, and respectful of researchers' time.**

Rather than relying on a single database or blindly generating contact information, the system combines multiple scholarly sources, evaluates the available evidence, and separates **high-confidence records from those that require human verification**.

The result is a practical workflow for turning a research topic into a focused list of relevant researchers — and managing the outreach process from **discovery to response**.

---

# 👤 Author

Built as an independent tool to support **academic research, scientific collaboration, and researcher outreach**.

The application source code is private. This repository contains the project's documentation and technical overview.
