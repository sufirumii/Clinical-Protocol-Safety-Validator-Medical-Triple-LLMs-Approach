# Clinical Protocol Safety Validator (CPSV)

**Multi-agent AI system** that autonomously audits clinical trial protocols for:

- Safety gaps (patient protection risks)
- Regulatory compliance issues (FDA/EMA guidelines)
- Ethical concerns

Built with **three specialized 7B medical LLMs** working together, powered by **RAG** (ChromaDB + real-time PubMed integration).

## Overview

This project uses a coordinated multi-agent architecture to analyze uploaded clinical trial protocols before they proceed to human trials. It helps identify potential issues that could harm patients or violate regulations.

### Agents
- **Agent A** – Literature & Standard-of-Care Checker  
  Model: `epfl-llm/meditron-7b` (EPFL)  
  Focus: Alignment with current medical guidelines and PubMed literature

- **Agent B** – Inclusion/Exclusion & Safety Gap Detector  
  Model: `BioMistral/BioMistral-7B`  
  Focus: Missing protections, drug interactions, contraindicated conditions, vulnerable populations

- **Agent C** – Regulatory & Ethical Compliance Reviewer  
  Model: `dmis-lab/meerkat-7b-v1.0` (DMIS Lab)  
  Focus: Informed consent, adverse event reporting, IRB processes, GCP, privacy

### Core Technologies
- Retrieval-Augmented Generation (RAG) via ChromaDB
- Real-time PubMed API integration
- Parallel agent execution (ThreadPoolExecutor)
- Gradio web UI for easy protocol submission and report viewing

## Installation

```bash
# 1. Clone the repository
git clone https://github.com/sufirumii/Clinical-Protocol-Safety-Validator-Medical-LLMs-.git
cd Clinical-Protocol-Safety-Validator-Medical-LLMs-

# 2. Install dependencies (Python 3.10+ recommended)
pip install torch gradio transformers requests chromadb accelerate

# Optional: better memory management for 7B models
pip install bitsandbytes
Hardware note: Requires a GPU with ~16–24 GB VRAM for comfortable inference (or use 4/8-bit quantization via bitsandbytes).
Quick Start
Bash# Launch the Gradio interface
python main.py    # or whatever your entry script is named

Open the local URL shown in terminal (usually http://127.0.0.1:7860)
Click Initialize System → wait for models to load (first time takes longest)
Paste your clinical trial protocol text (include condition, treatment, study drug, inclusion/exclusion criteria, etc.)
Click Validate Protocol
Review: Executive Summary, Findings Table, Detailed Analysis

Important Advisory & Safety Notice
This is a research / educational prototype — NOT for clinical or production use.
All three base models (Meditron, BioMistral, Meerkat) carry explicit warnings against deployment in real medical settings without:

Extensive alignment & safety testing
Randomized controlled trials in real-world practice
Professional medical/regulatory oversight

Do NOT rely on CPSV outputs for:

Patient safety decisions
Trial protocol approval
Regulatory submissions
Any action that could impact human health

Always involve qualified clinicians, regulatory experts, and ethics committees.
Models & References

































AgentHugging Face IDBase ModelDeveloperKey Paper / CitationAepfl-llm/meditron-7bLlama-2EPFL LLM TeamarXiv:2311.16079BBioMistral/BioMistral-7BMistralBioMistral TeamarXiv:2402.10373Cdmis-lab/meerkat-7b-v1.0MistralDMIS Labnpj Digital Medicine (2025) – Small LMs from Textbooks
Citation
If this project is useful in your research, please cite:
bibtex@misc{cpsv2026,
  title = {Clinical Protocol Safety Validator: Multi-Agent LLM System for Clinical Trial Protocol Auditing},
  author = {Rumii},
  year = {2026},
  url = {https://github.com/sufirumii/Clinical-Protocol-Safety-Validator-Medical-LLMs-}
}

@misc{chen2023meditron,
  title={MEDITRON-70B: Scaling Medical Pretraining for Large Language Models},
  author={Zeming Chen and others},
  year={2023},
  eprint={2311.16079},
  archivePrefix={arXiv}
}

@misc{labrak2024biomistral,
  title={BioMistral: A Collection of Open-Source Pretrained Large Language Models for Medical Domains},
  author={Yanis Labrak and others},
  year={2024},
  eprint={2402.10373},
  archivePrefix={arXiv}
}

@article{kim2025small,
  title={Small language models learn enhanced reasoning skills from medical textbooks},
  author={Hyunjae Kim and others},
  journal={npj Digital Medicine},
  volume={8},
  number={1},
  pages={240},
  year={2025},
  publisher={Nature Publishing Group UK London}
}
License
Apache-2.0 – compatible with the base model licenses.
