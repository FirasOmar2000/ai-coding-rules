# Coding Rules

This is the complete collection of coding rules for AI coding assistants. Each rule is written as a direct instruction you can give to an assistant, followed by a short explanation of why it matters.

Rules are numbered permanently. A rule's number never changes, so you can refer to it in prompts and discussions (for example, "Follow rule 13").

## Contents

- [Rules](#rules)
  1. [Write Clean and Readable Code](#1-write-clean-and-readable-code)
  2. [Add Clear Code Comments](#2-add-clear-code-comments)
  3. [Use Meaningful Names](#3-use-meaningful-names)
  4. [Avoid Duplicate and Unnecessary Code](#4-avoid-duplicate-and-unnecessary-code)
  5. [Keep Functions Small](#5-keep-functions-small)
  6. [Use Reusable Components and Functions](#6-use-reusable-components-and-functions)
  7. [Follow the Existing Project Structure](#7-follow-the-existing-project-structure)
  8. [Don't Recreate Existing Components](#8-dont-recreate-existing-components)
  9. [Handle Errors and Application States Properly](#9-handle-errors-and-application-states-properly)
  10. [Follow Security Best Practices](#10-follow-security-best-practices)
  11. [Follow Performance Best Practices](#11-follow-performance-best-practices)
  12. [Make All UI Designs Responsive](#12-make-all-ui-designs-responsive)
  13. [Don't Modify Unrelated Code](#13-dont-modify-unrelated-code)
  14. [Inspect Before Making Changes](#14-inspect-before-making-changes)
  15. [Explain Important Changes](#15-explain-important-changes)
  16. [Suggest a Meaningful Commit Message](#16-suggest-a-meaningful-commit-message)
  17. [Plan Before Building](#17-plan-before-building)
  18. [Prevent Race Conditions](#18-prevent-race-conditions)
- [General Instructions](#general-instructions)
- [Copy-Ready Version](#copy-ready-version)
- [Adding a New Rule](#adding-a-new-rule)

---

## Rules

### 1. Write Clean and Readable Code

Write code that is easy to read, understand, and maintain. Avoid unnecessary complexity.

**Why it matters:** AI assistants sometimes choose clever or overly abstract solutions. Readable code is easier to review, debug, and extend, both for you and for the assistant in later sessions.

### 2. Add Clear Code Comments

Add comments that explain what important lines and blocks of code do. Comments should help developers understand the purpose of the code.

**Why it matters:** Comments make AI-generated code easier to review, especially code you did not write yourself. Good comments explain intent and purpose instead of repeating what the syntax already says.

### 3. Use Meaningful Names

Give variables, functions, and components clear names that describe their purpose.

**Why it matters:** Names like `data`, `temp`, or `handleStuff` hide intent. Descriptive names such as `unpaidInvoices` or `fetchUserProfile` make code self-explanatory.

### 4. Avoid Duplicate and Unnecessary Code

Don't repeat the same logic in different places. Reuse existing code whenever possible.

**Why it matters:** AI assistants often copy logic instead of reusing it. Duplicated code means a bug must be fixed in several places, and the copies slowly drift apart.

### 5. Keep Functions Small

Each function should have one clear job. Avoid putting multiple unrelated tasks inside one function.

**Why it matters:** Small, focused functions are easier to test, reuse, and understand. If a function's name needs the word "and", it is probably doing too much.

### 6. Use Reusable Components and Functions

Create components and functions that can be reused in different parts of the application instead of writing the same code again.

**Why it matters:** Code designed for reuse accepts parameters or props instead of hard-coded values, so one well-tested piece can serve many parts of the application.

### 7. Follow the Existing Project Structure

Respect the current folder structure, file organization, and coding style. Don't introduce a new structure without a good reason.

**Why it matters:** An assistant does not know your conventions unless it looks for them. Mixing new patterns with existing ones makes a codebase inconsistent and harder to navigate.

### 8. Don't Recreate Existing Components

Before creating a new component or feature, check whether something similar already exists. Reuse or improve existing components when possible.

**Why it matters:** AI assistants frequently build a new button, modal, or helper when one already exists. Checking first keeps a single source of truth.

### 9. Handle Errors and Application States Properly

Handle loading states, empty states, errors, and success messages. Always provide useful feedback to users.

**Why it matters:** Code that handles only the "happy path" breaks in real use. Users should always know whether something is loading, empty, failed, or completed successfully.

### 10. Follow Security Best Practices

Protect sensitive information, validate user input, secure API endpoints, and check user permissions. Before finishing any feature, check it against this list:

- Keep API keys and secrets out of the code and the frontend. Store them in environment variables, and make sure `.env` files are listed in `.gitignore`.
- Require proper authentication, and protect admin routes on the server, not only in the UI.
- Check permissions on every request, so users can only access and change their own data.
- Validate and sanitize all form input on the server.
- Prevent cross-site scripting (XSS) by escaping user content before displaying it. Never insert raw user input as HTML.
- Add rate limiting to login, signup, and public API endpoints.
- Set security headers, such as `Content-Security-Policy`, `Strict-Transport-Security`, and `X-Content-Type-Options`.
- Turn off debug mode and detailed error messages in production.
- Keep dependencies up to date, and check them for known vulnerabilities (for example, with `npm audit`).
- Make sure no sensitive files are publicly accessible, such as `.env` files, the `.git` folder, backups, or logs.
- Secure the database: use parameterized queries, give the application only the access it needs, and never expose the database directly to the internet.
- Hash passwords with a strong algorithm such as bcrypt or Argon2. Never store passwords in plain text.

**Why it matters:** Generated code can work correctly and still be insecure. AI assistants rarely add these protections unless asked, and a single missed item can expose user data or the whole application.

### 11. Follow Performance Best Practices

Avoid unnecessary API requests, optimize database queries, and prevent unnecessary rendering or processing.

**Why it matters:** Small inefficiencies, such as repeated requests, fetching more data than needed, or components that re-render on every change, add up and slow the application down as it grows.

### 12. Make All UI Designs Responsive

Ensure the application works properly on mobile, tablet, and desktop screens.

**Why it matters:** AI assistants often design for a single screen size. Many users visit on mobile devices, and fixed layouts that break on small screens are a common problem.

### 13. Don't Modify Unrelated Code

Only change files and functionality related to the requested task. Don't break or modify existing features unnecessarily.

**Why it matters:** Unrequested refactors and "improvements" make changes harder to review and can break working features. Other improvements should be suggested separately, not applied silently.

### 14. Inspect Before Making Changes

Before implementing anything, examine the existing code and understand how the relevant parts of the application work.

**Why it matters:** Changes made without understanding the surrounding code tend to conflict with it. Reading the relevant files first leads to changes that fit the project.

### 15. Explain Important Changes

After implementation, summarize which files were changed, what was added or modified, and why.

**Why it matters:** A clear summary lets you review the work quickly, spot unexpected edits, and keep track of how the project changes over time.

### 16. Suggest a Meaningful Commit Message

After completing a task, suggest a clear commit message that describes what changed and why. Start with a short summary line (about 50 characters) that begins with a verb, such as "Add", "Fix", or "Update". Add a short body when the reason for the change is not obvious. Avoid vague messages like "update" or "fix stuff".

**Why it matters:** The commit history is how developers find when and why something changed. Clear messages make it easy to track down bugs, review past work, and undo changes safely.

```text
Bad:  fixed stuff
Good: Fix login error when email contains uppercase letters
```

### 17. Plan Before Building

Before starting a new project or a major feature, make sure these planning documents exist. If any are missing, draft them and ask for approval before writing code:

- **Product requirements:** what the application does, feature by feature.
- **Technical requirements:** the languages, frameworks, libraries, and services it is built on.
- **App flow:** what happens when a user takes an action, and which page or screen comes next.
- **Design brief:** colors, fonts, and how each screen should look, so the design stays consistent.
- **Database schema:** what data is stored, how it is structured, and who can access it.
- **Implementation plan:** what gets built, and in what order.

Follow these documents while building. If a request conflicts with them, point out the conflict and ask before continuing.

**Why it matters:** Without a plan, AI assistants guess: they choose tools, invent screens, and change direction halfway through. Written documents keep every session working toward the same product and make the result predictable.

### 18. Prevent Race Conditions

When two requests can change the same data at the same time, such as stock, seats, balances, or counters, never check a value in one step and update it in another. Make the database check and update in a single atomic step, for example with a conditional update, and confirm that a row was actually changed. When several changes must happen together, use a transaction and lock the rows being changed. Review existing code for this "check, then write" pattern and fix it.

**Why it matters:** Code with this problem works perfectly when you test it alone, then fails in production when two users act at the same moment. The result is overselling, double charges, or negative balances, and the bug is hard to reproduce.

```js
// Bad: check, then write in two separate steps
const { rows } = await db.query("SELECT remaining FROM tickets WHERE id = $1", [id]);
if (rows[0].remaining > 0) {
  await db.query("UPDATE tickets SET remaining = remaining - 1 WHERE id = $1", [id]);
}

// Good: check and write in one atomic step
const result = await db.query(
  "UPDATE tickets SET remaining = remaining - 1 WHERE id = $1 AND remaining > 0",
  [id]
);
if (result.rowCount === 0) {
  // Sold out: show a clear message to the user
}
```

---

## General Instructions

These instructions apply to every task, alongside the numbered rules.

- **Don't install unnecessary packages.** Use existing libraries whenever possible.
- **Test your changes.** Fix any errors or warnings before finishing.
- **Aim for quality, not just working code.** Don't just make the code work. Make it clean, secure, organized, easy to understand, and easy to maintain.

---

## Copy-Ready Version

Copy the block below into your AI assistant's instructions or prompt. Remove any rules that don't apply to your project.

```text
Follow these coding rules:

1. Write Clean and Readable Code: Write code that is easy to read, understand, and maintain. Avoid unnecessary complexity.
2. Add Clear Code Comments: Add comments that explain what important lines and blocks of code do. Comments should help developers understand the purpose of the code.
3. Use Meaningful Names: Give variables, functions, and components clear names that describe their purpose.
4. Avoid Duplicate and Unnecessary Code: Don't repeat the same logic in different places. Reuse existing code whenever possible.
5. Keep Functions Small: Each function should have one clear job. Avoid putting multiple unrelated tasks inside one function.
6. Use Reusable Components and Functions: Create components and functions that can be reused in different parts of the application instead of writing the same code again.
7. Follow the Existing Project Structure: Respect the current folder structure, file organization, and coding style. Don't introduce a new structure without a good reason.
8. Don't Recreate Existing Components: Before creating a new component or feature, check whether something similar already exists. Reuse or improve existing components when possible.
9. Handle Errors and Application States Properly: Handle loading states, empty states, errors, and success messages. Always provide useful feedback to users.
10. Follow Security Best Practices: Protect sensitive information, validate user input, secure API endpoints, and check user permissions. Before finishing any feature, check that:
   - API keys and secrets are stored in environment variables, never in the code or frontend, and .env files are in .gitignore.
   - Authentication is required, and admin routes are protected on the server.
   - Every request checks permissions, so users can only access their own data.
   - All form input is validated and sanitized on the server.
   - User content is escaped to prevent XSS. Raw user input is never inserted as HTML.
   - Login, signup, and public API endpoints have rate limiting.
   - Security headers are set (Content-Security-Policy, Strict-Transport-Security, X-Content-Type-Options).
   - Debug mode and detailed error messages are turned off in production.
   - Dependencies are up to date and checked for known vulnerabilities.
   - No sensitive files are publicly accessible (.env, .git, backups, logs).
   - The database uses parameterized queries, minimal access rights, and is not exposed to the internet.
   - Passwords are hashed with bcrypt or Argon2, never stored in plain text.
11. Follow Performance Best Practices: Avoid unnecessary API requests, optimize database queries, and prevent unnecessary rendering or processing.
12. Make All UI Designs Responsive: Ensure the application works properly on mobile, tablet, and desktop screens.
13. Don't Modify Unrelated Code: Only change files and functionality related to the requested task. Don't break or modify existing features unnecessarily.
14. Inspect Before Making Changes: Before implementing anything, examine the existing code and understand how the relevant parts of the application work.
15. Explain Important Changes: After implementation, summarize which files were changed, what was added or modified, and why.
16. Suggest a Meaningful Commit Message: After completing a task, suggest a clear commit message that describes what changed and why. Start with a short summary line (about 50 characters) that begins with a verb, such as "Add", "Fix", or "Update". Add a short body when the reason for the change is not obvious. Avoid vague messages like "update" or "fix stuff".
17. Plan Before Building: Before starting a new project or a major feature, make sure these planning documents exist. If any are missing, draft them and ask for approval before writing code:
   - Product requirements: what the application does, feature by feature.
   - Technical requirements: the languages, frameworks, libraries, and services it is built on.
   - App flow: what happens when a user takes an action, and which page or screen comes next.
   - Design brief: colors, fonts, and how each screen should look, so the design stays consistent.
   - Database schema: what data is stored, how it is structured, and who can access it.
   - Implementation plan: what gets built, and in what order.
   Follow these documents while building. If a request conflicts with them, point out the conflict and ask before continuing.
18. Prevent Race Conditions: When two requests can change the same data at the same time, such as stock, seats, balances, or counters, never check a value in one step and update it in another. Make the database check and update in a single atomic step, for example with a conditional update, and confirm that a row was actually changed. When several changes must happen together, use a transaction and lock the rows being changed. Review existing code for this "check, then write" pattern and fix it.

General instructions:
- Don't install unnecessary packages. Use existing libraries whenever possible.
- Test your changes and fix any errors or warnings.
- Don't just make the code work. Make it clean, secure, organized, easy to understand, and easy to maintain.
```

---

## Adding a New Rule

Follow these steps so the collection stays consistent as it grows.

1. **Check for overlap.** Read the existing rules first. If the idea is already covered, improve that rule instead of adding a new one.
2. **Use the next available number.** Never renumber, reorder, or reuse the number of an existing rule.
3. **Write a short, meaningful title** in title case that starts with a verb or a clear action (for example, "Keep Functions Small").
4. **Write the instruction** as a few short, direct sentences addressed to the AI assistant. Use a short checklist when the rule has several specific checks.
5. **Explain why it matters** in one or two sentences.
6. **Update every place the rule appears:**
   - The [Contents](#contents) list in this file
   - The [Rules](#rules) section in this file
   - The [Copy-Ready Version](#copy-ready-version) in this file
   - The Coding Rules list in [README.md](README.md)

### Rule template

```markdown
### N. Rule Title

One or two sentences written as a direct instruction to the AI assistant.

**Why it matters:** One or two sentences explaining the problem this rule prevents.
```
