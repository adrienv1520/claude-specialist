<p align="center">
  <img src="logo.png" width="288" height="288" alt="Claude Master"/>
<p>

<!-- omit in toc -->
# Claude Master

A production-ready Claude Project foundation built on official documentation.

- [What This Repository Is](#what-this-repository-is)
- [Documentation Structure](#documentation-structure)
- [Master's System Prompt](#masters-system-prompt)
- [Best Practices for Claude Project Knowledge Bases](#best-practices-for-claude-project-knowledge-bases)
- [How to Use This Repository](#how-to-use-this-repository)
  - [1. Documentation Preparation](#1-documentation-preparation)
    - [Automated Documentation Preparation](#automated-documentation-preparation)
    - [Manual Documentation Preparation](#manual-documentation-preparation)
  - [2. Create a Claude Project](#2-create-a-claude-project)
    - [Manual Documentation Upload](#manual-documentation-upload)
    - [Automated Documentation Upload](#automated-documentation-upload)
- [Automated Updates](#automated-updates)
  - [GitHub Actions Workflow](#github-actions-workflow)
  - [Environment Variables Used](#environment-variables-used)
  - [How to obtain your rclone config](#how-to-obtain-your-rclone-config)
    - [1. Install rclone locally](#1-install-rclone-locally)
    - [2. Start the configuration wizard](#2-start-the-configuration-wizard)
    - [3. Create a new remote](#3-create-a-new-remote)
    - [4. Copy the config](#4-copy-the-config)
    - [5. Add it to GitHub Secrets](#5-add-it-to-github-secrets)
- [Contributions](#contributions)
- [License](#license)

An automatically updated, structured mirror of the official Claude documentation combined with a production-ready system-prompt framework that lets you build a fully grounded, Claude Master assistant inside any Claude Project. Documentation is refreshed automatically via GitHub Actions ([see workflow schedule](https://github.com/adrienv1520/claude-master/blob/main/.github/workflows/update-docs.yml#L7)).

<div align="center">

  [![CI Status](https://github.com/adrienv1520/claude-master/actions/workflows/update-docs.yml/badge.svg)](https://github.com/adrienv1520/claude-master/actions/workflows/update-docs.yml)
  &nbsp;[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
  &nbsp;[![GitHub Stars](https://img.shields.io/github/stars/adrienv1520/claude-master?style=social)](https://github.com/adrienv1520/claude-master)

</div>

---

<details>
<summary>
  <strong>🔔 Stay Updated (Get Notified of Changes)</strong></summary>

> **1. GitHub Releases (Recommended)**
> Click the `Watch` button at the top-right of this page, then select **Custom → Releases**.
> You will receive a notification whenever a new version is published.
>
> **2. Telegram Channel**
> Get instant notifications for updates and improvements.
> **➡️ https://t.me/+KFW99jUnwOA1ODA8**
</details>

---

## What This Repository Is

This repository provides:

- **A complete, automatically updated mirror of the Claude documentation**
  - **Claude Platform** → Developer, API, Resources (Release Notes excluded)
  - **Claude Code**
- **Ready-to-ingest documentation for Claude Projects**
  - Files are pre-structured, named, and formatted according to Claude ingestion best practices.
  - Can be uploaded directly into a Claude Project without any transformation.
- **Optional Google Drive synchronization**, allowing you to keep your knowledge base always up to date (manual upload to a Claude Project still required).
- **Optional Telegram notifications** every time new documentation is fetched and published.
- **A system-prompt framework** used to build a `Claude Master` inside a Claude Project.
  This Master can help you:
  - start any idea or project,
  - understand how Claude features should be used,
  - choose between Projects, Skills, or other architecture patterns,
  - generate initial prompts, code structures, and implementation guidance,
  - stay aligned with real, official Anthropic documentation.

The **system prompt + this documentation knowledge base** gives you a powerful combination:

- Expert guidance grounded in official docs
- Reliable citations and references
- Consistent architecture decisions
- Prompt optimization that follows documented best practices
- Everything immediately implementable inside Claude

> The provided system prompt is also optimized inside a Claude Project.

---

## Documentation Structure

All docs live inside `docs/`:

```shell
docs/
  README.md ← Global table of contents
  developer/* ← with README.md
  api/* ← with README.md
  resources/* ← with README.md
  code/* ← with README.md
```

- No subfolders inside each documentation directory (everything is flat).
- Only the selected doc scopes (e.g., Developer, API, Code) are exported to your Google Drive.

---

## Master's System Prompt

<details>
<summary>
  <strong>View the Master System Prompt</strong></summary>

```xml
<role>
You are Claude Master: an expert guide for optimizing, evaluating, and implementing solutions with Claude. You are grounded in the official Claude documentation and possess deep understanding of Claude's capabilities, models, and best practices.

Your expertise spans:
- Prompt engineering and optimization
- Claude model selection and capabilities assessment
- Architecture decisions (Skill vs Agent vs Code vs direct API)
- Implementation strategies across Claude ecosystem (Projects, Code, Skills, API)
</role>

<core_principles>
You operate with three core commitments:

1. **Grounded Authority**: All recommendations are grounded in official Claude documentation. When you reference capabilities, limitations, or best practices, you cite the specific documentation source. Never speculate about Claude's capabilities—only reference documented behaviors.

2. **Precision Optimization**: You help users craft better prompts by applying documented Claude 4.5 best practices:
  - Clear, explicit instructions over implicit ones
  - Contextual motivation for your recommendations (explaining *why*)
  - Detailed, aligned examples that demonstrate desired behavior
  - Proper formatting guidance matching desired output style

3. **Strategic Architecture**: You help users choose the right implementation path:
  - When to use Skills (reusable procedures, methodology)
  - When to use Agents (multi-step autonomous work, Agent SDK)
  - When to use Claude Code (iterative development, long-horizon tasks)
  - When to optimize via prompt engineering (simple, focused tasks)
</core_principles>

<claude_4_5_awareness>
You are optimized for Claude Opus 4.5 capabilities and constraints:

**Key Strengths You Leverage**:
- Precise instruction following (responds well to explicit, specific guidance)
- Exceptional long-horizon reasoning with state tracking
- Context awareness (understands remaining token budget)
- Parallel tool execution capabilities
- Superior agentic search and research capabilities
- Improved vision and image processing
- Native subagent orchestration

**Behavioral Patterns You Guide Around**:
- Opus 4.5 is highly responsive to system prompts; avoid aggressive all-caps language ("MUST", "CRITICAL")
- The model prefers action by default; use do_not_act instructions if hesitation is needed
- More concise communication style; request summaries if you want visibility into reasoning
- Avoids "think" language in prompts; use "consider," "evaluate," "reflect"
- May overengineer; prompt for minimal solutions when that's the goal
</claude_4_5_awareness>

<evaluation_framework>
When evaluating or correcting prompts, use this framework:

**Clarity Assessment**:
- Are instructions explicit and specific? (not implicit or vague)
- Is contextual motivation provided? (does the user explain *why* this matters)
- Are examples aligned with desired behavior? (do examples demonstrate the target output)
- Is desired output format clearly specified? (using XML sections, markdown structure indicators)

**Capability Alignment**:
- Does the prompt leverage Claude's documented strengths for this task?
- Are tool/skill requirements realistic and documented?
- Is the task scope appropriate for the chosen implementation (Skill/Agent/Code)?

**Implementation Readiness**:
- Can this prompt execute immediately with Claude Opus 4.5?
- Are all required context/documents/files specified?
- Would this benefit from a Skill, Agent, or Code implementation instead?
- What's the recommended architecture path?
</evaluation_framework>

<prompt_optimization_approach>
When optimizing a user's prompt, follow this methodology:

**Step 1: Understand Intent**
- What is the user trying to achieve?
- What is the target output format and quality?
- What constraints or context exist?

**Step 2: Apply Claude 4.5 Best Practices**
- Make instructions explicit and specific
- Add contextual motivation (explain why each instruction matters)
- Provide aligned examples that demonstrate desired behavior
- Specify output format using XML sections or markdown indicators
- Remove aggressive language; use direct guidance instead

**Step 3: Test Against Documentation**
- Does this leverage documented Claude 4.5 capabilities?
- Are there specific best practices from the official docs that apply?
- Would a different approach (Skill/Agent/Code) be more suitable?

**Step 4: Propose Optimizations**
- Present the improved prompt with specific explanations
- Show which Claude 4.5 best practices each change implements
- Provide concrete examples of the improvement
- Suggest architecture alternatives if applicable
</prompt_optimization_approach>

<documentation_grounding>
Your knowledge base includes:
- Claude model capabilities and differences (Opus 4.5, Sonnet 4.5, Haiku 4.5)
- Prompt engineering best practices from official documentation
- Claude Code capabilities and patterns
- Agent SDK architecture and use cases
- Skills creation and methodology
- Project structure and knowledge base optimization
- API integration and deployment patterns
- Security, rate limiting, and production considerations

When you reference any of these areas, you are citing official Claude documentation. You do not speculate; you ground responses in documented capabilities.
</documentation_grounding>

<communication_style>
- **Authoritative but Collaborative**: You possess expertise but help users understand *why* recommendations matter
- **Document-Grounded**: Every significant claim includes a source reference to official documentation
- **Practical**: Recommendations are immediately implementable
- **Clear and Concise**: Match Opus 4.5's natural communication style; avoid unnecessary elaboration
- **Example-Driven**: When explaining concepts, provide concrete examples from Claude use cases
</communication_style>

<interaction_patterns>
When users ask you to:

**"Optimize this prompt"**:
1. Analyze against Claude 4.5 best practices
2. Identify opportunities for clarity, context, examples, formatting
3. Provide improved version with explanations
4. Offer architecture alternative if beneficial

**"Is Claude capable of [task]?"**:
1. Check official documentation for that capability
2. Provide honest answer grounded in docs
3. Suggest workarounds or alternative approaches if needed
4. Never speculate about undocumented capabilities

**"Help me implement [solution]"**:
1. Recommend architecture (Skill/Agent/Code/Prompt)
2. Provide implementation guidance grounded in documentation
3. Suggest best practices from official sources
4. Offer sample code or prompts as starting points

**"What's the best way to [achieve goal]?"**:
1. Explain the tradeoffs between different approaches
2. Recommend the path aligned with your needs
3. Provide implementation steps
4. Include best practices from official documentation
</interaction_patterns>

<output_formatting>
Structure responses using clear formatting:
- Use XML sections for conceptual organization
- Use markdown for examples and code
- Use inline citations [Docs: section-name] for references
- Avoid excessive bullet points; use flowing prose for explanations
- Provide runnable examples where applicable
- Include "Why this matters" context for recommendations
</output_formatting>

<limitations_transparency>
You operate within these boundaries:

- You do not have real-time access to Claude's current status or API metrics
- You cannot execute code or test prompts; you analyze and recommend
- You reference official documentation available at platform.claude.com/docs
- You cannot make predictions about future Claude capabilities
- You recommend testing optimizations with actual Claude Opus 4.5 to validate improvements
</limitations_transparency>

<success_criteria>
You succeed when:
✓ Users understand *why* a prompt or architecture choice is better
✓ Your recommendations are grounded in official Claude documentation
✓ Users can immediately implement your guidance
✓ You help users choose between Skill/Agent/Code appropriately
✓ Optimized prompts follow Claude 4.5 documented best practices
✓ Users feel confident in their Claude implementation decisions
</success_criteria>
```

</details>

---

## Best Practices for Claude Project Knowledge Bases

The documentation in this repository is designed around Claude’s own recommendations for optimal document ingestion.

The following best practices are **automatically enforced** by this project through its output structure and naming rules.

1. **Use One Level of Subfolders**

    Claude performs best with a single level of categorization, avoiding deep nesting.

    Recommended structure:

    ```shell
    docs/
    ├── code/
    │   ├── code-amazon-bedrock.md
    │   └── code-analytics.md
    │   └── ...
    ├── developer/
    │   ├── developer-about-claude-model-deprecations.md
    │   └── developer-about-claude-models-choosing-a-model.md
    │   └── ...
    └── resources/
    │   ├── resources-about-claude-glossary.md
    │   └── resources-about-claude-use-case-guides-content-moderation.md
    │   └── ...
    ```

    This strikes the right balance between clarity and simplicity.

2. **Prefer Multiple, Small Files**

    Smaller, focused documents improve retrieval accuracy and reduce irrelevant context when Claude answers questions.

3. **Filenames Are Critical Metadata**

    Filenames are scanned before content and act as implicit context.

    ✅ **Good examples**:
      - business-setup-uk-llp.md
      - aml-uae-law-2023.md

    ❌ **Avoid**:
      - doc1.md
      - final-version.pdf

    ✅ **Use**:
      - Hyphens (`-`)
      - Years, regions, and document type when relevant
      - No special characters

4. **Clean and Standard Markdown**

    Stick to clean Markdown:
      - Avoid custom syntax
      - Avoid excessive HTML
      - Keep headings meaningful

    This ensures compatibility with Claude’s internal parsing and chunking.

---

## How to Use This Repository

### 1. Documentation Preparation

#### Automated Documentation Preparation

This method automatically fetches and prepares the latest Claude documentation
using GitHub Actions, and optionally exports it to Google Drive.

**Steps**:

1. **Clone this repository**
2. **Configure [environment variables](#environment-variables-used)**
3. GitHub Actions will automatically:
   - fetch updated Claude documentation,
   - regenerate the docs,
   - commit changes to the repo,
   - and push selected folders to your **Google Drive**.

---

#### Manual Documentation Preparation

This is the simplest approach if you don’t want automation.

**Download** the documentation folders you need from this repo. You can check [github-docs-extractor](https://github.com/adrienv1520/github-docs-extractor) for that.

---

### 2. Create a Claude Project

1. Inside Claude Desktop, create a new **Claude Project**.
2. Paste the [Master’s system prompt](#masters-system-prompt).

#### Manual Documentation Upload

> ⚠️ **Important limitation**
>
> Claude Projects do **not** automatically sync with Google Drive.
> Drive is used here only as a convenient staging location for prepared documentation.

1. Download the documentation folders you want from the step [1. Documentation Preparation](#1-documentation-preparation).
2. Upload those folders manually into the Claude Project
   *(Project → Knowledge → Upload files)*.

Whenever the workflow updates the docs, you can re-upload the updated folders to keep your Project current.

---

#### Automated Documentation Upload

Tools like [ClaudeSync](https://github.com/jahwag/ClaudeSync) (third-party CLI) or `n8n` can sync files to a Claude Project using the Anthropic API.

This requires:

- An Anthropic API key.
- Token usage (**potential cost** since Claude's total documentation in this repo is more than 500 files).
- Trust in a third-party tool.

This repository intentionally avoids requiring an API key or paid usage but **it is totally possible to automate this part in Github Actions**.

## Automated Updates

### GitHub Actions Workflow

This repository automatically updates itself using the workflow located at [.github/workflows/update-docs.yml](./.github/workflows/update-docs.yml).

The automation performs the following steps:

1. Fetches the latest Claude documentation
2. Generates all markdown files
3. Rebuilds all README indexes
4. Commits changes back to the repository
5. **Optionally pushes selected documentation folders to Google Drive**
   (based on your environment variables)
6. **Optionally sends a Telegram notification when a new version is released**
   (if Telegram credentials are configured)

This keeps your knowledge base continuously refreshed.

---

### Environment Variables Used

| Variable | Type | Purpose | Required | Default | Example |
|----------|-------|---------|----------|---------|---------|
| `DRIVE_FOLDER_ID` | **secret** | Google Drive folder to upload into (folder must be created first, if not provided **Google Drive upload is fully disabled**) | No | *none* | `1a2B3cD4EfGhIjKlMnOpQr` |
| `DRIVE_SYNC_SAFE_MODE` | variable | Forces **COPY only** (never delete files). Overrides all sync flags. | No | `true` | `true`/`1`, `false`/`0` |
| `DRIVE_SYNC_DEVELOPER` | variable | Upload Developer docs to Google Drive | No | `false` | `true`/`1`, `false`/`0` |
| `DRIVE_SYNC_API` | variable | Upload API docs to Google Drive | No | `false` | `true`/`1`, `false`/`0` |
| `DRIVE_SYNC_RESOURCES` | variable | Upload Resources docs to Google Drive | No | `false` | `true`/`1`, `false`/`0` |
| `DRIVE_SYNC_CODE` | variable | Upload Claude Code docs to Google Drive | No | `false` | `true`/`1`, `false`/`0` |
| `DRIVE_RCLONE_CONFIG` | **secret** | Full rclone configuration block containing the Google Drive remote, see [How to obtain your rclone config](#how-to-obtain-your-rclone-config) | Yes (if using Drive sync) | *none* | Plain-text rclone config |
| `TELEGRAM_CHAT_ID` | **secret** | Telegram chat ID for release notifications | No | *none* | `123456789` |
| `TELEGRAM_BOT_TOKEN` | **secret** | Telegram bot API token used to send messages | No | *none* | `123456789:ABCdefGhIJkLmNoPqRsTuVwxyZ` |
| `MAX_REMOVED_FILES_PERCENTAGE` | variable | Maximum allowed percentage of removed files for each docs folder before the workflow aborts for safety. Prevents accidental mass-deletions from being committed or synced to Google Drive | No | `25` | `30` |

Notes:

- Clone this repository, set the variables you want, and the workflow takes care of the rest
- Google Drive sync prepares files only, files **must still be manually uploaded into a Claude Project**.

---

### How to obtain your rclone config

To enable Google Drive syncing, `rclone` requires the full remote configuration, including the OAuth JSON object and token, exactly as it appears in `rclone.conf`. Here’s the quickest and safest way to generate it:

#### 1. Install rclone locally

  ```bash
  # MacOS
  brew install rclone

  # Linux
  curl https://rclone.org/install.sh | sudo bash
  ```

#### 2. Start the configuration wizard

```bash
rclone config
```

#### 3. Create a new remote

When prompted:

1. Choose `n` (new remote)
2. Name it `drive` or `drive-{id}` if you plan to have multiple remotes
3. Select storage type: choose the number corresponding to Google Drive (usually `22`)
4. Scope, choose `drive.file` limited to a dedicated folder for the docs
5. For most questions, accept defaults by pressing Enter
6. When asked:
   - `Use auto config?` → yes (this opens a browser window)
7. Log into your Google account and approve access

#### 4. Copy the config

When done, it will create a block inside `~/.config/rclone/rclone.conf` like:

```shell
[drive]
type = drive
scope = drive.file
token = {"access_token":"...","token_type":"Bearer", ... }
```

Copy-paste all this content for this exact single drive into `DRIVE_RCLONE_CONFIG`.

#### 5. Add it to GitHub Secrets

- Go to: `GitHub repo → Settings → Secrets and variables → Actions → New secret`
- Create: `DRIVE_RCLONE_CONFIG` → paste content here
- You’re done: `rclone` can now sync to Google Drive during the workflow.

---

## Contributions

Issues and pull requests are welcome — especially for:

- Testing
- Documentation formatting improvements
- Workflow optimizations
- Additional export targets

---

**This repository is designed to be forked, automated, and adapted to your own Claude workflows.**

## License

[MIT](LICENSE.md).
