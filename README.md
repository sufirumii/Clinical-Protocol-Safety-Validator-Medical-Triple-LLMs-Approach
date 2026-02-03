# Clinical Protocol Safety Validator (CPSV)

**An autonomous multi-agent AI system** designed to audit clinical trial protocols for safety risks, regulatory non-compliance, and ethical issues **before human trials begin**.

Built with three domain-specialized 7B medical LLMs in a collaborative architecture, Retrieval-Augmented Generation (RAG), ChromaDB vector storage, and live PubMed evidence retrieval.

##  Core Capabilities

- Detects missing safety protections in inclusion/exclusion criteria  
- Verifies alignment with current standard-of-care & medical literature  
- Checks FDA/EMA regulatory requirements & ethical standards  
- Produces structured findings with severity, evidence, and recommendations  
- Runs agents in parallel for faster analysis  
- User-friendly Gradio interface for protocol upload & report generation

## Agents

| Agent | Role                              | Model ID                          | Developer      | Focus Area                              |
|-------|-----------------------------------|-----------------------------------|----------------|-----------------------------------------|
| A     | Literature & Standard-of-Care     | `epfl-llm/meditron-7b`           | EPFL           | PubMed + clinical guidelines alignment  |
| B     | Inclusion/Exclusion Safety Gaps   | `BioMistral/BioMistral-7B`       | BioMistral     | Drug interactions, contraindications    |
| C     | Regulatory & Ethical Compliance   | `dmis-lab/meerkat-7b-v1.0`       | DMIS Lab       | Informed consent, GCP, IRB, privacy     |

##  Quick Start

```bash
# Clone
git clone https://github.com/sufirumii/Clinical-Protocol-Safety-Validator-Medical-LLMs-.git
cd Clinical-Protocol-Safety-Validator-Medical-LLMs-

# Install
pip install -r requirements.txt
# or directly:
# pip install torch gradio transformers requests chromadb accelerate bitsandbytes

# Launch
python main.py

Open the Gradio link (usually http://127.0.0.1:7860)
Click Initialize System (first load takes time – models are ~7B each)
Paste protocol text (include condition, treatment, drug, criteria, etc.)
Click Validate Protocol
Read summary + detailed findings

Recommended hardware: GPU with ≥16 GB VRAM (quantization helps on 12–16 GB cards)
 Critical Safety & Usage Disclaimer
This is strictly a research and educational prototype — NOT a medical device or regulatory tool.
The underlying models carry explicit warnings against clinical deployment:

No real-world clinical validation or randomized trials have been performed
Outputs may contain hallucinations, biases, or incomplete reasoning
Never use results for: patient safety decisions, trial approval, IRB submission, or any action affecting human health

Always require review by qualified physicians, regulatory affairs professionals, and ethics committees.
Use at your own risk. For research purposes only.
References & Citations
Please cite if this work is useful:
bibtex@misc{cpsv2026,
  title = {Clinical Protocol Safety Validator – Multi-Agent Auditing of Clinical Trial Protocols},
  author = {Rumii},
  year = {2026},
  url = {https://github.com/sufirumii/Clinical-Protocol-Safety-Validator-Medical-LLMs-}
}

@misc{chen2023meditron,
  title={MEDITRON-70B: Scaling Medical Pretraining for Large Language Models},
  author={Zeming Chen and others},
  year={2023}, eprint={2311.16079}
}

@misc{labrak2024biomistral,
  title={BioMistral: A Collection of Open-Source Pretrained Large Language Models for Medical Domains},
  author={Yanis Labrak and others},
  year={2024}, eprint={2402.10373}
}

@article{kim2025small,
  title={Small language models learn enhanced reasoning skills from medical textbooks},
  author={Hyunjae Kim and others},
  journal={npj Digital Medicine},
  volume={8}, number={1}, pages={240},
  year={2025}
}
