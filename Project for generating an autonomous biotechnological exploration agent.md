Project for generating an autonomous biotechnological exploration agent:

Important concepts/variables:

R – Report

E – Experiment design

O – Objective 

1. Structure of project
   1. Objective
   1. Data Repository
   1. Agents
1. Objective
   1. A goal articulated by the user.
      1. Defined
         1. Find a peptide that can bind to protein X in HeLa cells without binding to protein Y. 
      1. Undefined
         1. Cure aging
   1. Avenues of exploration:
      1. Having an undefined goal may result in a smaller scale paperclip problem.
      1. Undefined may also result in the model growing increasingly confused as our strategies to compress information grow harder to parse.
      1. I would guess this will be currently limited to tasks that involve concrete applications of known concepts.
      1. While this may be able to grapple more complex tasks involved in generating entirely new methods it will require more careful evaluation to ensure that the steps taken are reasonable as compared to applying known methods. 
1. Data repository
   1. This is the location for data related to the objective.
   1. Data classes
      1. Papers
         1. Requires multi-modal data ingestion tools. 
      1. Databases
         1. PDB,  https://data.rcsb.org/#data-api
      1. Data generated in the course of satisfying the objective.
      1. Books
      1. Lab notebooks
      1. Reports
   1. May be filled in via:
      1. Internet search
      1. Plug-ins1
      1. Semantic search of local database2
      1. API requests
1. The agents.
   1. Agents are fine-tuned models in charge of specific tasks.
   1. Judge
      1. Determines if a report given satisfies an objective.
      1. Responds with a score according to some rubric.
   1. Reporter
      1. Generates reports on what the status of the project is.
      1. Calls data from archivist 
      1. Reads research plan.
   1. Principle investigator
      1. Reads reports. 
      1. Initiates data queries for the data repository
      1. Generates research plans.
         1. What experiment types are required?
         1. What is the budget?
         1. Hypotheses and expected results?
   1. Experimental designers
      1. In sillico
      1. In vivo/vitro
      1. Initiates data queries for the data repository
      1. Reads research plans.
   1. Archivist
      1. Handles requests for information to the data repository.
      1. Determines if data in repository is sufficient or if an external request should be made.
      1. Compresses information requested into a format intelligible for the language model with the fewest number of tokens.
      1. Sends a completed cycle of research to the reporter
   1. Lab monkey
      1. Receives experimental designers specifications.
      1. API requests 
         1. Emerald Labs API3
      1. Write emails to a CRO
         1. White glove CRO Micah contracts
   1. Code monkey
      1. Receives experimental designers specifications.
      1. Intakes an experiment from the in-silico designer and designs code/API requests to execute the experiment.
         1. HADDOCK4
         1. ROSETTA5
            1. Cyrus biotechnologies6
         1. Alphafold7
         1. Etc.
   1. Data analyzer
      1. Intakes data from CRO or computational tool users 
      1. Runs statistical analysis. 
      1. Generates relevant figures.
      1. Writes short text snippets about the data.
      1. Sends to archivist. 
      1. Reads research plan.
1. Models that may be useful8
   1. Medical specific models9	

   1. chatGPT10
      1. GPT 3.5
      1. GPT 4
      1. GPT-plugin
   1. Llama11
   1. PaLM
      1. PaLM-E12
      1. medPaLM13
   1. Protein design14













(1)	*ChatGPT Gets Its “Wolfram Superpowers”!* https://writings.stephenwolfram.com/2023/03/chatgpt-gets-its-wolfram-superpowers/ (accessed 2023-04-10).

(2)	Leys, M. *Semantic search: a practical overview*. Medium. https://blog.ml6.eu/semantic-search-a-practical-overview-bf2515e7be76 (accessed 2023-04-10).

(3)	*Emerald Cloud Labs API Documentation*. https://www.emeraldcloudlab.com/internal-developers-api/ (accessed 2023-04-10).

(4)	*HADDOCK*. GitHub. https://github.com/haddocking (accessed 2023-04-10).

(5)	*Servers | RosettaCommons*. https://www.rosettacommons.org/software/servers#rosetta-at-cloud (accessed 2023-04-10).

(6)	Sam. *API | Cyrus Biotechnology*. https://support.cyrusbio.com/api/api/ (accessed 2023-04-10).

(7)	*Alphafold API - Developer docs, APIs, SDKs, and auth.* https://apitracker.io/a/alphafold (accessed 2023-04-10).

