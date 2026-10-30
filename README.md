# Intelligent University Assistant — LangGraph

## 1. Project Overview

This project implements an Intelligent University Assistant using Python, LangGraph, LangChain, and a local Large Language Model (LLM) through Ollama.

The assistant classifies user questions and routes them to specialized agents. It can answer university-related questions, assist with programming, perform mathematical calculations, provide administrative guidance, and handle general questions.

## 2. Technologies Used

- Python 3.11
- LangGraph
- LangChain
- Ollama
- Qwen 2.5 (0.5B)
- Jupyter Notebook / Visual Studio Code

## 3. System Architecture

The assistant follows a graph-based workflow:

1. The user submits a question.
2. The classifier identifies the question category.
3. LangGraph routes the question to the appropriate specialized agent.
4. The agent generates a response or requests an available tool.
5. When a tool is called, its result is returned to the agent.
6. The assistant produces the final answer.

The system includes five specialized agents:

| Agent | Responsibility |
|---|---|
| COURSES | University courses and academic guidance |
| PROGRAMMING | Python programming and algorithms |
| MATHEMATICS | Mathematical questions and calculator integration |
| ADMINISTRATION | Enrollment, certificates, and university procedures |
| GENERAL | General questions, conversation, and date/time |

## 4. Tools

The project integrates two tools:

- **Calculator:** Performs mathematical calculations.
- **Current Date/Time:** Retrieves the current date and time.

## 5. Conversation Memory

LangGraph uses `MemorySaver` to maintain conversation history.

A `thread_id` identifies each conversation, allowing the assistant to access previous messages within the same thread.

## 6. Error Handling

The system includes error handling for:

- Empty user questions.
- Classification errors.
- Unexpected categories.
- Technical errors during agent execution.

## 7. Installation and Setup

Install Python and Ollama.

Download the local language model:

```bash
ollama pull qwen2.5:0.5b
```

Install the required Python packages:

```bash
pip install langgraph langchain langchain-core langchain-ollama requests ipykernel
```

Make sure the Ollama service is running before executing the notebook.

## 8. How to Run

1. Open `langgraph_lab_Arzam.ipynb` in VS Code.
2. Select the Python environment.
3. Start Ollama.
4. Execute the notebook cells sequentially.
5. Run the demonstration queries.
6. Inspect the LangGraph execution traces.

## 9. Testing

The assistant was tested with different types of questions:

- **Courses:** What topics are covered in a machine learning course?
- **Programming:** Write a Python factorial function.
- **Mathematics:** Compute (15 + 27) * 3.
- **Administration:** How do I request an enrollment certificate?
- **General:** What is today's date?
- **Error handling:** Submit an empty question.

A conversation memory test was also performed by providing a name and asking the assistant to recall it.

The calculator integration was verified using the mathematical expression `(15 + 27) * 3`, which returned `126`.

## 10. Design Choices

LangGraph was selected to implement conditional routing between specialized agents and tools.

Specialized agents were used to separate responsibilities and provide category-specific instructions.

Ollama enables local LLM execution without requiring a cloud-based API.

The calculator tool improves arithmetic reliability, while `MemorySaver` supports multi-turn conversations.

## 11. Limitations

- Small local language models may produce inconsistent answers.
- Question classification may occasionally be inaccurate.
- University-specific information is not available unless explicitly provided.
- Conversation memory depends on the configured checkpoint and thread identifier.
- Tool usage requires correct routing and execution.

## 12. Conclusion

This project demonstrates how LangGraph can coordinate specialized AI agents, external tools, conditional routing, error handling, and conversation memory to build an Intelligent University Assistant.