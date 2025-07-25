# AI-Assisted Development Workflow

This repository contains the core prompts, rules, and logic for an AI-assisted software development lifecycle. It is designed to be cloned into a project and used by an agent orchestrator to automate development tasks.

## Quick Start

1.  **Clone this repository into your project:**

    ```bash
    git clone [https://github.com/endofu/asdw.git](https://github.com/endofu/asdw.git) .agent_workflow_repo
    ```

    _Note: It's recommended to add `.agent_workflow_repo/` to your project's `.gitignore` file if it is placed inside the code repository._

2.  **Create your project's `WORKFLOW.md`:**
    Create a `WORKFLOW.md` file in the root of your project to define which rules and tools your project uses. Use the `@import()` directive to include rules from this repository.

    _Example `WORKFLOW.md`:_

    ```markdown
    # Project Workflow: My Awesome App

    @import(javascript/bundle-react-ts-effect.md)
    @import(javascript/testing-vitest.md)

    ## Project-Specific Tools

    - bun: 1.0
    - context7
    - effect-mcp
    - linear-mcp
    ```

3.  **Run the Agent:**
    Start your agent orchestrator, which will use the prompts in this repository to begin processing tasks from Linear.

## How It Works

This system is based on a "Command-Streaming Agent" that uses the `prompts/orchestrator.md` prompt as its core policy function. It polls Linear for actionable tickets, makes decisions one command at a time, and uses the project's `WORKFLOW.md` and `AGENTS.md` for context. The entire lifecycle is managed through Linear issue statuses.
