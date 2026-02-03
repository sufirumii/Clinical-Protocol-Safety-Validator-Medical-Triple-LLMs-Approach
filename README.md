Clinical Protocol Safety Validator (CPSV)
A multi-agent AI system for autonomous clinical trial protocol auditing using specialized medical language models, RAG, and real-time PubMed integration.
# Overview
The Clinical Protocol Safety Validator is an autonomous AI system that audits clinical trial protocols for safety gaps, regulatory compliance issues, and ethical concerns before trials begin. It uses three specialized medical language models working together through an orchestrated multi-agent architecture to identify potential risks that could harm patients or violate regulations.
# Features

Multi-agent architecture with three specialized medical AI models
Real-time PubMed integration for current medical literature
RAG-powered knowledge retrieval using ChromaDB
Parallel agent execution for efficient analysis
Comprehensive risk scoring and reporting
Web-based interface powered by Gradio

# System Architecture
# Three Specialized Medical AI Agents
# Agent A: Medical Literature Agent (Meditron 7B)
Meditron 7B from EPFL serves as the literature review specialist, trained specifically on PubMed abstracts and medical documentation. This agent searches current medical literature in real-time to verify that proposed treatments align with established standards of care.
Responsibilities:

Search PubMed for standard of care guidelines
Verify treatment alignment with current medical practice
Identify deviations from accepted protocols

# Agent B: Protocol Analyst (BioMistral 7B)
BioMistral 7B focuses on identifying safety gaps in patient selection criteria. This biomedical language model examines inclusion and exclusion criteria to find missing protections that could expose vulnerable populations to harm.
Responsibilities:

Analyze inclusion/exclusion criteria
Identify missing safety exclusions
Detect potential drug interactions
Flag contraindicated conditions

# Agent C: Ethical and Compliance Agent (Meerkat 7B)
Meerkat 7B from DMIS Lab ensures regulatory and ethical compliance by reviewing protocols against FDA and EMA guidelines.
Responsibilities:

Verify informed consent procedures
Check data safety monitoring requirements
Validate adverse event reporting mechanisms
Ensure IRB approval processes
Assess good clinical practice adherence

# Retrieval Augmented Generation (RAG)
The system uses ChromaDB as its vector database to implement a sophisticated RAG pipeline:

Protocol sections are parsed and embedded into the vector database
PubMed articles related to the study condition and drug are retrieved and indexed
Agents query the knowledge base for contextually relevant information during analysis

# PubMed Integration
Direct connection to NCBI E-utilities API for real-time literature searches:

Standard of care guidelines
Treatment recommendations
Drug interaction data
Safety information

# Installation
# Prerequisites

Python 3.10+
CUDA-compatible GPU (H100/H200 recommended, 40GB+ VRAM)
Ubuntu/Linux environment

# Setup
bash# Install dependencies
pip install torch transformers accelerate gradio chromadb sentence-transformers requests pandas numpy tqdm bitsandbytes sentencepiece protobuf

# Login to Hugging Face (for model access)
huggingface-cli login
# Single-line Installation (Jupyter)
python!pip install torch transformers accelerate gradio chromadb sentence-transformers requests pandas numpy tqdm bitsandbytes sentencepiece protobuf --quiet
# Usage
# Running the System
pythonpython clinical_protocol_validator.py
```

The system will launch a Gradio web interface on `http://localhost:7860` with a public shareable URL.

### # Web Interface Workflow

1. Click **"Initialize System"** to load all three AI models (5-10 minutes first time)
2. Enter your clinical trial protocol in the text area
3. Optional: Add a Protocol ID
4. Click **"Validate Protocol"** to run the audit (2-5 minutes)
5. Review results across three tabs:
   - Executive Summary
   - Findings Overview
   - Detailed Findings

