# Agent Knowledge Base: Agentic Software Dev# Agent Knowledge Base: Agentic Software Development Workflow (ASDW)

This document is the single source of truth for AI agents developing the ASDW project itself.

## 1. Project Overview

* **Objective:** To create a versionable, reusable system where an AI agent can perform software development tasks, directed by a human via a Linear interface.

* **Tech Stack:** Bash (for the orchestrator), Markdown (for prompts and rules), `gemini-cli`, `linear-mcp`.

## 2. Architecture

* **Directory Structure:**

  * `prompts/`: Contains markdown files that define the agent's core capabilities (e.g., generating PRDs, generating code).

  * `rules/`: Contains reusable knowledge snippets and coding patterns for different languages/frameworks (e.g., `testing-pytest.md`).
  
  * `bundles/`: Contains reusable collections of rules and prompts in markdown files. Typically these files contain `@import...` statements to refer to other files in the repo.

* **Core Architectural Pattern:** The system uses a **Command-Streaming Agent** architecture. A lightweight `agent.sh` orchestrator script runs a loop, calling the `prompts/orchestrator.md` policy prompt to get the single next command to execute. This makes the system stateless at each step and highly resilient.

## 3. Coding Patterns & Conventions

* **Language & Version:** POSIX-compliant `bash` for all scripts to ensure maximum portability.

* **Code Style & Formatting:**

  * **Bash:** Use ShellCheck to lint scripts. Adhere to the Google Shell Style Guide. Use 2 spaces for indentation.

  * **Markdown:** Use Prettier to format markdown files for consistency.

* **Naming Conventions:**

  * Prompt files are numbered for sequence: `00_...`, `01_...`.

  * Rule files are structured by category: `language/pattern.md`.

  * Shell variables are `UPPER_CASE`. Functions are `lower_case_with_underscores`.

* **Key Abstractions:**

  * **Policy Prompt (`orchestrator.md`):** The central "brain" of the agent. All high-level logic and decision-making should be defined here, not hard-coded in the shell script.

  * **Rule Files:** All specific coding knowledge (e.g., how to write a Vitest test) must be in a `rules/` file to be composable.

## 4. Testing

* **Testing Philosophy:** "Prompt-First Testing." The primary method of testing is manually running a prompt with a specific context and verifying its output is correct and useful.

* **Test Runner:** Manual execution via `gemini-cli`.

* **Future Goal:** Develop a test harness script that can run a suite of test cases against the prompts to check for regressions.

## 5. Build & Deployment

* **Build Command:** There is no "build" command. The project is used directly from the source.

* **Deployment:** The workflow is "deployed" to another project by cloning this repository into its `.agent_workflow_repo/` directory.to another project by cloning this repository into its .agent_workflow_repo/ directory.