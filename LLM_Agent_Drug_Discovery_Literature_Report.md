# LLM-based Agents for Drug Discovery: 2024-2026 文献调研报告

检索日期：2026-05-24  
主题边界：仅纳入具备 agentic workflow 的 LLM/LM 系统，包括规划、工具调用、RAG、多智能体协作、记忆、反思/纠错、约束控制、人类监管、实验/计算环境交互或闭环执行。普通 LLM 问答、普通 RAG、单纯分子生成/性质预测模型不作为核心文献。

核验说明：本环境的 shell 直接下载 PDF 时遇到 DNS/网络沙箱限制；因此本报告的 PDF 核验以浏览器/检索工具打开的 arXiv、ACL、AAAI、OpenReview、PMC、publisher full text/PDF 页面为准。标为 “Original metadata + PDF source” 的条目已找到原始 PDF 来源但仍建议在正式投稿前逐页复核；标为 “Confirmed by PDF/PMC/publisher full text” 的条目已经基于原始全文入口核验 agent 与任务证据。

## 1. 检索方法说明

### 数据源与入口

本轮检索使用开放网络检索并交叉核验原始论文入口，重点覆盖：

- arXiv / bioRxiv / medRxiv / PMC / PubMed
- ACL Anthology, OpenReview, AAAI proceedings, NeurIPS/OpenReview pages
- ACS Publications, ScienceDirect, Oxford Academic, Nature portfolio 页面
- GitHub / project pages / publisher landing pages
- Google-Scholar-style web query、Semantic Scholar/DBLP/Sciety/Papers With Code/Hugging Face paper pages作为元数据辅助，不作为最终核心判断依据

### 关键词

使用并扩展了以下组合：

- `"LLM agent" AND "drug discovery"`
- `"language agent" AND "drug discovery"`
- `"multi-agent" AND "drug discovery"`
- `"RAG agent" AND "drug discovery"`
- `"tool-augmented LLM" AND "drug discovery"`
- `"LLM agents" AND "molecular design"`
- `"LLM agent" AND "ADMET"`
- `"LLM agent" AND "target discovery"`
- `"LLM agent" AND "wet lab"`
- `"LLM agent" AND "closed-loop drug discovery"`
- `"DrugPilot"`, `"DrugAgent"`, `"Mozi Governed Autonomy"`, `"RAG-Enhanced Collaborative LLM Agents for Drug Discovery"`, `"Constraint-Aware Corrective Memory"`, `"CoFEE Reasoning Control"`
- 扩展：`PharmAgents`, `LIDDIA`, `AgentD`, `FROGENT`, `MADD`, `Tippy`, `DrugMCTS`, `Medea`, `Biomni`, `TxAgent`, `CACTUS`, `CIDD`

### 纳入/排除标准

核心纳入必须同时满足：

1. 明确属于 LLM/language/AI agent，或包含可证实的 agentic workflow；
2. 直接应用于药物发现、分子设计、靶点发现、药物重定位、DTI、ADMET、虚拟筛选、实验规划、湿实验自动化或治疗发现；
3. PDF/原文中可定位 agent 机制与药物发现任务证据。

排除或降级：

- 仅问答、摘要、NER、文献挖掘的 LLM 药物论文；
- 仅分子生成、GNN、扩散模型、蛋白语言模型、虚拟筛选模型，但没有 agentic planning/tool use/memory/reflection；
- 普通 RAG，无规划/工具执行/多智能体/反馈；
- 通用科学 agent，除非与药物发现或生物医学发现有直接任务交集。

### 真实性状态定义

- **Confirmed by PDF/original full text**：打开了原始 PDF、PMC 全文、ACL/AAAI/OpenReview PDF 或 publisher full text，并核验 agent 与任务证据。
- **Original metadata + PDF source**：找到原始论文页和 PDF 链接，但本轮没有完整逐页核验，不能作为最终已确认核心。
- **Unverified preprint**：预印本存在，但版本/全文细节需二次核查。
- **Possibly unrelated / excluded**：题名相似或技术相关，但不属于药物发现 agent 核心。

### 可能漏检风险

- Google Scholar、IEEE Xplore、ACM DL、Elsevier/Wiley 等部分出版商全文可能被索引滞后或访问受限。
- 2026 年论文可能存在 “online first / future issue / preprint revised after publication” 的版本差异。
- arXiv 题名和正式发表题名可能不一致，例如 CIDD 与 FROGENT。
- `DrugAgent` 是高风险同名项：至少包含 ML-programming DrugAgent 与 DTI/repurposing DrugAgent 两条独立工作线。

## 2. 核心文献总表

字段压缩说明：Agent 类型可多选；RAG/Mem/Plan/Refl/Gov/Wet 分别表示 RAG、长期/纠错记忆、规划、反思/反馈、治理/安全/人类监管、湿实验。`推荐引用` 为综述写作中的建议版本。

