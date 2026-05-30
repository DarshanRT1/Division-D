# 👑 Multi-Agent Event Planning Orchestrator

An advanced multi-agent cooperative planner designed for high-impact corporate, academic, and cultural events. Built as a fully functional 12-hour hackathon submission using Python, Streamlit, and Groq's Llama 3 LLM.

---

## 🎯 System Architecture Diagram

Below is the conceptual flow of our multi-agent cooperative orchestration system:

```
                  +--------------------------------+
                  |    Page 1: Event Input Form    |
                  +--------------------------------+
                                  |
                                  v
                  +--------------------------------+
                  |  Page 2: Live Agent Dashboard  |
                  +--------------------------------+
                                  |
            +---------------------+---------------------+
            |                     |                     |
     (Parallel Run)         (Parallel Run)        (Parallel Run)
            |                     |                     |
            v                     v                     v
   +-----------------+   +-----------------+   +-----------------+
   |   Venue Agent   |   |  Speaker Agent  |   | Catering Agent  |
   | (Meetup Data    |   | (Panel Bios &   |   | (Culinary Board |
   | Recommendations)|   |  Topics Finder) |   |  & Cost Sheets) |
   +-----------------+   +-----------------+   +-----------------+
            |                     |                     |
            +---------------------+---------------------+
            |                     |                     |
            v                     v                     v
   +-----------------+   +-----------------+   +-----------------+
   | Logistics Agent |   |  Comms Agent    |   |                 |
   | (AV Technical & |   | (Attendee/VIP   |   |  (Task Engine)  |
   | Setup Checklists|   | Invite Mailers) |   |                 |
   +-----------------+   +-----------------+   +-----------------+
            |                     |                     |
            +---------------------+---------------------+
                                  |
                                  v
                  +--------------------------------+
                  |   Page 3: Lead Coordinator     |
                  | (Synthesizes Asana Templates)  |
                  +--------------------------------+
                                  |
                                  v
                  +--------------------------------+
                  |  Final Strategic Portfolio &   |
                  |  Professional Word Export      |
                  +--------------------------------+
```

---

## 🛠️ Key Agent Board & Scope

1. **🏢 Venue Scouting Agent**: Reads historical stats from the Meetup dataset, matches attendee limits, and recommends three highly viable, theme-specific property profiles.
2. **🎤 Speaker Board Agent**: Curates three highly relevant industry speakers, crafts unique panel topics, abstracts, and estimates professional honorariums.
3. **🍽️ Culinary Catering Agent**: Focuses strictly on guest count and dietary requirements (e.g. Vegetarian, Gluten-Free), designing distinct menu variations.
4. **📦 Logistics Operations Agent**: Forms detailed checklists for audio-visual channels, stage elevation, VIP airport transport, and event-day timelines.
5. **✉️ Comms Specialist Agent**: Drafts clear, engaging speaker outreach pitches, attendee invites, 48-hour reminders, and post-event appreciations.
6. **👑 Lead Event Coordinator**: Aggregates all reports, maps them against the Asana milestone task framework (`event_checklist.json`), and renders the unified strategy board.

---

## 📦 Local Datasets We Integrated

- **Kaggle Tech Meetup Dataset (`data/meetup_events.csv`)**: Contains over 150 realistic meetup records in 10 major hubs. Used by the Venue Scouting Agent to perform historical average attendance metrics and guide capacity sizing.
- **Asana Event Template (`templates/event_checklist.json`)**: Pre-populates five phase milestones (Initiation, Booking, Logistics, Comms, Execution) inside the Coordinator Synthesis engine.

---

## 🚀 Setup & Execution Instructions

Follow these quick steps to set up and run the application locally on Windows:

### 1. Prerequisite Installations
Ensure you have Python 3.10 or higher installed. Open your terminal/PowerShell and clone/navigate to the workspace folder:

```powershell
cd c:\Users\darsh\OneDrive\Desktop\genAI_hackthon\event_orchestrator
```

### 2. Install Package Dependencies
Install all required libraries using our standard requirements file:

```powershell
pip install -r requirements.txt
```

### 3. (Optional) Configure Environment Variables
Create a file named `.env` in the root of `event_orchestrator/` and add your Groq API Key:

```text
GROQ_API_KEY=your_groq_api_key_here
```

> 💡 **No API Key? No Problem!**
> The application contains a built-in, high-fidelity **Simulation Mode** that runs out-of-the-box. It performs local procedural intelligence to simulate agent thinking processes and generate highly realistic, theme-matched strategic plans. You can also directly type your API key in the sidebar of the Streamlit application interface!

### 4. Run the Streamlit Dashboard
Launch the main application interface:

```powershell
streamlit run app.py
```

Streamlit will compile and launch the dashboard inside your default web browser (typically at `http://localhost:8501`).
