# AI Health Care Triage Agent
Gemini-powered Rural Health AI agent for community health workers 
AI Health Care Triage Agent
Rural Health AI Agent for community health workers, built with Gemini, Google ADK, MCP tools, and Streamlit.
AI Health Care Triage Agent helps community health workers collect symptom information in local-language text or voice transcription, ask clarifying questions, flag red flags, review optional photos such as rashes, wounds, medicine strips, or prescriptions, and draft a PHC referral note.
Problem
Community health workers often collect first-line health information in rural communities, but escalation decisions can be difficult when symptoms are incomplete, written in local language, or include visual clues such as skin rashes, wounds, or medicine strips. Delayed escalation can increase risk for pregnant women, children, fever cases, dehydration, respiratory distress, wounds, and other urgent presentations.

Solution
This project provides a working AI agent workflow:
Intake Agent normalizes patient details, local-language symptom text, vitals, and optional image metadata.
Gemini Triage Agent screens the case for danger signs using Gemini text and image capability when an API key is available.
PHC Escalation Agent uses MCP tools to find the nearest PHC, draft a referral note, and save the case log.
Streamlit Web UI gives community health workers a simple demo interface for intake, triage output, red flags, clarifying questions, and referral note download.
The app also includes a deterministic local fallback, so the demo remains usable even without network access or an API key.

Google Stack Mapping

Requirement	Implementation
Theme	Rural Health
Working AI Agent	Streamlit app backed by an intake -> triage -> escalation agent pipeline
Gemini	health_triage/gemini_client.py calls Gemini for multilingual and multimodal triage
AI Studio	Uses a Gemini API key from Google AI Studio via GOOGLE_API_KEY
ADK	health_triage/adk_agents.py builds a Google ADK SequentialAgent graph
MCP	mcp_server.py exposes PHC lookup, referral drafting, and case logging tools
Google AI Stack	Gemini API, Google ADK, MCP tools, Streamlit web app
Multimodal	Optional image upload is passed to Gemini when enabled

Disclaimer

This application does not provide medical diagnosis. It supports documentation, danger-sign screening, and referral preparation. Final clinical decisions must be made by qualified healthcare staff.
