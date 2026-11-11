---
layout: default
title: API Specifications as Documentation
---

# API Specifications as Documentation: An Overview

An OpenAPI specification is no longer just an engineering artifact. It is often the first and only documentation a developer or an AI agent reads. If the spec is incomplete, every tool that reads it passes the gaps along.

This overview explains why spec quality matters, who reads the spec, and how writers can improve it. Each section links to a detailed guide where one exists.

## Who reads the spec

| Reader | What it does with the spec | What breaks when the spec is incomplete |
|---|---|---|
| Swagger UI and docs portals | Renders the reference pages | Pages show blank or one-word descriptions |
| Postman | Imports requests and collections | Developers guess at values and formats |
| SDK generators | Turn the spec into client libraries | SDKs lack comments, types, and error handling |
| AI writing tools | Draft reference docs from the spec | Drafts repeat gaps or invent missing details |
| AI agents and MCP servers | Decide which operation to call and how | Agents call the wrong operation or send bad values |

One fix in the spec improves every reader at once. That is why I treat the spec as the source of truth for documentation.

## Common gaps in API specs

Most specs share the same problems:

- One-line or blank descriptions
- Boilerplate such as "successful operation"
- Missing request and response examples
- Missing or incomplete status codes
- Error responses with no body or error schema
- No formats, units, limits, or defaults
- Undocumented edge cases and state rules

**Detailed guide:** [Troubleshooting: Incomplete API Specifications](/case-studies/swagger_api.md) walks through these symptoms using the Swagger Petstore spec. Each symptom includes the cause, the solution, and the result.

## The workflow

I improve a spec in six steps:

1. **Audit** the spec with a linter to list the gaps.
2. **Test** each operation to learn how the API really behaves.
3. **Draft** missing content, with AI help where it saves time.
4. **Verify** every draft against the test results.
5. **Review** the changes with engineering in a pull request.
6. **Fix the source** so every downstream tool improves.

The sections below cover each step.

## Audit the spec with Spectral

[Spectral](https://github.com/stoplightio/spectral) is an open-source linter for OpenAPI specs. The Spectral extension for Visual Studio Code highlights problems as you edit. Its built-in rules catch structural errors. Custom rules can enforce documentation quality, such as requiring a description on every parameter.

A linter turns "the spec has gaps" into a numbered list. Running it again after each fix shows progress. The team can track a simple metric, such as the percentage of operations fully documented.

## Test the API to verify behavior

A linter finds missing content. It cannot tell you what the correct content is. Only testing can do that.

I call each operation in Postman or curl. I start with a valid request. Then I break it on purpose:

- Omit required fields
- Send wrong types and out-of-range values
- Use IDs that do not exist
- Call actions on objects in the wrong state
- Send requests without credentials

Each test result becomes a fact for the spec. A status code the API returns but the spec omits is a gap. A field the spec lists but the API ignores is an error.

## Use AI to draft, then verify

AI tools can draft descriptions, examples, and code samples from a spec in minutes. But AI reads the same incomplete spec. It often fills gaps with confident guesses, such as wrong units or invented fields.

I use AI for speed and testing for accuracy:

- I ask the AI to flag unknowns instead of guessing.
- I check every claim against the spec, the code, or a live call.
- I run every code sample before it ships.

**Detailed guide:** [How Technical Writers Use AI to Fill the Gaps in Incomplete API Specs](/case-studies/ai-and-incomplete-api-specs/)

## Write descriptions for AI agents

AI agents increasingly call APIs on their own. Some teams generate Model Context Protocol (MCP) tools directly from OpenAPI specs. In that case, the spec's descriptions become instructions for the agent.

An agent reads a description to decide when to call an operation and what to send. A vague description leads to the wrong call. Good descriptions for agents:

- Say what the operation does and when to use it
- Say when **not** to use it and name the alternative
- State formats, units, limits, and defaults for every field
- Warn about side effects, such as spending money or deleting data
- Return error messages that explain how to fix the request

These habits help human readers too. A description precise enough for an agent is clear enough for a developer.

## Fix the source, not just the docs

Writers often fix gaps in a separate docs page. The spec stays incomplete, and every other tool still shows the gap.

I fix gaps in the spec itself. Then I submit the changes as a pull request:

- Engineers review the changes in their normal workflow.
- Each question for engineering is short and has a yes or no answer.
- The linter runs on every pull request, so new gaps do not slip in.

This keeps the docs and the API in sync as the API changes.

## Writer and engineer responsibilities

| Task | Writer | Engineer |
|---|---|---|
| Run the linter and list gaps | Owns | Reviews |
| Test operations and record behavior | Owns | Answers questions |
| Write descriptions and examples | Owns | Reviews for accuracy |
| Confirm intended behavior | Asks | Owns |
| Change API behavior or the contract | Flags issues | Owns |

The writer improves the documentation inside the spec. The writer does not change the API contract. Questions about intended behavior go to engineering.

## Key terms

| Term | Meaning |
|---|---|
| OpenAPI specification | A machine-readable description of an API, in JSON or YAML |
| Swagger | Tools for viewing and testing OpenAPI specs, such as Swagger UI |
| Linter | A tool that checks files against rules and flags problems |
| Spectral | An open-source linter for OpenAPI and other API formats |
| MCP | Model Context Protocol, an open standard for connecting AI agents to tools |
| API contract | The agreed behavior of an API: its operations, inputs, and outputs |

## Summary

The spec is the documentation that every tool reads. Audit it with a linter. Test the API to learn the truth. Use AI to draft and testing to verify. Then fix the gaps in the spec itself, so every reader benefits.

