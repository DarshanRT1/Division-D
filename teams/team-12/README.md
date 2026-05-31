# 👑 Multi-Agent Event Planning Orchestrator

## 📅 Hackathon Details
- **Hackathon Date**: 30th May 2026
- **Duration**: 12 hours (7:00 PM to 8:00 AM)
- **Mid-review session**: 12:00 AM to 1:00 AM
- **Final demo platform**: Microsoft Teams

## 👥 Team Details
- **Team ID**: D12

| Name | Roll Number | USN |
|------|-------------|-----|
| Eranna Patil | 450 | 01fe23bcs304 |
| Sohan Kallur | 461 | 01fe23bcs020 |
| Darshan R Talawar | 449 | 01fe23bcs303 |
| Sai Kiran Yelgurthi | 466 | 01fe22bcs312 |

## 🌐 Domain Information
- **Domain Number**: 12
- **Domain Name**: Agentic AI & Multi-Agent Systems
- **CO Mapping**: CO4 / CO5
- **Problem Statement**: Multi-Agent Event Planning Orchestrator

## 🎯 Problem Statement (Exact)
"Organising a large academic or corporate event involves coordinating venue, speakers, catering, logistics, and communications simultaneously. Build a multi-agent system where specialised agents handle each domain in parallel and a coordinator agent synthesises their outputs into a complete event plan with timeline, vendor brief, and communication templates."

## 🤖 System Architecture & 6 Agents Explained
The system employs a cooperative, data-grounded multi-agent network that runs parallel domain workers and maps outputs into structured corporate timelines:

```text
                      +--------------------------------+
                      |   Streamlit UI Event Inputs    |
                      +--------------------------------+
                                       |
                                       v (Parallel Execution Thread)
            +--------------------------+--------------------------+
            |                          |                          |
            v                          v                          v
   +-----------------+        +-----------------+        +-----------------+
   |   Venue Agent   |        |  Speaker Agent  |        | Catering Agent  |
   | (Queries Meetup |        | (Invited Bios & |        | (Culinary Board |
   | Events CSV Data)|        | Session Topics) |        | & Cost Sheets)  |
   +-----------------+        +-----------------+        +-----------------+
            |                          |                          |
            +--------------------------+--------------------------+
            v                          v                          
   +-----------------+        +-----------------+
   | Logistics Agent |        |  Comms Agent    |
   | (AV technical & |        | (Attendee & VIP |
   | Setup Schedule) |        | Invite Mailers) |
   +-----------------+        +-----------------+
            |                          |
            +--------------------------+
                                       |
                                       v
                      +--------------------------------+
                      |  Coordinator Synthesis Engine  |
                      | (Incorporates Asana Checklist) |
                      +--------------------------------+
                                       |
                                       v
                      +--------------------------------+
                      |  Interactive UI / Word Export  |
                      +--------------------------------+
```

- **Venue Agent**: Queries Meetup Events CSV Data to find and recommend venue locations that strictly accommodate expected guest counts based on historical data.
- **Speaker Agent**: Generates targeted speaker profiles, session abstracts, and calculates honorarium costs.
- **Catering Agent**: Constructs detailed culinary boards, menus, and cost sheets ensuring all dietary requirements are met.
- **Logistics Agent**: Drafts comprehensive AV technical setups and operational schedules.
- **Communications Agent**: Formats and prepares ready-to-use invite mailers, reminders, and thank you notes for attendees and VIPs.
- **Coordinator Agent (Orchestrator)**: Synthesizes the outputs of all specialized agents and incorporates the Asana checklist into a unified event strategy.

## 💻 Tech Stack & Justification
- **LangChain Agents / CrewAI**: Provides the underlying framework to route reasoning, manage state, and build parallel execution paths for all agents.
- **LLM API (FREE only)**: Utilizes Groq Python SDK for lightning-fast, free-tier processing using `llama3-8b-8192`. No paid OpenAI API is used.
- **Streamlit**: Selected for rapid creation of a fully interactive and responsive frontend user interface.
- **python-docx**: Allows programmatic generation of highly formatted MS Word documents (with tables, callouts, and colored borders) directly from agent outputs.
- **Python**: Core programming language, chosen for its powerful data processing and vast AI ecosystem.