| # | 论文 | 作者/机构 | 年份/渠道 | 链接与PDF来源 | 状态 | Agent证据 | 任务证据 | 类型 | 主要任务 | LLM/工具 | RAG/Mem/Plan/Refl/Gov/Wet | 推荐引用 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | **DrugPilot: LLM-based Parameterized Reasoning Agent for Drug Discovery** | Kun Li, Zhennan Wu, Shoupeng Wang, Jia Wu, Shirui Pan, Wenbin Hu；另有 Research Square 版本作者顺序/列表差异 | 2025 arXiv；Research Square v1 | arXiv:2505.13940；Research Square DOI 10.21203/rs.3.rs-7489358/v1 | **version conflict; core candidate** | Abstract/Method: LLM-based agent, parameterized reasoning, memory pool, tool calling | 8 个药物发现任务、Berkeley function-calling style evaluation | single/tool/memory agent | 多任务药物发现、工具调用、数据整合 | LLM + drug tools；具体工具需二次PDF表格核对 | RAG? / Mem✓ / Plan✓ / Refl部分 / Gov- / Wet- | 建议先引用 arXiv latest；正式投稿前核对 Research Square 与 arXiv 作者/版本 |
| 2 | **DrugAgent: Automating AI-aided Drug Discovery Programming through LLM Multi-Agent Collaboration** | Sizhe Liu, Yizhou Lu, Siyu Chen, Xiyang Hu, Jieyu Zhao, Tianfan Fu, Yue Zhao | 2024 arXiv CoRR；v2 2025-03-05 | arXiv:2411.15692 | **Confirmed original metadata + PDF source; core** | Abstract/Method: multi-agent framework, Planner + Instructor, automated ML programming | ADMET、DTI 等 AI-aided drug discovery programming | multi-agent/tool/code agent | ML pipeline generation, ADMET/DTI | LLM agents + code/data/model tools | RAG? / Mem- / Plan✓ / Refl部分 / Gov- / Wet- | 引用 arXiv v2（若无正式版） |
| 3 | **DrugAgent / DruGagent: Explainable Drug Repurposing Agent with LLM-based Reasoning / Multi-Agent LLM-Based Reasoning for DTI Prediction** | Yoshitaka Inoue, Tianci Song, Xinlin Wang, Augustin Luna, Tianfan Fu；早期 arXiv authors 也有 3 人版本 | 2024 arXiv；2025 MLGenX/OpenReview workshop；PMC full text | arXiv:2408.13378；OpenReview MLGenX PDF；PMC12036430 | **Confirmed by PMC/OpenReview; core** | Method: Coordinator, KG Agent, AI Agent, Search Agent, CoT/ReAct | DTI prediction, drug repurposing, kinase inhibitor benchmark | multi-agent/RAG/tool/reasoning | DTI, drug repurposing | GPT-4o/o3-mini/GPT-4o-mini；DrugBank, DGIdb, CTD, STITCH, DeepPurpose, Bing/literature | RAG✓ / Mem- / Plan✓ / Refl部分 / Gov- / Wet- | 若引用 DTI 完整版，优先 OpenReview/PMC 版本；说明与 #2 不是同一工作 |
| 4 | **RAG-Enhanced Collaborative LLM Agents for Drug Discovery (CLADD)** | Namkyeong Lee, Edward De Brouwer, Ehsan Hajiramezanali, Tommaso Biancalani, Chanyoung Park, Gabriele Scalia；KAIST, Genentech | AAAI-26；arXiv:2502.17506 | AAAI PDF；GitHub Genentech/CLADD | **Confirmed by AAAI PDF; core** | Abstract/Method: RAG-empowered agentic system, multiple LLM agents | drug discovery tasks with biomedical KB retrieval and molecule contextualization | multi-agent/RAG/tool | molecule QA/property/binding-related tasks | General LLMs + biomedical KBs | RAG✓ / Mem- / Plan✓ / Refl部分 / Gov- / Wet- | 引用 AAAI-26 proceedings，arXiv 作补充 |
| 5 | **LIDDIA: Language-based Intelligent Drug Discovery Agent** | Reza Averly, Frazier N. Baker, Ian A. Watson, Xia Ning；Ohio State University + independent researcher | EMNLP 2025 main；PMC/PubMed | DOI 10.18653/v1/2025.emnlp-main.603；PMC12765491；ACL PDF | **Confirmed by PDF/PMC; core** | Intro/Method: autonomous agent, Reasoner, Executor, Evaluator, Memory | autonomous in-silico drug discovery; clinically relevant targets; molecule generation | single-agent/memory/tool/evaluator | molecular generation, optimization, target-oriented design | LLM + molecule generation/evaluation tools | RAG? / Mem✓ / Plan✓ / Refl✓ / Gov- / Wet- | 引用 EMNLP 2025 / ACL Anthology |
| 6 | **Large Language Model Agent for Modular Task Execution in Drug Discovery (AgentD)** | Janghoon Ock et al.; CMU, Univ. Nebraska-Lincoln, Texas A&M | JCIM 2026, 66(4), 2055-2068；bioRxiv 2025 | DOI 10.1021/acs.jcim.5c02454；PMC12933718 | **Confirmed by ACS/PMC; core** | Agentic Workflow / Methods: LLM agent with six task modules | data extraction, RAG QA, SMILES generation, property prediction/refinement, protein-ligand structures | single/tool/RAG modular agent | early computational drug discovery | GPT-4o, Claude-3.7, DeepSeek; UniProt, ChEMBL, Serper, Semantic Scholar, REINVENT, Mol2Mol, DeepPK, BAPULM, Boltz-2 | RAG✓ / Mem- / Plan✓ / Refl部分 / Gov- / Wet- | 引用 JCIM 2026 正式版 |
| 7 | **PharmAgents: Building a Virtual Pharma with Large Language Model Agents** | Bowen Gao, Yanwen Huang, Yiqiao Liu, Wenxuan Xie, Wei-Ying Ma, Ya-Qin Zhang, Yanyan Lan；Tsinghua AIR 等 | 2025 arXiv | arXiv:2503.22164 | **Original metadata + PDF source; core candidate** | Abstract/Method: virtual pharmaceutical ecosystem, 22 specialized agents | target discovery to preclinical evaluation | multi-agent/hierarchical/tool/memory | target discovery, design, development, preclinical in silico | GPT-4; specialized ML/computational tools | RAG? / Mem✓ / Plan✓ / Refl✓ / Gov部分 / Wet- | 引用 arXiv latest；正式投稿前补全文核验 |
| 8 | **FROGENT: An End-to-End Full-process Drug Design Agent / Multi-Agent System** | Qihua Pan, Dong Xu, Jenna Xinyi Yao, Lijia Ma, Zexuan Zhu, Junkai Ji；Shenzhen University ADDG | 2025 arXiv | arXiv:2508.10760 | **Original metadata + PDF source; core candidate** | Abstract: Full-pROcess druG dEsign ageNT, MCP, dynamic workflow execution | target identification, molecule generation, retrosynthesis, virtual screening, mechanism analysis | tool/MCP/full-process agent | full-process drug design | GPT-4o, Qwen3-32B baselines; biochemical DBs, tool libraries, task models | RAG? / Mem? / Plan✓ / Refl部分 / Gov部分 / Wet- | 引用 arXiv latest |
| 9 | **MADD: Multi-Agent Drug Discovery Orchestra** | Gleb V. Solovev et al. | 2025 Findings EMNLP/arXiv | arXiv:2511.08217；ACL Findings PDF | **Confirmed original PDF source; core** | Abstract/Architecture: four coordinated agents, natural-language query to hit-identification pipelines | de novo generation, screening, hit identification, benchmark over >3M compounds | multi-agent/tool/orchestration | hit identification | LLM + generation/screening/docking/property tools | RAG? / Mem- / Plan✓ / Refl部分 / Gov- / Wet- | 引用 ACL/Findings PDF if accepted version is final |
|10| **Accelerating Drug Discovery Through Agentic AI: A Multi-Agent Approach to Laboratory Automation in the DMTA Cycle (Tippy)** | Yao Fehlis et al.; Artificial, Inc. | 2025 arXiv | arXiv:2507.09023 | **Original metadata + PDF source; core for lab automation; wet-lab claims need caution** | Abstract: Supervisor, Molecule, Lab, Analysis, Report agents + safety guardrail | DMTA laboratory automation | multi-agent/closed-loop/lab automation | design-make-test-analyze | OpenAI Agents SDK; Artificial platform; HPLC/lab tools claimed | RAG? / Mem? / Plan✓ / Refl✓ / Gov✓ / Wet✓/claimed | 引用 arXiv v1；将“生产/闭环”宣称单独审慎分析 |
|11| **Technical Implementation of Tippy: Multi-Agent Architecture and System Design for Drug Discovery Laboratory Automation** | Yao Fehlis et al.; Artificial, Inc. | 2025 arXiv | arXiv:2507.17852 | **Confirmed original metadata; supplement** | Methods: Kubernetes microservices, five agents, MCP, OpenAI Agents SDK, vector DB | lab automation infrastructure | multi-agent/MCP/RAG/governed | DMTA system architecture | MCP, Kubernetes, Helm, Docker, Envoy, vector DB | RAG✓ / Mem? / Plan✓ / Gov✓ / Wet✓/infrastructure | 与 Tippy conceptual paper 合并引用为系统系列 |
|12| **Mozi: Governed Autonomy for Drug Discovery LLM Agents** | He Cao, Siyu Liu, Fan Zhang, Zijing Liu, Hao Li, Bin Feng, Shengyuan Bai, Leqing Chen, Kai Xie, Yu Li | 2026 arXiv | arXiv:2603.03655 | **Original metadata + PDF source; core** | Abstract: governed supervisor-worker hierarchy, constrained action spaces, reflection-based replanning | target identification to lead optimization skill graphs | governed/tool/supervisor-worker agent | full-pipeline computational drug discovery | tool-augmented LLM + skill graphs | RAG? / Mem? / Plan✓ / Refl✓ / Gov✓ / Wet- | 引用 arXiv v1，待正式发表 |
|13| **Constraint-Aware Corrective Memory for Language-Based Drug Discovery Agents (CACM)** | Maochen Sun, Youzhi Zhang, Gaofeng Meng | 2026 arXiv | arXiv:2604.09308 | **Confirmed original metadata + PDF source; core** | Abstract: protocol auditing, grounded diagnostician, corrective memory | set-level molecule candidate satisfaction; binding/diversity/developability constraints | memory/corrective/governed agent | molecule-set optimization | language-based agent + molecular evidence/tools | RAG? / Mem✓ / Plan✓ / Refl✓ / Gov✓ / Wet- | 引用 arXiv v1 |
|14| **DrugMCTS: a drug repurposing framework combining multi-agent, RAG and Monte Carlo Tree Search** | Z. Yang, Y. Wan, Y. Li, Y. Matsuda, T. Xie, L. Song | 2025 arXiv | arXiv:2507.07426 | **Original metadata only; candidate core, needs PDF pass** | Abstract refs: five specialized agents + MCTS + RAG | DrugBank/KIBA drug repurposing/DTI | multi-agent/RAG/search | drug repurposing | Qwen2.5-7B-Instruct; DrugBank/KIBA | RAG✓ / Mem- / Plan✓ / Refl via search / Gov- / Wet- | 不作为已确认核心，需全文核验后纳入 |
|15| **Medea: An omics AI agent for therapeutic discovery** | Pengwei Sui et al.; Harvard Medical School, Broad, Imperial, King's | 2026 bioRxiv/PMC/PubMed | DOI 10.64898/2026.01.16.696667；PMC12871667 | **Confirmed by PMC; core for target/therapeutic discovery** | Abstract/Results/Methods: planning, analysis execution, literature reasoning, multi-round discussion, verification | target nomination, synthetic lethality, immunotherapy response | tool/RAG/verification/multi-module agent | target discovery, therapeutic hypothesis | GPT-4o, Gemini, o3-mini; 20 omics/literature/tools | RAG✓ / Mem? / Plan✓ / Refl✓ / Gov✓/verification / Wet- | 引用 bioRxiv/PMC preprint |
|16| **Prompt-to-Pill: Multi-Agent Drug Discovery and Clinical Simulation Pipeline** | authors to verify in publisher PDF; ChatMED project | 2025/2026 PMC | PMC12800774; GitHub ChatMED/Prompt-to-Pill | **Confirmed by PMC; supplement/core-adjacent** | Intro/Architecture: orchestrator + molecule/docking/property/trial/patient/outcome agents | molecule-to-virtual trial simulation | multi-agent/orchestrator | drug discovery + clinical simulation | LLM agents + docking/property/trial tools | RAG? / Mem? / Plan✓ / Refl部分 / Gov部分 / Wet-/simulation | 可作“drug development extension”而非严格早期发现核心 |
|17| **TxAgent: An AI Agent for Therapeutic Reasoning Across a Universe of Tools** | Shanghua Gao, Richard Zhu, Zhenglun Kong, Ayush Noori, Xiaorui Su, Curtis Ginder, Theodoros Tsiligkaridis, Marinka Zitnik；Harvard/MIT Lincoln/Broad | 2025 arXiv | arXiv:2503.10970；project page | **Confirmed original source; supplemental** | Abstract: multi-step reasoning, real-time retrieval, 211 tools, structured function calls | therapeutic reasoning, drug interactions, treatment selection | tool/RAG/single-agent | precision therapeutics, drug safety | TxAgent + ToolUniverse 211 tools, OpenFDA, OpenTargets | RAG✓ / Mem? / Plan✓ / Refl✓ / Gov✓ / Wet- | 背景/补充，不列为药物发现核心 |
|18| **Biomni: A General-Purpose Biomedical AI Agent** | Kexin Huang et al.; Stanford and collaborators | 2025 bioRxiv/PMC | DOI 10.1101/2025.05.30.656746；PMC12157518 | **Confirmed by PMC; background/supplement** | Results/Methods: unified action space, reasoning, retrieval, code execution | includes drug repurposing/gene prioritization but broad biomedical | general biomedical/code/tool agent | biomedical research automation | 105 software, 150 bio tools, 59 databases | RAG✓ / Mem? / Plan✓ / Refl/code debugging / Gov✓ / Wet protocols only | 背景与方法启发，不作为药物发现专属核心 |
|19| **CACTUS: Chemistry Agent Connecting Tool-Usage to Science** | ACS Omega authors; exact author list from ACS PDF to cite | 2024 ACS Omega; arXiv:2405.00972 | DOI 10.1021/acsomega.4c08408 | **Confirmed publisher full text; supplemental** | Abstract/Methods: LLM-based chemistry agent, LangChain tool use | cheminformatics/molecular property queries, drug-likeness descriptors | tool-augmented chemistry agent | cheminformatics/property | RDKit descriptors: MolWt, LogP, TPSA, QED, etc. | RAG- / Mem- / Plan有限 / Refl- / Gov- / Wet- | 补充文献；不是完整 drug discovery agent |
|20| **CIDD: Collaborative Intelligence for Structure-Based Drug Design Empowered by LLMs** | Bowen Gao et al.; Tsinghua AIR, PKU, SCUT, CityU HK, BAAI | NeurIPS 2025/OpenReview | OpenReview PDF; arXiv earlier title 2503.01376 | **Confirmed by OpenReview PDF; edge/supplement** | Method: LLM-enhanced drug designer with design/reflection modules, but not explicitly agent system | SBDD, molecule generation, drug-likeness, synthetic accessibility | reflective LLM workflow; not clear agent | structure-based molecular design | LLM + 3D SBDD generators, QikProp/docking metrics | RAG- / Mem- / Plan部分 / Refl✓ / Gov- / Wet- | 作为“agentic workflow 边界案例”，不列核心 agent |
|21| **CoFEE: Reasoning Control for LLM-Based Feature Discovery** | Maximilian Westermann et al.; Oxford/Vela/Amazon affiliations reported | 2026 arXiv | arXiv:2604.21584 | **Confirmed original source; excluded from drug core** | Reasoning control, decomposition, verification, backtracking | 非药物发现；quant VC feature discovery | reasoning-control workflow | feature discovery | LLM prompting | RAG- / Mem- / Plan✓ / Refl✓ / Gov✓ / Wet- | 指定分析但排除；可作为可信 reasoning-control 启发 |

