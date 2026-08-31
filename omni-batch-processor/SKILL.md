---
name: omni-batch-processor
description: |
  Automates the massive batch processing of topics to generate a comprehensive Book (as a PDF) 
  and a complete Software Architecture Design (PRD, TRD, System Flow).
license: Apache-2.0
metadata:
  version: v1
  publisher: local
---

# Omni Batch Processor Skill

When the user asks you to "run omni batch processor" or "batch process these topics", you must execute the following TWO workflows for EACH topic provided by the user.

## Workflow 1: The Book Generator
For a given `{topic}`, you must internally generate a massive, comprehensive book using the following prompt template:

> Write a complete comprehensive book of {topic} as complete comprehensive skill course to build it and most importantly eficiently using of it so reader will be mastermind of this skill with toc step by step process with practical instructions and explain in easy way how everything works part by part and most importantly teach/explain each chapter pages topics subtopics in deeeply detailed with easy to understand explanation with real life example too start from begining of it like story how it started and curent progress also predictable future add ciatations and references too. author shivam kumar in last of the book request to review this book read my other books and review them too also use my github asssests and for tech and ai consultancy or my asssests licence contact me github https://github.com/shivay00001 contact shivaysinghrajput@proton.me use diagram too for explaining and give me output as pdf.

**Execution Steps for Workflow 1:**
1. Generate the content as pure Markdown (including `mermaid` code blocks for diagrams).
2. Save this Markdown to a temporary file using the `write_to_file` tool (e.g., `Outputs/{topic}/Book.md`).
3. Ensure dependencies are installed by running `python -m pip install -r C:\Users\shiva\.gemini\config\plugins\omni-batch-processor\requirements.txt` and `playwright install chromium` if necessary.
4. Run the following command using the `run_command` tool to convert the markdown to a PDF:
   ```powershell
   python C:\Users\shiva\.gemini\config\plugins\omni-batch-processor\scripts\pdf_generator.py "Outputs\{topic}\Book.md" "Outputs\{topic}\Book.pdf"
   ```

## Workflow 2: Software Architecture Design
For the same `{topic}`, you must internally design the software architecture using the following prompt template:

> Design a app framework system architecture design ui flow prd trd and all system components fast working optimization and many More Fundamental foundation to completion in {topic} more features and design the system with smartness by understanding needs of these types of apps or softwares what system should exist mind about all security and safety features too all things allowed on what level or limit allowed by manys don't overcode or don't make a silly mistakes too use best architectural framework on all parameters.

**Execution Steps for Workflow 2:**
1. Generate the PRD, TRD, UI Flow, and System Architecture.
2. Use the `write_to_file` tool to save these components into structured Markdown files within `Outputs/{topic}/Software_Design/` (e.g., `PRD.md`, `Architecture.md`).

## Constraints
- Do NOT ask the user for permission between topics; process them all in a loop if possible.
- Ensure all diagrams use Mermaid syntax.
- Ensure the author signature and github links exactly match the prompt in Workflow 1.
