---
name: figma-create-design-system-rules
description: Generates custom design system rules for the user's codebase. Use when user says "create design system rules", "generate rules for my project", "set up design rules", "customize design system guidelines", or wants to establish project-specific conventions for Figma-to-code workflows. Requires Figma MCP server connection.
disable-model-invocation: false
---

# Create Design System Rules

## Overview
This skill helps you generate custom design system rules tailored to a project's specific needs. These rules guide AI coding agents to produce consistent code when implementing Figma designs.

## Supported Rule Files
- Claude Code: `CLAUDE.md`
- Codex CLI: `AGENTS.md`
- Cursor: `.cursor/rules/figma-design-system.mdc`

## What Are Design System Rules?
Design system rules are project-level instructions that encode the unwritten knowledge of the codebase:
- Which layout primitives and components to use
- Where component files should be located
- How components should be named and structured
- What should never be hardcoded
- How to handle design tokens and styling
- Project-specific architectural patterns

## Prerequisites
- Figma MCP server must be connected and accessible.
- Access to the project codebase for analysis.
- Understanding of the team's component conventions, or willingness to establish them.

## Required Workflow
1. Run the `create_design_system_rules` tool to get the foundational prompt and template.
2. Analyze the codebase to understand component organization, styling, and architectural patterns.
3. Generate project-specific rules from that analysis.

## Figma MCP Integration
- Always inspect the codebase before finalizing rules.
- Define clear component, styling, and token conventions.
- Include Figma integration rules that tell agents how to use `get_design_context`, `get_screenshot`, and related tools.