## 3. 代表性论文深度分析

### 3.1 DrugPilot

- **定位**：参数化推理 agent，用于跨模态/异构药物发现数据处理、多工具调用、多阶段任务执行。
- **核心机制**：parameterized reasoning + parameterized memory pool，将公有数据和用户输入标准化为参数化表示，缓解多轮对话的信息损失。
- **评价**：构造 drug instruction dataset，按 Berkeley function-calling 风格评估 simple / multi-tool / multi-turn 任务，报告 98.0%、93.5%、64.0% 完成率。
- **版本问题**：arXiv 记录与 Research Square 版本在作者顺序/作者数量上存在差异。综述投稿前必须以最终 PDF 为准；若尚无正式期刊/会议版，建议引用 arXiv latest 并在文献管理中记录 Research Square DOI。
- **局限**：主要是函数调用与计算 workflow 能力；缺少真实湿实验和候选分子生物活性验证。

### 3.2 DrugAgent: AI-aided drug discovery programming

- **定位**：多智能体自动化 ML 编程系统，而不是直接分子生成器。
- **核心机制**：Planner 生成研究/建模想法，Instructor 识别领域需求并构造工具，执行从数据获取、代码实现到模型评估的 pipeline。
- **任务**：ADMET、DTI 等药物发现 ML 任务；案例中可完成 PAMPA absorption prediction，随机森林 F1=0.92。
- **贡献**：把 LLM agent 的价值从“回答药物问题”转为“自动构建和评估药物发现 ML pipeline”。
- **局限**：自治对象是编程/建模流程，不是实验发现流程；对生成代码的正确性、数据泄漏、重复运行稳定性仍需严格审计。