### # Example Protocol Input
```
Condition: Type 2 Diabetes Mellitus

Study Drug: XYZ-123 (Novel SGLT2 Inhibitor)

Treatment: XYZ-123 10mg orally once daily for 24 weeks

Inclusion Criteria:
- Adults aged 18-75 years
- Diagnosed Type 2 Diabetes
- HbA1c 7.5-11.0%
- BMI 25-40 kg/m²

Exclusion Criteria:
- Type 1 Diabetes
- Severe renal impairment (eGFR <30 mL/min/1.73m²)
- History of diabetic ketoacidosis

Primary Endpoint: Change in HbA1c from baseline at week 24

Safety Monitoring: Monthly laboratory assessments
```

## # Output Format

### # Risk Scoring

- **0-30**: Low Risk (minor concerns, protocol generally sound)
- **31-60**: Moderate Risk (several issues requiring attention)
- **61-100**: High Risk (critical issues, major revision needed)

### # Finding Severity Levels

- **CRITICAL**: Immediate patient safety risk or major regulatory violation
- **HIGH**: Significant concern requiring protocol revision
- **MEDIUM**: Important issue that should be addressed
- **LOW**: Minor concern or suggestion for improvement

### # Sample Output
```
AUDIT SUMMARY
=============
Overall Risk Score: 42.3/100

Findings Breakdown:
- Critical Issues: 0
- High Priority: 2
- Medium Priority: 3
- Total Findings: 5

Risk Level: 🟡 MODERATE RISK

Top Concerns:

1. [HIGH] Missing critical exclusion criteria identified
   Source: Protocol Analyst Agent

2. [HIGH] Known drug interactions exist for XYZ-123
   Source: Protocol Analyst Agent

⚠️ RECOMMENDATION: Address identified concerns before trial initiation.
# Technical Details
# Models Used
AgentModelSizePurposeAgent Aepfl-llm/meditron-7b7BMedical literature analysisAgent BBioMistral/BioMistral-7B7BProtocol safety analysisAgent Cdmis-lab/meerkat-7b-v1.07BRegulatory compliance
Total GPU Memory Required: ~35GB (with FP16)
# Technology Stack

Language Models: Transformers (Hugging Face)
Vector Database: ChromaDB
Medical Literature: PubMed/NCBI E-utilities API
Web Interface: Gradio
Parallel Processing: ThreadPoolExecutor
Precision: FP16 for efficient inference

# Use Cases

Pre-submission Protocol Review: Identify issues before regulatory filing
Quality Assurance: Additional layer of safety review
Training and Education: Support protocol development teams
Competitive Analysis: Evaluate publicly available trial protocols

# Limitations

This is a research and educational tool, not a replacement for human experts
All findings should be validated by qualified professionals
AI models can occasionally generate incorrect information
Limited to English language protocols
Requires significant GPU resources

# Performance
# On H100/H200 GPUs

Model Loading: 5-8 minutes (first time), 2-3 minutes (cached)
Per-Protocol Analysis: 2-4 minutes
GPU Memory Peak: ~35GB
Throughput: 12-20 protocols per hour

# Contributing
Contributions are welcome! Please feel free to submit issues or pull requests.
# License
This project is provided for research and educational purposes. Consult with legal and regulatory experts before using in production clinical trial environments.
# Citation
bibtex@software{cpsv2026,
  title={Clinical Protocol Safety Validator: Multi-Agent AI for Trial Protocol Auditing},
  author={CPSV Development Team},
  year={2026},
  url={https://github.com/your-repo/clinical-protocol-validator}
}
# Acknowledgments

Meditron: EPFL LLM Team
BioMistral: BioMistral Development Team
Meerkat: DMIS Lab
PubMed: NCBI/NIH
ChromaDB: Chroma Team

# Disclaimer
This software is for research and educational purposes only. It is not intended to replace professional medical or regulatory advice. Always consult qualified experts for clinical trial protocol review and regulatory submissions.
# Contact
For issues, questions, or contributions, please open an issue on GitHub.
