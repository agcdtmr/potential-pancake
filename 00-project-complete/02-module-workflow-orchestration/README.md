# Module 02: Workflow Orchestration

This is the repository on how to use the Mage platform to author and share magical data pipelines.

We will:

- Run Mage and Postgres in a docker environment.
- Take the NY taxi data set, transform it and load it to both Postgres and GCS
- Perform additional transformations using pandas, apache arrow, and sql and then load to BigQuery
- Extract, transform, and load data to multiple sources.

## To Do's

- [ ] 2.2.1 - 📯 Intro to Orchestration
- [ ] 2.2.2 - 🧙‍♂️ Intro to Mage
- [ ] 2.2.3 - 🐘 ETL: API to Postgres
- [ ] 2.2.4 - 🤓 ETL: API to GCS
- [ ] 2.2.5 - 🔍 ETL: GCS to BigQuery
- [ ] 2.2.6 - 👨‍💻 Parameterized Execution
- [ ] 2.2.7 - 🤖 Deployment (Optional)
- [ ] 2.2.8 - 🗒️ Homework
- [ ] 2.2.9 - 👣 Next Steps

### 2.2.1 - 📯 Intro to Orchestration

What is [Orchestration](https://www.youtube.com/watch?v=Li8-MWHhTbo&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb&index=17)?

- A large part of data engineering is extracting, transforming, and loading data between sources.
- Orchestration is a process of dependency management, facilitated through automation.
- The data orchestrator manages scheduling, triggering, monitoring, and even resource allocation.
  ☝️ Every workflow requires sequential steps.
  ☕️ A French press with cold water will only brew disappointment
  ☔️ Poorly sequenced transformations brew a storm far more bitter.
  📕 Steps 🟰 tasks
  🔄 Workflows 🟰 DAGs (directed acyclic graphs)

I think orchestration doesn't click for new folks because when you build test cases or hobby projects there's nothing that needs to happen "automatically". Like you often just build the pipeline then run it once, then smile at your results.

Orchestration helps you schedule and chain tasks together, and especially also allows your pipeline to respond to events automatically. Such as the delivery of new input files, or the detection of anomalous data features... Then it can trigger the running of various actions in a row to provide results.

Think creatively from there

“Data orchestration provides the answer to making your data more useful and available. But ultimately, it goes beyond simple data management. In the end, orchestration is about using data to drive actions, to create real business value.” – Steven Hillion, Head of Data at Astronomer

it is an automated process that takes data from multiple storage locations and allows you to author, schedule, and monitor data pipelines programmatically. Data orchestration platforms let you control data, monitor systems, and draw valuable business insights.

Data Engineering Lifecycle

![image](https://github.com/agcdtmr/potential-pancake/assets/112581827/d63eeec4-b666-445f-a47c-81f2d4f26078)


A good orchestrator handles…
Workflow management
Automation
Error handling
Recovery
Monitoring, alerting
Resource optimization
Observability
Debugging
Compliance/Auditing

The developer experience
Flow state 🌊
“I need to switch between 7 tools/services.”
Feedback Loops 🔁
“I spent 5 hours locally testing this DAG.”
Cognitive Load 🧱
How much do you need to know to do your job?

### 2.2.2a - 🧙‍♂️ Intro to Mage

What is [Mage.ai](https://www.youtube.com/watch?v=AicKRcK3pa4&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb&index=18)? An open-source pipeline tool for orchestrating, transforming, and integrating data

### 2.2.2b - 🧙‍♂️ [Configure Mage](https://www.youtube.com/watch?v=tNiV7Wp08XE)

Let's get started!

This contains a Docker Compose template for getting started with a new Mage project. It requires Docker to be installed locally. If Docker is not installed, please follow the instructions [here](https://docs.docker.com/get-docker/).

You can start by cloning the repo:

```bash
git clone https://github.com/mage-ai/mage-zoomcamp.git mage-zoomcamp
```

Navigate to the repo:

```bash
cd mage-data-engineering-zoomcamp
```

Rename `dev.env` to simply `.env`— this will _ensure_ the file is not committed to Git by accident, since it _will_ contain credentials in the future.

Now, let's build the container

```bash
docker compose build
```

Finally, start the Docker container:

```bash
docker compose up
```

Now, navigate to http://localhost:6789 in your browser! Voila! You're ready to get started with the course.

#### What just happened?

We just initialized a new mage repository. It will be present in your project under the name `magic-zoomcamp`. If you changed the variable `PROJECT_NAME` in the `.env` file, it will be named whatever you set it to.

This repository should have the following structure:

```
.workflow-orchestration-mage
├── mage_data
│   └── magic-zoomcamp
├── magic-zoomcamp
│   ├── __pycache__
│   ├── charts
│   ├── custom
│   ├── data_exporters
│   ├── data_loaders
│   ├── dbt
│   ├── extensions
│   ├── interactions
│   ├── pipelines
│   ├── scratchpads
│   ├── transformers
│   ├── utils
│   ├── __init__.py
│   ├── io_config.yaml
│   ├── metadata.yaml
│   └── requirements.txt
├── Dockerfile
├── README.md
├── dev.env
├── docker-compose.yml
└── requirements.txt
```

#### Assistance

1. [Mage Docs](https://docs.mage.ai/introduction/overview): a good place to understand Mage functionality or concepts.
2. [Mage Slack](https://www.mage.ai/chat): a good place to ask questions or get help from the Mage team.
3. [DTC Zoomcamp](https://github.com/DataTalksClub/data-engineering-zoomcamp/tree/main/week_2_workflow_orchestration): a good place to get help from the community on course-specific inquireies.
4. [Mage GitHub](https://github.com/mage-ai/mage-ai): a good place to open issues or feature requests.

### 2.2.2c - 🧙‍♂️ A Simple Pipeline

## Resources

- [Mage.ai](https://docs.mage.ai/introduction/overview)
- [What Is Data Orchestration](https://www.astronomer.io/blog/what-is-data-orchestration)
- [Taking Data Orchestration to the Next Level](https://www.astronomer.io/blog/apache-airflow-at-astronomer-data-orchestration/)