### 3.3 DrugAgent/DruGagent: DTI and repurposing

- **定位**：面向 DTI/药物重定位的解释性多智能体推理系统。
- **核心机制**：Coordinator 调度 AI Agent、KG Agent、Search Agent；结合 ML DTI score、DrugBank/DGIdb/CTD/STITCH 知识图谱路径和文献证据。
- **LLM**：GPT-4o、o3-mini、GPT-4o-mini 在不同模块/版本中出现。
- **评价**：kinase inhibitor dataset；相比 non-reasoning GPT-4o-mini F1 从 0.355 到 0.514，AUROC/AUPRC 也报告提升；有消融 w/o Search/KG/AI。
- **局限**：没有真实体外验证；DTI ground truth 与数据库偏差会影响结论。解释路径提高可审计性，但不等于真实机制证明。

### 3.4 CLADD: RAG-Enhanced Collaborative LLM Agents

- **定位**：Genentech/KAIST 的 RAG + 多 agent 药物发现框架。
- **核心机制**：多个 LLM agents 分工检索、分子上下文化、多源证据整合；目标是避免为每个任务进行昂贵 domain-specific fine-tuning。
- **正式版本**：AAAI-26 proceedings 是推荐引用版本；arXiv:2502.17506 可作为预印本记录。
- **创新**：将 RAG 从“检索增强回答”提升为 agent collaboration，强调 heterogeneous biochemical data、ambiguity、多源整合。
- **局限**：仍是计算/benchmark 层面的验证；没有药效湿实验闭环。

