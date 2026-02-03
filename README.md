# Clinical Protocol Safety Validator (CPSV)

Autonomous multi-agent AI system that audits clinical trial protocols for safety risks, regulatory compliance gaps, and ethical concerns before human trials begin.

The system coordinates three specialized 7B medical language models with Retrieval-Augmented Generation (RAG), ChromaDB vector storage, and real-time PubMed evidence retrieval to produce structured audit reports.

## Features

- Multi-agent collaborative analysis  
- Real-time PubMed literature search  
- RAG-powered context retrieval using ChromaDB  
- Parallel execution of agents  
- Gradio web interface for protocol submission and report viewing  
- Structured findings with severity levels, evidence, and recommendations  
- Executive summary and overall risk scoring  

## Agents

| Agent | Role                                    | Model ID                           | Developer       |
|-------|-----------------------------------------|------------------------------------|-----------------|
| A     | Medical Literature & Standard of Care   | epfl-llm/meditron-7b              | EPFL LLM Team   |
| B     | Inclusion/Exclusion & Safety Gaps       | BioMistral/BioMistral-7B          | BioMistral      |
| C     | Regulatory & Ethical Compliance         | dmis-lab/meerkat-7b-v1.0          | DMIS Lab        |

## Installation

```bash
git clone https://github.com/sufirumii/Clinical-Protocol-Safety-Validator-Medical-LLMs-.git
cd Clinical-Protocol-Safety-Validator-Medical-LLMs-

pip install torch gradio transformers requests chromadb accelerate bitsandbytes
Usage
Bashpython main.py

Open the local Gradio URL displayed in the terminal
Click "Initialize System" (model loading may take several minutes the first time)
Paste the clinical trial protocol text
Click "Validate Protocol"
Review the executive summary and detailed findings

Recommended hardware: GPU with at least 16 GB VRAM (quantization can help on 12–16 GB cards).
Important Disclaimer
This project is provided strictly for research and educational purposes.
It is not a medical device, clinical decision support tool, or regulatory validation system. The underlying models have not undergone clinical validation or randomized controlled trials. Outputs may contain hallucinations, omissions, biases, or incomplete reasoning.
Under no circumstances should the results be used to:

Make patient safety decisions
Approve or modify clinical trial protocols
Satisfy regulatory or IRB requirements
Influence any real-world medical or compliance action

All outputs must be independently verified by qualified physicians, regulatory affairs professionals, and ethics committees.
Use at your own risk.
Model References

Meditron-7B: https://huggingface.co/epfl-llm/meditron-7b
Paper: https://arxiv.org/abs/2311.16079
BioMistral-7B: https://huggingface.co/BioMistral/BioMistral-7B
Paper: https://arxiv.org/abs/2402.10373
Meerkat-7B: https://huggingface.co/dmis-lab/meerkat-7b-v1.0
Reference: npj Digital Medicine (2025) – Small language models learn enhanced reasoning skills from medical textbooks

Citation
If this work is useful in your research, please cite:
bibtex@misc{cpsv2026,
  title = {Clinical Protocol Safety Validator (CPSV) - Multi-Agent Clinical Trial Protocol Auditing},
  author = {Rumii},
  year = {2026},
  url = {https://github.com/sufirumii/Clinical-Protocol-Safety-Validator-Medical-LLMs-}
}

@misc{chen2023meditron,
  title = {MEDITRON-70B: Scaling Medical Pretraining for Large Language Models},
  author = {Zeming Chen and others},
  year = {2023},
  eprint = {2311.16079},
  archivePrefix = {arXiv}
}

@misc{labrak2024biomistral,
  title = {BioMistral: A Collection of Open-Source Pretrained Large Language Models for Medical Domains},
  author = {Yanis Labrak and others},
  year = {2024},
  eprint = {2402.10373},
  archivePrefix = {arXiv}
}

@article{kim2025small,
  title = {Small language models learn enhanced reasoning skills from medical textbooks},
  author = {Hyunjae Kim and others},
  journal = {npj Digital Medicine},
  volume = {8},
  number = {1},
  pages = {240},
  year = {2025}
}
License
Apache-2.0
