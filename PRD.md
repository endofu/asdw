
# **PRD: Agentic Software Development Workflow System**

Version: 1.0  
Status: In Progress

## **1\. Overview**

This document outlines the requirements for building an **Agentic Software Development Lifecycle (ASDL)** system. The goal is to create a semi-autonomous system where an AI agent, directed by a human developer via a Linear interface, can perform end-to-end software development tasks.  
The system will be built as a versionable, reusable workflow repository that can be integrated into various software projects. It will use a "Command-Streaming Agent" architecture, where the agent makes one decision at a time, allowing for robust error handling, self-correction, and human-in-the-loop collaboration.

## **2\. Core Features & Requirements**

| Feature ID | Feature Name | Description | Status |
| :---- | :---- | :---- | :---- |
| F-01 | **Versionable Workflow Repository** | The core logic (prompts, rules) will live in a standalone Git repository that can be cloned into any project. | **Defined** |
| F-02 | **Command-Streaming Agent** | The agent orchestrator will not be a static script. It will be a loop that calls an LLM "policy" prompt to get the single next command, executes it, and re-evaluates. | **Defined** |
| F-03 | **Git-Native Workspace** | Each task will be managed in its own Git worktree. All artifacts, including PRDs and logs, will be versioned on the feature branch. | **Defined** |
| F-04 | **Linear-Driven UI** | The primary human-agent interface will be Linear. The agent will read statuses, post comments for updates/questions, and pause its execution based on the issue's status. | **Defined** |
| F-05 | **Composable Knowledge (@import)** | The system will support importing rule sets into a project's WORKFLOW.md, allowing for flexible and reusable knowledge composition. | **Defined** |
| F-06 | **Resilient Error Handling** | The agent must attempt to self-correct upon command failure and will only enter a "Blocked" state after multiple distinct failed attempts. | **Defined** |
| F-07 | **Interactive Task Selection** | The agent will be able to list actionable issues from Linear and prompt the user to select which one to begin working on. | **Defined** |
| F-08 | **Explicit Cleanup & Reset** | Worktree cleanup will be triggered by a dedicated 'Cleanup' status in Linear. A manual reset mechanism will be available to abandon a faulty worktree. | **Defined** |

## **3\. User Stories**

| Story ID | User Story |
| :---- | :---- |
| US-01 | As a developer, I want to initialize a new project with the ASDL so that I can start using agents for development tasks. |
| US-02 | As a developer, I want the agent to fetch a ticket from Linear, create a worktree, and generate a PRD for my review. |
| US-03 | As a developer, I want to approve a PRD by changing its status in Linear, triggering the agent to start coding. |
| US-04 | As an agent, I want to follow a TDD cycle by generating a failing test, then generating code to pass it, based on the project's testing rules. |
| US-05 | As an agent, I want to detect when I'm stuck and notify the developer by updating the Linear ticket to "Agent Blocked". |
| US-06 | As a developer, I want to review a Pull Request created by the agent for a completed feature. |
| US-07 | As a developer, I want to trigger the cleanup of a feature's worktree by moving the corresponding Linear ticket to the "Cleanup" status. |

## **4\. Task Breakdown**

This plan will be executed by completing the following tasks.

| Task ID | Task Description | Status |
| :---- | :---- | :---- |
| T-01 | **Finalize Workflow Repository Structure:** Create all prompt and rule files as defined. | **Done** |
| T-02 | **Create prompts/02\_generate\_test.md:** Write the prompt for generating a failing test based on a PRD. | **To Do** |
| T-03 | **Create prompts/03\_generate\_code.md:** Write the prompt for generating code that satisfies a failing test. | **To Do** |
| T-04 | **Create prompts/04\_document\_changes.md:** Write the prompt for documenting new functions and files. | **To Do** |
| T-05 | **Develop Agent Orchestrator (agent.sh):** Build the command-streaming loop script that orchestrates the entire workflow. | **To Do** |
| T-06 | **Implement @import Pre-processor:** Create a utility to resolve @import statements in WORKFLOW.md files. | **To Do** |
| T-07 | **Write Documentation:** Thoroughly document the setup, usage, and extension of the workflow system. | **To Do** |
