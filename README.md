<!-- TITLE & STATUS BADGES -->
# 🎯 **Bullseye**  
![Status](https://img.shields.io/badge/status-ARCHIVED-lightgray?style=for-the-badge) 
![Hackathon](https://img.shields.io/badge/built%20in-36h%20Hackathon-blueviolet?style=for-the-badge) 
![MIT License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)

> *“Fire practice questions that hit the mark—every time.”*

---

## 📚 Inspiration
High-school classes often come with **few practice tests** and *no* resources that match a tough teacher’s exact style.  
**Bullseye** sprang from the idea of letting students upload a teacher’s past papers (PDF) and instantly drill questions that mimic the same *structure* and *difficulty*, saving hours of blind searching.

---

## 🚀 What Bullseye Does
1. **Upload PDF** Students drag-and-drop previous tests or worksheets.  
2. **AI Question Generator** OpenAI LLM + parsed PDF content → brand-new questions that mirror the teacher’s wording & rigor.  
3. **Adaptive Practice UI** Answers are graded inline; mastery per topic is tracked in real time.  
4. **Personalised Feedback** Immediate hints & a mastery dashboard to focus the next study session.

---

## 🛠️ How We Built It

| Layer | Tech | Why we chose it |
|-------|------|-----------------|
| **Frontend** | React + Vite • Tailwind CSS | Fast dev setup & utility-first styling |
| **Backend** | Node.js • Express.js | Familiar JS stack for rapid API prototyping |
| **AI** | OpenAI LLMs | High-quality question generation & answer analysis |
| **PDF Parsing** | **Aryn** | Structured text extraction from academic PDFs |
| **Collaboration** | ChatGPT | Accelerated boilerplate & debugging during the 36 h sprint |

<details>
<summary>📐 High-Level Architecture</summary>

```mermaid
graph TD
  subgraph Client
    UI[React + Tailwind UI]
    Upload[PDF Upload]
    Practice[Practice Screen]
    Dashboard[Mastery Dashboard]
  end

  subgraph Server
    API[Express REST API]
    PDF(Aryn Parser)
    LLM[OpenAI LLM Service]
    DB[(Future DB)]
  end

  Upload -->|POST /pdf| API
  API --> PDF
  PDF -->|Parsed JSON| API
  Practice -->|GET /questions| API
  API --> LLM
  LLM -->|AI Items| Practice
  Practice -->|POST /answer| API
  API -->|score| Dashboard
