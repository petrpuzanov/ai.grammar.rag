## RAG System Demo (Japanese Grammar QA)

This is a demo RAG system designed as a question-answering assistant for Japanese grammar. Instead of relying only on the LLM’s internal knowledge, it uses a structured dataset of grammar rules to provide accurate and grounded answers.

#### Architecture

The system is built using the following components:

1. **Application layer** – Spring Boot with Spring AI for orchestration and integration.
2. **Local model deployment** – Ollama for running both chat and embedding models locally.
3. **Vector database** – PostgreSQL with pgvector for storing embeddings and performing similarity search.

All components are free and open-source.

#### How It Works

1. Japanese grammar rules are stored in a CSV dataset (each row = one rule).
2. Each rule is converted into an embedding and stored in the vector database.
3. When a user asks a question:

    * The query is embedded
    * The system retrieves the most relevant grammar rules
    * The LLM generates an answer based only on this retrieved context

#### Running the System

##### Prerequisites

* Docker (make sure you are logged into Docker Hub)

##### Running

Download the `docker-compose.yml` file and run:

```bash
docker-compose up
```

This will start:

* the Spring Boot application
* the local LLM via Ollama
* PostgreSQL with pgvector enabled

Once running, you can send questions like:

* “What is the difference between は and が?”
* “How does the て-form work?”

and receive context-aware answers based on the dataset.