### 3.5 Mozi

- **定位**：治理型自治 drug discovery LLM agents。
- **核心机制**：双层架构。Control Plane 采用 supervisor-worker、role-based tool isolation、constrained action spaces、reflection-based replanning；Workflow Plane 将 Target Identification 到 Lead Optimization 形式化为 stateful skill graphs。
- **可信性价值**：明确将工具权限、数据契约、HITL checkpoint、trace-level auditability 放在架构中心。
- **评价**：PharmaBench 和 end-to-end in-silico case studies。
- **局限**：截至本轮为 2026 arXiv 预印本；真实湿实验与独立复现仍缺。

### 3.6 CACM

- **定位**：针对 language-based drug discovery agents 的 constraint-aware corrective memory。
- **核心机制**：protocol auditing + grounded diagnostician，对候选集整体的 set-level requirements 进行诊断：数量、多样性、binding quality、developability；再写回 concise corrective memory。
- **创新点**：把 agent 失败定位从“粗糙自我反思”推进到“协议级诊断 + 紧凑记忆回写”。
- **评价**：报告 target-level success rate 相比 SOTA baseline 提升 36.4%。
- **局限**：计算指标依赖协议定义和代理评估器；缺少湿实验。

### 3.7 CoFEE

- **结论**：不属于药物发现核心文献。
- **原因**：研究对象是复杂非结构化数据的 feature discovery，论文语境为 quant venture capital，不涉及药物发现、分子设计、靶点、ADMET 或实验。
- **为何仍值得分析**：其 backward chaining、subgoal decomposition、observability/leakage verification、backtracking 对药物发现 agent 的可信 reasoning-control 很有启发，尤其适合迁移到 ADMET 特征设计、临床/组学特征泄漏控制和实验前可观测性约束。
- **综述位置**：放在“可信 reasoning-control 背景/启发”或“排除但易误纳入”。

## 4. 技术分类框架 Taxonomy

### 4.1 按 Agent 架构

