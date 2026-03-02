# ai-driven-product

AI starts with product.

## Project Overview
A reference implementation and workflow guide for a federal software consulting firm demonstrating how to transform a traditional software development process into an AI-native workflow.

The goal is to show how AI tooling (primarily Claude) can be embedded at every stage of the SDLC — from requirements and design through development, testing, and delivery — increasing speed, consistency, and quality for federal software engagements.

## Commands
<!-- Update these as the project takes shape -->
- **Install:** TBD
- **Dev server:** TBD
- **Build:** TBD
- **Test:** TBD
- **Lint/Format:** TBD

## Architecture
<!-- Fill in as decisions are made -->
- Stack: TBD
- AI model(s): Claude (via Anthropic API) — default to `claude-sonnet-4-6` or `claude-opus-4-6`
- Key directories: TBD

## Code Conventions
- Keep code simple and focused — avoid over-engineering
- Prefer editing existing files over creating new ones
- No unnecessary comments or docstrings on unchanged code
- Validate only at system boundaries (user input, external APIs)

## AI / Anthropic API
- Use the latest Claude models: Sonnet 4.6 (`claude-sonnet-4-6`) for most tasks, Opus 4.6 (`claude-opus-4-6`) for complex reasoning
- Store API keys in `.env` (never commit secrets)

## Environment Variables
- Copy `.env.example` to `.env` (file TBD)
- Never commit `.env` or secret keys

## Git
- Main branch: `main`
- Remote: https://github.com/eganpg/ai-driven-product
