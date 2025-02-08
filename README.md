# Groclake Multi-Agent Integration Framework

The Groclake Multi-Agent Integration Framework is a modular system for integrating various external services—such as GitHub, Gmail, Photos, and more—using a unified agent architecture. It leverages Groclake tools alongside the Groq API to convert natural language commands into structured JSON instructions, which are then executed by the appropriate service-specific agent.

## Overview

This project implements a unified agent architecture where each agent extends a common base (`GrocAgent`). The primary goal is to allow users to interact with multiple services through simple natural language commands. For example, the GitHub agent can create repositories, star/unstar repositories, list repositories, and more. Similar patterns apply to agents for Gmail, Photos, and other services.

## Key Features

- **Unified Agent Architecture:** A standardized interface for handling operations across multiple services.
- **Natural Language Parsing:** Uses the Groq API to translate commands (e.g., "Create private repo test with README") into JSON instructions.
- **Extensibility:** Easily add new agents (Gmail, Photos, etc.) by following the established pattern.
- **RESTful API:** A Flask-based endpoint (`/agent`) receives commands in JSON format and processes them accordingly.

## Architecture

### Groclake Tools Integration

- **Base Agent (`GrocAgent`):** Provides core functionalities such as initialization, command parsing, and error handling.
- **Groq API:** The `call_groq_chat` function sends a prompt with the available operations to the Groq API in streaming mode, accumulates the response, and returns a JSON object with the parsed command.

### Service-Specific Agents

- **GitHub Agent:**
  - **Operations:** Create repository, star/unstar repository, list repositories, delete repository, get repository details, and fork repository.
  - **Implementation:** Uses GitHub API endpoints with proper authentication via a `GITHUB_TOKEN`.

- **Additional Agents:**
  - **Gmail Agent:** Would handle email operations such as sending and receiving messages.
  - **Photos Agent:** Would manage photo uploads, album organization, and related tasks.
  - **Future Integrations:** New agents can be added using the same design principles.

## Installation

### Prerequisites

- **Python 3.7+**
- Required libraries:
  - Flask
  - requests
  - groq (for interacting with the Groq API)
  - groclake (provides the base agent class and utilities)

### Setup

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/vansh-potpose/ai-agents.git
   cd groclake-agents