| 类别 | 定义 | 代表论文 |
|---|---|---|
| Single modular LLM agent | 一个中心 LLM 调度多个任务模块/工具 | LIDDIA, AgentD, TxAgent, Biomni |
| Multi-agent collaboration | 多角色 agent 分工、通信、协作 | DrugAgent #2, DrugAgent/DruGagent, CLADD, PharmAgents, MADD, Tippy |
| RAG-enhanced agent | 检索不仅提供上下文，还驱动证据整合与工具选择 | CLADD, AgentD, TxAgent, Medea, Biomni, Tippy technical |
| Tool-augmented agent | LLM 调用数据库、预测模型、生成模型、docking/结构工具 | CACTUS, AgentD, FROGENT, DrugPilot, Mozi |
| Memory/corrective agent | 长期记忆、经验库、纠错记忆、候选集级诊断 | LIDDIA, DrugPilot, PharmAgents, CACM |
| Reflective/corrective agent | evaluator/reflection/backtracking/replanning | LIDDIA, CACM, CIDD, Mozi, CoFEE |
| Governed autonomous agent | 权限隔离、HITL、约束动作空间、审计轨迹 | Mozi, Tippy, Medea, TxAgent |
| Closed-loop wet-lab/lab-automation agent | 连接实验平台、LIMS/ELN、仪器和实验反馈 | Tippy 系列；目前证据仍需谨慎 |

### 4.2 按药物发现流程

| 流程阶段 | Agent 作用 | 代表论文 |
|---|---|---|
| Knowledge acquisition | 文献/数据库检索、证据归因 | CLADD, AgentD, TxAgent, Medea |
| Hypothesis generation | 生成靶点/药物重定位/机制假设 | Medea, Biomni, DrugAgent/DruGagent, PharmAgents |
| Target identification | 组学/疾病上下文靶点提名 | Medea, PharmAgents, FROGENT |
| Molecular design | 分子生成、结构合理性、药物化学反馈 | LIDDIA, AgentD, CIDD, PharmAgents, MADD |
| Virtual screening / DTI | docking, DTI, hit identification | DrugAgent/DruGagent, MADD, DrugMCTS, FROGENT |
| Property/ADMET | 性质预测、ADMET、多目标优化 | AgentD, DrugAgent #2, DrugPilot, FROGENT |
| Experimental planning | 设计实验方案、协议、资源调度 | Tippy, Biomni, Mozi |
| Wet-lab validation | 自动化合成/分析/反馈 | Tippy claims closest; confirmed biology wet-lab validation remains sparse |
| Decision feedback | 反思、纠错记忆、候选集修复 | LIDDIA, CACM, Mozi |

### 4.3 按自治程度

1. **Assistant-level agent**：CACTUS, TxAgent；能调用工具与解释，但多为辅助。
2. **Workflow orchestration agent**：AgentD, DrugPilot, FROGENT；能串联工具/模块完成多步流程。
3. **Decision-support agent**：CLADD, DrugAgent/DruGagent, Medea；输出带证据的科学决策。
4. **Semi-autonomous discovery agent**：LIDDIA, PharmAgents, MADD；可自主探索候选分子/靶点，但仍是 in silico。
5. **Human-supervised autonomous agent**：Mozi, Tippy；强调治理、HITL、审计。
6. **Closed-loop autonomous discovery system**：目前只有 Tippy 接近，但还不足以证明“可信药物发现闭环”。

### 4.4 按可信性机制

| 可信性机制 | 作用 | 代表论文 |
|---|---|---|
| Retrieval grounding | 减少静态知识过时和幻觉 | CLADD, TxAgent, Medea, AgentD |
| Tool verification | 用工具输出替代纯文本猜测 | AgentD, FROGENT, CACTUS |
| Constraint-aware reasoning | 对候选集合/协议要求进行硬约束 | CACM, Mozi |
| Memory correction | 将失败原因压缩为后续可用状态 | CACM, LIDDIA, DrugPilot |
| Uncertainty/abstention | 低信心时拒答或保守输出 | Medea |
| Human governance | HITL checkpoint、权限隔离 | Mozi, Tippy |
| Wet-lab validation | 用实验而非 benchmark 支撑发现 | 当前缺口最大 |
| Audit trail/reproducibility | trace、日志、版本化配置 | Tippy technical, Mozi, Biomni |

## 5. 发展脉络：2024-2026

### 2024：工具增强与多智能体雏形

2024 年的代表是 DrugAgent/DruGagent 和 DrugAgent ML programming。前者把 ML、KG、文献检索组织为 DTI/repurposing 多智能体推理；后者把药物发现中的 AI/ML 编程自动化，说明 agent 的价值不只是生成答案，而是执行科研计算流程。CACTUS 代表化学工具调用 agent 的基础范式。

### 2025：从单任务工具调用走向全流程 in-silico discovery

2025 年出现 CLADD、LIDDIA、PharmAgents、FROGENT、MADD、Tippy、CIDD、DrugMCTS 等。技术主线从 RAG/工具增强转向多角色协作、分子生成-评估-反馈、多任务 benchmark、虚拟制药公司、DMTA 实验室自动化架构。

### 2026：可信自治、治理、记忆纠错、治疗/组学发现

2026 年的代表是 Mozi、CACM、AgentD 正式发表、Medea。方向从“能串工具”转向“能被监管、能纠错、能审计、能验证”。AgentD 将模块化早期发现任务落实到正式 JCIM；Medea 强调 verification-aware omics discovery；CACM 和 Mozi 直接针对 long-horizon reliability 与安全治理。

## 6. 可信性与湿实验分析

### 6.1 真正涉及湿实验或实验平台的工作