(8)	Zhao, W. X.; Zhou, K.; Li, J.; Tang, T.; Wang, X.; Hou, Y.; Min, Y.; Zhang, B.; Zhang, J.; Dong, Z.; Du, Y.; Yang, C.; Chen, Y.; Chen, Z.; Jiang, J.; Ren, R.; Li, Y.; Tang, X.; Liu, Z.; Liu, P.; Nie, J.-Y.; Wen, J.-R. A Survey of Large Language Models. arXiv March 31, 2023. https://doi.org/10.48550/arXiv.2303.18223.

(9)	Yang, X.; Chen, A.; PourNejatian, N.; Shin, H. C.; Smith, K. E.; Parisien, C.; Compas, C.; Martin, C.; Costa, A. B.; Flores, M. G.; Zhang, Y.; Magoc, T.; Harle, C. A.; Lipori, G.; Mitchell, D. A.; Hogan, W. R.; Shenkman, E. A.; Bian, J.; Wu, Y. A Large Language Model for Electronic Health Records. *Npj Digit. Med.* **2022**, *5* (1), 1–9. https://doi.org/10.1038/s41746-022-00742-2.

(10)	*Introducing ChatGPT*. https://openai.com/blog/chatgpt (accessed 2023-04-10).

(11)	*Introducing LLaMA: A foundational, 65-billion-parameter language model*. https://ai.facebook.com/blog/large-language-model-llama-meta-ai/ (accessed 2023-04-10).

(12)	*PaLM-E: An embodied multimodal language model – Google AI Blog*. https://ai.googleblog.com/2023/03/palm-e-embodied-multimodal-language.html (accessed 2023-04-10).

(13)	Singhal, K.; Azizi, S.; Tu, T.; Mahdavi, S. S.; Wei, J.; Chung, H. W.; Scales, N.; Tanwani, A.; Cole-Lewis, H.; Pfohl, S.; Payne, P.; Seneviratne, M.; Gamble, P.; Kelly, C.; Scharli, N.; Chowdhery, A.; Mansfield, P.; Arcas, B. A. y; Webster, D.; Corrado, G. S.; Matias, Y.; Chou, K.; Gottweis, J.; Tomasev, N.; Liu, Y.; Rajkomar, A.; Barral, J.; Semturs, C.; Karthikesalingam, A.; Natarajan, V. Large Language Models Encode Clinical Knowledge. arXiv December 26, 2022. https://doi.org/10.48550/arXiv.2212.13138.

(14)	Madani, A.; Krause, B.; Greene, E. R.; Subramanian, S.; Mohr, B. P.; Holton, J. M.; Olmos, J. L.; Xiong, C.; Sun, Z. Z.; Socher, R.; Fraser, J. S.; Naik, N. Large Language Models Generate Functional Protein Sequences across Diverse Families. *Nat. Biotechnol.* **2023**, 1–8. https://doi.org/10.1038/s41587-022-01618-2.

(15)	*The Role of ChatGPT-4 in the Future of Scientific Research: AI-driven Hypothesis Generation and Experiment Design – TS2 SPACE*. https://ts2.space/en/the-role-of-chatgpt-4-in-the-future-of-scientific-research-ai-driven-hypothesis-generation-and-experiment-design/ (accessed 2023-04-10).






















What I will be investigating:

1) Requirements for an MVP
   1) What agents are needed to answer a research question?
      1) Which of these agents are minimally required to produce a sensible experimental request?
         1) Ie. Reporter might be superfluous, and the PI can make the reports itself.
   1) What data is needed?
      1) What color is a liquid could probably be answered without any added data (run a spectrophotometer) but what protein binds ADK in a crowded environment might not. 
      1) How to access that data?
   1) What are the API requirements for the CRO’s?
      1) Can an API request be generated with prompt engineering instead of fine tuning individually?
      1) Can we have the AI scrape the internet for academics to contact about including in the project?
         1) Ie. Project requires a really obscure measurement that only a single lab in the world can do so it drafts an email to that professor asking if they wish to collaborate.
1) What other products exist that solve automated research and development?
   1) Are non-language model solutions already here? Are language model solutions here?
   1) People are talking about this but have no leads for it beyond academics directly asking with their own research. This was published yesterday 15
1) Which models are appropriate?
   1) Which ones are the best match for a given problem?
   1) Which ones are open source?


