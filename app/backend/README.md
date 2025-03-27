## Backend Documentation

The `app/backend/` directory contains the backend implementation of the RAG (Retrieval Augmented Generation) chat app. It is built using the [Quart](https://quart.palletsprojects.com/) framework for asynchronous web applications and integrates with Azure services for AI and data processing.

### Directory Structure

- **`app.py`**: The main application file that initializes the Quart app and sets up routes, middleware, and configurations.
- **`config.py`**: Contains configuration settings for the backend, including environment variables and default values.
- **`custom_uvicorn_worker.py`**: Custom Uvicorn worker for running the backend server.
- **`decorators.py`**: Contains reusable decorators for route handling and middleware.
- **`Dockerfile`**: Dockerfile for containerizing the backend application.
- **`error.py`**: Defines custom error handling logic for the backend.
- **`gunicorn.conf.py`**: Configuration file for the Gunicorn server.
- **`load_azd_env.py`**: Loads Azure Developer CLI environment variables into the application.
- **`main.py`**: Entry point for running the backend application.
- **`prepdocs.py`**: Script for preprocessing documents for ingestion into Azure AI Search.
- **`requirements.in`**: Input file for generating `requirements.txt` using `pip-tools`.
- **`requirements.txt`**: Lists all the Python dependencies required for the backend.
- **`approaches/`**: Contains classes implementing different RAG approaches for the Chat and Ask tabs.
  - **`approach.py`**: Base class for RAG approaches.
  - **`chatapproach.py`**: Implements the chat-based RAG approach.
  - **`chatreadretrieveread.py`**: Implements the "Chat-Read-Retrieve-Read" approach.
- **`chat_history/`**: Contains utilities for managing chat history.
- **`core/`**: Core utilities and helpers for the backend.
- **`prepdocslib/`**: Library for preprocessing documents.

### Features

1. **Integration with Azure Services**:
   - Uses Azure AI Search for document indexing and retrieval.
   - Supports Azure OpenAI for GPT-based chat functionality.
   - Includes optional features like speech input/output and vision-based document analysis.

2. **Customizable RAG Approaches**:
   - The `approaches/` folder allows for easy customization of retrieval and generation strategies.

3. **Error Handling**:
   - Centralized error handling is implemented in `error.py` for consistent responses.

4. **Preprocessing Tools**:
   - The `prepdocs.py` script and `prepdocslib/` library provide tools for preparing documents for ingestion.

5. **Containerization**:
   - The `Dockerfile` enables easy deployment of the backend as a containerized application.

### Docs: Backend Requirements

The backend dependencies are listed in the `requirements.txt` file. Below is a summary of the key dependencies:

- **Azure SDKs**:
  - `azure-core`, `azure-identity`, `azure-search-documents`, `azure-storage-blob`, `azure-monitor-opentelemetry`, etc.

- **Quart Framework**:
  - `quart`, `quart-cors` for building asynchronous web applications.

- **OpenTelemetry**:
  - `opentelemetry-api`, `opentelemetry-sdk`, `opentelemetry-instrumentation` for monitoring and tracing.

- **AI Libraries**:
  - `openai` for GPT-based chat functionality.
  - `pydantic` for data validation and serialization.

- **Utilities**:
  - `requests`, `httpx` for HTTP requests.
  - `tenacity` for retry logic.
  - `python-dotenv` for environment variable management.

To install the backend requirements, run:

```bash
pip install -r 