| 论文 | 实验是否真实完成 | Agent作用 | 证据强度 | 可信性判断 |
|---|---|---|---|---|
| Tippy conceptual + technical | 声称连接 DMTA lab automation、HPLC/实验平台；需要逐页核验真实合成/分析数据 | Supervisor/Molecule/Lab/Analysis/Report 协作，Lab Agent 控制实验作业 | 中等：架构和平台集成强，但药效/生物活性弱 | 可支撑“实验室自动化 agent”，不足以单独证明“药物发现有效性” |
| Biomni | 包含 wet-lab protocols 与分子克隆等任务评估，但不是药物发现闭环 | 规划/代码/协议辅助 | 中等：广义 biomedical agent | 背景价值高，药物发现核心证据有限 |
| Medea | 无真实湿实验；使用已有组学/临床数据和工具 | 目标提名、合成致死、免疫治疗响应推理 | 强 in-silico evidence | 可信 computational therapeutic discovery，不是 wet-lab discovery |
| AgentD/LIDDIA/MADD/FROGENT/CLADD | 主要计算验证 | 生成、筛选、评估、解释 | 计算层面较强 | 不足以证明湿实验有效性 |

### 6.2 关键判断

- **真实湿实验闭环不足**：多数论文停留在 in silico benchmark、case study 或 workflow automation。
- **实验验证≠Agent 有效性**：即使候选分子在实验中有效，也要证明 agent 的规划/工具选择/反馈比人类或固定 pipeline 更好。
- **Tippy 最接近闭环**：但需要区分“实验室自动化平台能执行”与“agent 发现了有效药物”。
- **Medea/AgentD/LIDDIA 更诚实**：多将未来 wet-lab validation 作为后续工作，避免把计算 case study 过度称为 autonomous discovery。

## 7. 研究空白与未来方向

1. **缺少真实闭环实验**：当前缺少从 target -> molecule -> synthesis -> assay -> feedback -> redesigned molecule 的完整、公开、可复现闭环。
2. **缺少统一 benchmark**：PharmaBench、PharmaEval、各自自建任务难以横向比较。
3. **评测任务过浅**：函数调用、QA、单步 DTI 难以代表药物发现的长周期不确定性。
4. **工具调用可靠性不足**：参数错误、单位错误、版本差异、数据库漂移、API 失败会在长链条中累积。
5. **RAG 幻觉与证据追踪不足**：需要 provenance、citation-level grounding、冲突证据整合和证据强度评分。
6. **分子生成与可合成性脱节**：许多生成分子仅满足 QED/SA/docking，缺少真实合成可行性和反应路线成本。
7. **湿实验成本高、负结果少**：缺少失败案例、负样本、ablation-to-wet-lab 的因果证据。
8. **安全性、合规性、人类监管不足**：Mozi/Tippy 是少数将治理放进架构的工作；大多数系统缺少权限隔离和审计。
9. **从“能回答”到“能发现”的鸿沟**：发现需要提出可检验假设、选择实验、承受失败、迭代优化，而非只生成合理文本。
10. **Agent 过度包装风险**：部分工作本质是 pipeline 或 RAG QA，只因使用 LLM 被命名为 agent；综述应设置严格判据。

## 8. 综述论文建议大纲

### 标题建议

1. **From Tool-Augmented LLMs to Governed Autonomous Agents for Drug Discovery**
2. **LLM-based Agents for Drug Discovery: Architectures, Trustworthiness, and the Road to Closed-Loop Discovery**
3. **Beyond Chatbots: Agentic Large Language Models in Drug Discovery**

### 摘要主线

药物发现 LLM agent 的核心演进不是“更会回答药物问题”，而是从工具增强、RAG grounding、多智能体协作，逐步走向带记忆纠错、人类监管、审计轨迹和实验闭环的可信自治发现系统。当前证据主要支持计算辅助与 workflow orchestration，真实湿实验闭环仍是最大空白。

### 章节结构

1. **Introduction: Why Agentic Drug Discovery?**
   - 区分 LLM for drug discovery 与 LLM agent for drug discovery。
   - 代表：DrugAgent, LIDDIA, AgentD。

2. **Definition and Inclusion Criteria**
   - agentic workflow、工具调用、规划、记忆、反馈、环境交互。
   - 处理 CoFEE/CIDD/CACTUS 这类边界案例。

3. **Technical Taxonomy of Drug Discovery Agents**
   - single vs multi-agent；RAG/tool/memory/reflective/governed/closed-loop。
   - 代表：CLADD, DrugPilot, PharmAgents, Mozi, CACM。

4. **Agents Across the Drug Discovery Pipeline**
   - target discovery、molecular design、virtual screening、ADMET、experimental planning、wet-lab automation。
   - 代表：Medea, LIDDIA, AgentD, FROGENT, MADD, Tippy。

5. **Trustworthiness, Control, and Evaluation**
   - hallucination、tool failure、evidence provenance、constraint satisfaction、HITL。
   - 代表：Mozi, CACM, Medea, Tippy technical。

6. **Wet-lab and Closed-loop Evidence**
   - 什么证据才足以支持 autonomous discovery。
   - 重点讨论 Tippy 与现有 in-silico 工作的边界。

7. **Benchmarks and Reproducibility**
   - PharmaBench、PharmaEval、自建 benchmark、DTI/ADMET/CrossDocked 等。
   - 评价多步任务、失败恢复、工具可用性和负结果。

8. **Open Challenges and Future Roadmap**
   - 从工具调用到可信自治；从候选生成到实验因果验证；从单点指标到闭环科学发现。

## 9. 最终文献清单

### 核心文献