## 📦 Datasets Sourced & Grounding
1. **Meetup Event Dataset**
   - **Source**: [kaggle.com/datasets/meetup-events](https://www.kaggle.com/datasets/meetup-events)
   - **Usage**: Used to ground the Venue Agent, allowing it to query real tech meetup events to compute historical average attendance sizes and pricing ranges.
2. **AgentBench Multi-Task Dataset**
   - **Source**: [github.com/THUDM/AgentBench](https://github.com/THUDM/AgentBench)
   - **Usage**: Provides schema guidance for evaluating multi-agent coordination, task tracking, and constraint validations.
3. **Corporate Event Planning Templates (Open Source)**
   - **Source**: [asana.com/resources/event-planning-template](https://asana.com/resources/event-planning-template)
   - **Usage**: Grounding data for the Coordinator Agent to pre-populate five phase milestones inside the synthesis engine.

*(Note: The Eventbrite Public Events API was listed as an option, but the above 3 datasets were selected for use in this project to satisfy the rule).*

## 🚀 Setup & Installation Instructions
Ensure you have Python 3.10+ installed.

1. **Navigate to the Project Directory**:
   ```bash
   cd teams/team-12
   ```

2. **Create a Virtual Environment (Optional but recommended)**:
   ```bash
   python -m venv venv
   # Windows: venv\Scripts\activate
   # Mac/Linux: source venv/bin/activate
   ```

3. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure API Key**:
   Create a `.env` file in the root of the project and add your Groq API Key:
   ```text
   GROQ_API_KEY=gsk_your_free_key_here
   ```

5. **Run the Application**:
   ```bash
   python -m streamlit run app.py
   ```

## 📁 Folder/Project Structure
```text
teams/team-12/
├── .env                    # Environment variables (API keys)
├── .gitignore              # Files ignored by git (e.g., venv, __pycache__)
├── app.py                  # Main Streamlit application and UI state management
├── requirements.txt        # All python dependencies required to run the project
├── README.md               # This documentation file
├── agents/                 # Directory containing all agent logic
│   ├── base_agent.py       # Base class handling Groq/Llama3 and simulation logic
│   ├── catering_agent.py   # Specialized logic for Catering Agent
│   ├── communications_agent.py # Specialized logic for Communications Agent
│   ├── coordinator_agent.py # Synthesizes outputs from all agents
│   ├── logistics_agent.py  # Specialized logic for Logistics Agent
│   ├── speaker_agent.py    # Specialized logic for Speaker Agent
│   └── venue_agent.py      # Specialized logic for Venue Agent
├── data/                   # Directory containing datasets
│   └── meetup_events.csv   # Synthesized Kaggle Meetup Event Dataset
├── templates/              # Directory containing logic templates
│   └── event_checklist.json # Asana Corporate Event Planning structure
└── tools/                  # Helper scripts and exporters
    └── docx_exporter.py    # Programmatically generates the final Word Document
```

## 🖥️ UI Walkthrough (Streamlit Pages)
* **Page 1: Event Input Form**
  * Collects event name, type, expected guest counts, location, date, theme, budget tiers, and dietary requirements via an interactive form.
* **Page 2: Agent Dashboard**
  * Displays live execution status. Shows each agent's active running status, progress loading bar, and individual Markdown log cards updating in real-time as tasks are processed in parallel.
* **Page 3: Final Event Plan + Download**
  * Presents the unified Strategy metrics cards, master timelines, vendor service briefs, and email copy. Includes a prominent download button to export the finished MS Word strategy.

## 📄 Word Document (.docx) Export Format
The exported document is generated with:
1. **Cover Page**: Title, subtitle, and structured metadata.
2. **Executive Summary**: Core strategy parameters.
3. **Master Timeline Table**: Formatted with distinct borders and shaded rows.
4. **Vendor Service Brief**: Consolidates venue, catering menus, and AV requirements.
5. **Speaker Profiles**: Bio summaries and estimated costs.
6. **Logistics Checklist**: Operational bullet points.
7. **Communication Pack**: Formatted email drafts for all attendees.

## ✅ Hackathon Rules Compliance Checklist
- [x] **Rule 1**: All code must be written during the hackathon window. (Completed during event)
- [x] **Rule 2**: Pre-built templates and open-source libraries are permitted with proper attribution. (Used Langchain, Streamlit, datasets cited above)
- [x] **Rule 3**: No paid OpenAI APIs should be used. (Strictly used Groq Llama3 free-tier API)
- [x] **Rule 4**: Teams must use at least one listed public dataset. (Used Meetup, AgentBench, and Asana templates)
- [x] **Rule 5**: Teams must build solutions only within their selected domain. (Domain 12 built)
- [x] **Rule 6**: Plagiarism, copying another team's work, or misrepresenting AI-generated content. (All architecture and code is original for this submission)
- [x] **Rule 7**: One review session will be conducted for all teams between 12:00 AM and 1:00 AM. (Understood)
- [x] **Rule 8**: All team members must be present during the final judging demo through online Microsoft Teams. (Acknowledged)
- [x] **Rule 9**: Teams must be ready with proper explanation, architecture flow, and working demonstration. (Ready for demo!)

## 👨‍💻 Team Contribution Breakdown
* **Eranna Patil**: Implemented core multi-agent execution pipeline in `base_agent.py` and `coordinator_agent.py`.
* **Sohan Kallur**: Designed and built the Streamlit interactive UI (`app.py`), encompassing all 3 dashboard pages.
* **Darshan R Talawar**: Handled prompt engineering for all specialized domain agents (Venue, Speaker, Catering, Logistics, Comms) and dataset grounding.
* **Sai Kiran Yelgurthi**: Developed the `docx_exporter.py` for professional Microsoft Word formatting and timeline tables.

## 📜 requirements.txt Dependencies
```text
streamlit==1.35.0
langchain-core==0.2.3
groq==0.8.0
python-docx==1.1.2
pandas==2.2.2
python-dotenv==1.0.1
```
