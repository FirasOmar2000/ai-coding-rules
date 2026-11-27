# AI Coding Rules

**Clear, practical instructions that help AI coding assistants write better code.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Contributions welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg)](#contributing)

---

## Introduction

AI coding assistants can write code quickly, but without clear direction they often produce code that works today and causes problems tomorrow: duplicated logic, ignored project conventions, missing error handling, unrelated changes, and security gaps.

This repository is a growing collection of numbered rules that you can give to an AI coding assistant before it writes code. Each rule is short, direct, and ready to copy. The rules work with Claude, ChatGPT, Cursor, GitHub Copilot, and any other AI tool that accepts written instructions.

## Purpose

An AI assistant can only follow standards it knows about. These rules make your expectations explicit, so the assistant is more likely to:

- Write code that is clean, readable, and easy to maintain
- Reuse existing code instead of duplicating it
- Respect your project's structure and coding style
- Handle errors, edge cases, and security from the start
- Change only what you asked it to change
- Explain what it did, so you can review it with confidence

Better instructions lead to better code, and better code leads to a better final product.

## Who Is This For?

- **Developers** who use AI assistants in their daily work and want more consistent results
- **Vibe coders** who build applications mostly by describing what they want to an AI
- **Teams** that want everyone's AI-generated code to follow the same standards
- **Beginners** who want to learn what good, maintainable code looks like

## How to Use

1. **Copy the rules.** Open [CODING-RULES.md](CODING-RULES.md) and copy the [Copy-Ready Version](CODING-RULES.md#copy-ready-version), or pick only the rules you need.
2. **Add them where your assistant reads instructions.**

   | Tool                   | Where to add the rules                                                       |
   | ---------------------- | ---------------------------------------------------------------------------- |
   | Claude Code            | `CLAUDE.md` in your project root                                             |
   | Cursor                 | A project rule in `.cursor/rules/`                                           |
   | GitHub Copilot         | `.github/copilot-instructions.md`                                            |
   | Codex and other agents | `AGENTS.md` in your project root                                             |
   | Claude, ChatGPT (chat) | Project instructions, custom instructions, or the start of your conversation |
   | Other tools            | The tool's system prompt or custom instructions setting                      |

3. **Refer to rules by number.** Because rule numbers never change, you can remind your assistant during a task, for example: "Follow rule 13 and don't modify unrelated code."

> **Tip:** Adapt the rules to your project. Remove what doesn't apply, and add project-specific details such as your framework, language, or folder layout.

## Coding Rules

A summary of all rules is below. See [CODING-RULES.md](CODING-RULES.md) for the full collection, including why each rule matters.

1. **Write Clean and Readable Code**
   Write code that is easy to read, understand, and maintain. Avoid unnecessary complexity.

2. **Add Clear Code Comments**
   Add comments that explain what important lines and blocks of code do. Comments should help developers understand the purpose of the code.

3. **Use Meaningful Names**
   Give variables, functions, and components clear names that describe their purpose.

4. **Avoid Duplicate and Unnecessary Code**
   Don't repeat the same logic in different places. Reuse existing code whenever possible.

5. **Keep Functions Small**
   Each function should have one clear job. Avoid putting multiple unrelated tasks inside one function.

6. **Use Reusable Components and Functions**
   Create components and functions that can be reused in different parts of the application instead of writing the same code again.

7. **Follow the Existing Project Structure**
   Respect the current folder structure, file organization, and coding style. Don't introduce a new structure without a good reason.

8. **Don't Recreate Existing Components**
   Before creating a new component or feature, check whether something similar already exists. Reuse or improve existing components when possible.

9. **Handle Errors and Application States Properly**
   Handle loading states, empty states, errors, and success messages. Always provide useful feedback to users.

10. **Follow Security Best Practices**
    Protect sensitive information, validate user input, secure API endpoints, and check user permissions.

11. **Follow Performance Best Practices**
    Avoid unnecessary API requests, optimize database queries, and prevent unnecessary rendering or processing.

12. **Make All UI Designs Responsive**
    Ensure the application works properly on mobile, tablet, and desktop screens.

13. **Don't Modify Unrelated Code**
    Only change files and functionality related to the requested task. Don't break or modify existing features unnecessarily.

14. **Inspect Before Making Changes**
    Before implementing anything, examine the existing code and understand how the relevant parts of the application work.

15. **Explain Important Changes**
    After implementation, summarize which files were changed, what was added or modified, and why.

16. **Suggest a Meaningful Commit Message**
    After completing a task, suggest a clear commit message that describes what changed and why.

17. **Plan Before Building**
    Before starting a new project or a major feature, make sure the planning documents exist: requirements, app flow, design brief, database schema, and implementation plan. Draft any that are missing and get approval before writing code.

18. **Prevent Race Conditions**
    When two requests can change the same data at the same time, never check a value and update it in separate steps. Let the database do both in one atomic step, or use a transaction that locks the row.

## General Instructions

These apply to every task, alongside the numbered rules.

- **Don't install unnecessary packages.** Use existing libraries whenever possible.
- **Test your changes.** Fix any errors or warnings before finishing.
- **Aim for quality, not just working code.** Don't just make the code work. Make it clean, secure, organized, easy to understand, and easy to maintain.

## Project Structure

```text
.
├── README.md         # Project introduction and rule summary
├── CODING-RULES.md   # Complete rule collection and copy-ready version
└── LICENSE           # MIT License
```

## Contributing

Contributions are welcome. You can help by suggesting new rules or improving existing ones.

**To suggest a new rule or an improvement:**

1. Open an issue that describes the rule: a proposed title, the instruction, and the problem it solves.
2. Check the existing rules first to avoid duplicates or overlap.

**To submit a pull request:**

1. Follow the steps in [Adding a New Rule](CODING-RULES.md#adding-a-new-rule).
2. Give a new rule the next available number. Never renumber existing rules.
3. Keep the same writing style: a short title, a direct instruction, and a brief explanation.
4. Update both `CODING-RULES.md` and `README.md` so they stay consistent.

**A good rule is:**

- Practical and useful in real-world development
- Written as a clear instruction an AI assistant can follow
- Independent of any single AI tool
- Distinct from the existing rules

## Future Improvements

This collection will keep growing as new practices are discovered and tested. New rules are always added with the next available number, and existing numbers never change, so any reference to a rule stays valid over time.

## License

This project is licensed under the [MIT License](LICENSE).

The MIT License was chosen because it is short, widely recognized, and permissive. Anyone can copy, adapt, and use these rules in personal or commercial projects, which suits a collection meant to be pasted into prompts and project instruction files.