1. Li, K. et al. **DrugPilot: LLM-based Parameterized Reasoning Agent for Drug Discovery.** arXiv:2505.13940, 2025. Also Research Square DOI: 10.21203/rs.3.rs-7489358/v1. **Core; version conflict.**
2. Liu, S., Lu, Y., Chen, S., Hu, X., Zhao, J., Fu, T., Zhao, Y. **DrugAgent: Automating AI-aided Drug Discovery Programming through LLM Multi-Agent Collaboration.** arXiv:2411.15692, 2024/2025. **Core.**
3. Inoue, Y., Song, T., Wang, X., Luna, A., Fu, T. **DruGagent: Multi-Agent Large Language Model-Based Reasoning for Drug-Target Interaction Prediction.** arXiv:2408.13378; MLGenX/OpenReview/PMC, 2024/2025. **Core.**
4. Lee, N., De Brouwer, E., Hajiramezanali, E., Biancalani, T., Park, C., Scalia, G. **RAG-Enhanced Collaborative LLM Agents for Drug Discovery.** AAAI-26; arXiv:2502.17506. **Core.**
5. Averly, R., Baker, F. N., Watson, I. A., Ning, X. **LIDDIA: Language-based Intelligent Drug Discovery Agent.** EMNLP 2025, doi:10.18653/v1/2025.emnlp-main.603. **Core.**
6. Ock, J. et al. **Large Language Model Agent for Modular Task Execution in Drug Discovery.** Journal of Chemical Information and Modeling 66(4):2055-2068, 2026. doi:10.1021/acs.jcim.5c02454. **Core.**
7. Gao, B. et al. **PharmAgents: Building a Virtual Pharma with Large Language Model Agents.** arXiv:2503.22164, 2025. **Core candidate.**
8. Pan, Q. et al. **FROGENT: An End-to-End Full-process Drug Design Agent.** arXiv:2508.10760, 2025. **Core candidate.**
9. Solovev, G. V. et al. **MADD: Multi-Agent Drug Discovery Orchestra.** arXiv:2511.08217; Findings EMNLP PDF, 2025. **Core.**
10. Fehlis, Y. et al. **Accelerating Drug Discovery Through Agentic AI: A Multi-Agent Approach to Laboratory Automation in the DMTA Cycle.** arXiv:2507.09023, 2025. **Core for lab automation.**
11. Fehlis, Y. et al. **Technical Implementation of Tippy: Multi-Agent Architecture and System Design for Drug Discovery Laboratory Automation.** arXiv:2507.17852, 2025. **Supplement to Tippy.**
12. Cao, H. et al. **Mozi: Governed Autonomy for Drug Discovery LLM Agents.** arXiv:2603.03655, 2026. **Core.**
13. Sun, M., Zhang, Y., Meng, G. **Constraint-Aware Corrective Memory for Language-Based Drug Discovery Agents.** arXiv:2604.09308, 2026. **Core.**
14. Yang, Z. et al. **DrugMCTS: a drug repurposing framework combining multi-agent, RAG and Monte Carlo Tree Search.** arXiv:2507.07426, 2025. **Candidate core; needs PDF pass.**
15. Sui, P. et al. **Medea: An omics AI agent for therapeutic discovery.** bioRxiv/PMC, 2026. doi:10.64898/2026.01.16.696667. **Core-adjacent for therapeutic target discovery.**

### 补充文献

16. **Prompt-to-Pill: Multi-Agent Drug Discovery and Clinical Simulation Pipeline.** PMC12800774, 2025/2026. **Supplement/core-adjacent.**
17. Gao, S. et al. **TxAgent: An AI Agent for Therapeutic Reasoning Across a Universe of Tools.** arXiv:2503.10970, 2025. **Supplement.**
18. Huang, K. et al. **Biomni: A General-Purpose Biomedical AI Agent.** bioRxiv/PMC, 2025. doi:10.1101/2025.05.30.656746. **Background/supplement.**
19. **CACTUS: Chemistry Agent Connecting Tool-Usage to Science.** ACS Omega, 2024. doi:10.1021/acsomega.4c08408. **Chemistry agent supplement.**
20. Gao, B. et al. **CIDD: Collaborative Intelligence for Structure-Based Drug Design Empowered by LLMs.** NeurIPS 2025/OpenReview. **Edge/supplement.**

### 背景/综述

21. **Large language model agents for biological intelligence across genomics, proteomics, spatial biology, and biomedicine.** Briefings in Bioinformatics, 2026. **Background survey.**
22. **Application and progress of artificial intelligence agents in drug development.** PMC review, 2026. **Background survey.**
23. **Foundation models and AI agents in oncology drug discovery.** Drug Discovery Today, 2026. **Background review.**
24. **ChemCrow: Augmenting large-language models with chemistry tools.** Nature Machine Intelligence, 2024 publication of earlier arXiv work. **Background chemistry agent.**

### 排除但容易误纳入

25. Westermann, M. et al. **CoFEE: Reasoning Control for LLM-Based Feature Discovery.** arXiv:2604.21584, 2026. **Excluded from drug discovery core; reasoning-control inspiration only.**
26. 普通 Tx-LLM、GenMol、DrugGPT/DrugGen、protein language model、3D diffusion/GNN molecular generator：若没有 agentic workflow，仅作为背景。
27. 普通 RAG-based drug side-effect retrieval：若无规划、工具执行、多智能体或反馈，不作为核心 agent。
