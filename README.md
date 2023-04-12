# RoboResearcher🤖

An AI agent for automatically researching an objective, executing
experiments, analyzing, and creating a result using complex chains of
reasoning and tool use similar to [ART: Automatic Multi-Step Reasoning and Tool-Use for Large Language Models.](https://doi.org/10.48550/arXiv.2303.09014) [Language Model Cascades.](https://doi.org/10.48550/arXiv.2207.10342).

# Structure 🧱

![image](https://user-images.githubusercontent.com/47462814/231152697-e0f6d0ac-3e35-4328-9cb4-51ddd3d7d34e.png)

There are three groups that are capable of interacting: 
* User 
* Records 
* Agents

The User submits an objective to the Agents. The Agents generate and
execute a plan to reach the objective. Throughout this process the
Agents may query the Records to recieve pertinent information. The
Records may pull data from the internet, internal databases, or via
direct questions to the User.

## User 👤

-   Inputs: Judgment, Report, Question
-   Outputs: Objective, Answer

A User is a person who defines the objectives and answers questions that
the RoboResearchers may have. They are also the one who provides
funds/server time for the RoboResearcher to function.

### Objectives🥅

An objective is some goal defined by the user that they are attempting
to answer. When the Agents have completed a round of experimentation and
analysis a report with a self-determined judgment is given to the User
based on how close to the objective the report is.

A defined objective is preferred to prevent a paperclip scenario,
however poorly-defined objectives may be important in the long run to
create fully independent researchers.

-   Well-defined objective
    -   Find a peptide that can bind protein X without binding to
        protein Y.
-   Poorly-defined objective
    -   Cure aging

The need for a well-thought out research objective is [self evident](https://doi.org/10.7748/nr.23.4.19.s5), and the need for appropriate [prompt
engineering](https://github.com/dair-ai/Prompt-Engineering-Guide) further
emphasizes this leading to several areas of optimization:

-   [ ] What constitutes a well-defined objective
-   [ ] Scales of objective (eg. Identify the gene that causes CF
    vs. Create a cure for CF)
-   [ ] Language used (eg. Formal scientific verbiage vs. slang)
-   [ ] Organization (eg. Find a gene that causes CF and then simulate
    the protein it should make vs. simulate the protein that causes CF
    based on the gene)
-   [ ] [Complexity level](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2912019/) can Agents handle the
    more complex case of being presented a research question or
    hypothesis?

### Answers 🙋

When faced with ambiguity the Archivist may send a question to the User.
These questions will, hopefully, allow the User to help keep the
RoboResearchers focused and prevent wasting resources when the
RoboResearcher is confused.

The question-answer pair will be returned to the Archivist which can
then be used to answer the Agent that asked the question.

This is an area that has shown promise in [past research](https://doi.org/10.48550/arXiv.1712.01238) and the relevance to the scientific method cannot be understated.
The areas of research for this topic would be:

-   [ ] How much should we motivate Agents to ask questions?
-   [ ] How should we answer the questions?

## Records📚

-   Inputs: Answer, query
-   Outputs: Question, info

The records are a combination of an Agent and a database. The Agent,
henceforth known as the Archivist, handles queries from other Agents or
Users and compiles info for them to digest on the topic.

### Database🗄️

The database is a storage location for all data that might be relevant
to the tasks the Agents complete. The database can be added to via the
Archivist, the User, or the Agents. This can be queried through a
variety of possible mechanisms from standard search via pattern matching
to [semantic search methods](https://blog.ml6.eu/semantic-search-a-practical-overview-bf2515e7be76).

#### Types of data

-   User
    -   Uploaded data (eg. A csv of some data, a PDF of a paper)
    -   Connecting an extant database (eg. a home server)
-   Archivist
    -   Data queried from an API request (eg. the [PDB](https://www.rcsb.org/docs/programmatic-access/web-services-overview))
    -   Plugin (eg. [Wolfram Alpha](https://writings.stephenwolfram.com/2023/03/chatgpt-gets-its-wolfram-superpowers/))
    -   Info
-   Agents
    -   Generated data (eg. results from an [Alphafold](https://apitracker.io/a/alphafold) API call
    -   Reports, Experiments, results, plans, etc.

### Archivist 👘

-   Inputs: Answer, query

-   Outputs: Question, info 
   
   
The Archivist is a LM that is finetuned to handle requests for information from both Agents and Users alike.

he Archivist can execute several different actions:

-   Generate Database directory

-   Search Database

-   Query list of provided API’s

-   Send question to User

-   Prepare a compressed summery of information

-   Sends data to the Agent’s workspace

-   Send info

The exact order of actions for the Archivist will be left up to the User or Archivist to define. There are different methods to access and call information that will need to be explored:

-   [ ] Different [compression
    methods](https://twitter.com/VictorTaelin/status/1642664054912155648/photo/1)
    for reducing token usage and how that affects the quality
-   [ ] Sending data to an Agents workspace
-   [ ] Can a single Agent handle all the Archivists task
-   [ ] Which model is best suited for this task. Perhaps using tools
    such as [scite](https://scite.ai/). Although this is
    [APGL](https://github.com/MuiseDestiny/zotero-gpt).

## Agents 🕵️

-   Inputs: Objective, info
-   Outputs: Report, judgment

The role of Agents is to perform various research tasks. All Agents
except the Archivist are listed here, as the Archivist is part of the
Records system. Ideally these Agents will all be fine tuned for their
respective tasks such that minimal User interference will be required.
(eg. PI outputs Research plan in a format that the Experimental Designer
easily parses)

### Principle Investigator🧑‍🔬

Inputs: Objective, info Output: Research plan The info they request
should be related to: 
* Objective 
* Budget 
* Information on available equipment

The Principle investigators job is to build a research plan to tackle
the objective. This could be thought of as the highest level planner.

An illustrative example for a peptide generation problem:

![image](https://user-images.githubusercontent.com/47462814/231204480-08f5de60-88d4-47dc-b13f-f57fd5ca123a.png)

### Experimental Designer 🥼

-   Inputs: Plan, info
-   Outputs: Experiments

The Experimental Designer intakes plans from the principal investigator
and outputs a list of discrete experiments that are able to be run by
the Monkeys.

The info requested should be related to: 
* Plan 
* Equipment 
* Information on available equipment

An illustrative example:

![image](https://user-images.githubusercontent.com/47462814/231213330-67df6d9d-d07d-4f2c-ac08-856921a79db8.png)

### Monkey 🐵

Input: Experiment, info, data 
Outputs: API Calls, emails, code, data, query

The info they request should be related to: 
* Experiment 
* Budget 
* Information on available equipment

The monkey’s job is to translate an experiment into a format that can be
read by the appropriate API or CRO representative. Alternatively the
Monkey will begin attempting to execute code in a local environment to
complete the task required. If the Monkey runs into problems it asks the
Archivist for help.

#### API’s and other access points

The ability to make API calls is already confirmed through the coming of
[Toolformer](https://doi.org/10.48550/arXiv.2302.04761) and open source implementations are
already underway such as [here](https://github.com/conceptofmind/toolformer) and
[here](https://github.com/lucidrains/toolformer-pytorch). This implies
that the only real barrier here would be accessing information on the
API’s themselves and integrating them into the Toolformer framework, a
task that itself may be well suited to automation.

This is a short list of some places that might be useful to send API
calls for experimental purposes: 
* [HADDOCK](https://github.com/haddocking)
* [ROSETTA](https://www.rosettacommons.org/software/servers#rosetta-at-cloud)
* [Cyrus Biotechnologies](https://support.cyrusbio.com/api/api/)
* [Alphafold](https://apitracker.io/a/alphafold)
* [Emerald Cloud Labs](https://www.emeraldcloudlab.com/internal-developers-api/)
* etc.

Other CRO’s are still accessible via automated email requests if an
arrangement is made with an appropriate representative. If desired one
may even have the Monkey trawl the internet for academic research labs
doing similar experiments and send emails asking for a collaboration.

An illustrative example where the Monkey attempts to access BSA and runs
into problems with the URL and API key

![image](https://user-images.githubusercontent.com/47462814/231218694-665dac43-7b83-40e4-9514-b24e5244f7e2.png)
![image](https://user-images.githubusercontent.com/47462814/231218819-f765fa61-8608-4121-984c-752ca251fdc1.png)
![image](https://user-images.githubusercontent.com/47462814/231218955-a10a3217-c2dc-4ca2-b1f2-9c70fb24335b.png)
![image](https://user-images.githubusercontent.com/47462814/231220256-796357fb-a79a-4a69-96e3-369dfe97e876.png)

``` python
import required modules
import requests
import os

# Set the PDB API URL and API key
url = "https://this.com"
api_key = "1234ABCD"

# Define the PDB query to retrieve the BSA protein structure
query = {
  "query": {
    "type": "terminal",
    "service": "text",
    "parameters": {
      "value": "BSA"
    }
  },
  "return_type": "polymer_entity"
}

# Send the query to the PDB API to retrieve the BSA protein structure
response = requests.post(url, json=query, headers={"Authorization": api_key})
response_json = response.json()

# Get the BSA protein ID from the response
bsa_id = response_json["result_set"][0]["identifier"]

# Download the BSA protein structure in PDB format
pdb_url = f"{url}/download/downloadFile.do?fileFormat=pdb&id={bsa_id}"
response = requests.get(pdb_url)
pdb_data = response.content

# Save the BSA protein structure to a file
with open("bsa.pdb", "wb") as f:
    f.write(pdb_data)

# Open the BSA protein structure in Chimera
os.system("chimera bsa.pdb")

# Remove water molecules, ligands, and ions using Chimera
# Save the modified protein structure in PDB format
os.system("chimera --nogui --script 'open bsa.pdb; delete solvent; delete ligand; delete ion; write bsa_clean.pdb'")
```

If instead they are asked to send an email to a person to perform this
task:

![image](https://user-images.githubusercontent.com/47462814/231221893-22c0940e-ec69-4235-94cf-eee1e844285c.png)

### Data Analyst 📊

Inputs: Data, info, experiment

Outputs: Results, data, query

The info they request should be related to: 
* Objective 
* Data 
* Experiment

The Data Analyst is designed to ingest the data that resulted from the
Monkey’s work and extract meaningful results from them. This Agent may
require multiple intermediate steps wherein the result is fed back into
itself until a well analyzed corpus is created. This Agent may be stand
alone or be subsumed by the Monkey-Experimental Designer relationship,
wherein the Monkey simply continues ingesting and transforming data
until the Experiment is fulfilled.

An illustrative example:

![image](https://user-images.githubusercontent.com/47462814/231228581-d3a5f9c6-50e5-4b86-90f6-7176d9cd9f46.png)
![image](https://user-images.githubusercontent.com/47462814/231228869-786962a8-d47d-48a2-8683-c609c3ec77c0.png)
![image](https://user-images.githubusercontent.com/47462814/231228972-d323a20f-74f3-458a-a093-94684cdb161d.png)

### Reporter 🎤

Inputs: Results, info, plan, experiment, objective

Outputs: Report 

The info they request should be:
-   Anything related to the project

The reporters job is to compile the results from the Analyst into a
human-readable report. This is where a [multi-modal LM](https://ai.googleblog.com/2023/03/palm-e-embodied-multimodal-language.html) can shine
or an open-source [alternative](https://blog.salesforceairesearch.com/blip-2/). The goal
is to create a report with a variety of multi-media information that
pertains to the original objective. Showing how the objective has been
answered experimentally and what those results indicate the answer to
the objective is.

### Judge 🧑‍⚖️

Input: Objective, Results

Output: Judgment

The Judge’s job is to evaluate the report and determine if the research
satisfied the objective, if not then it will be fed back into the cycle.
If it does the report and the judgment will be sent to the User.
