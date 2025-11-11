# Add missing 'Hooks' feature slide to presentation

## Issue
The presentation mentions 'Hooks' in Slide 6 (the Claude Code Features divider) but never actually explains what hooks are or provides examples.

## Suggestion
Add a dedicated slide after the Slash Commands slide that covers:
- What hooks are (event-driven automation)
- Examples of hooks (e.g., `user-prompt-submit-hook`, `session-start-hook`)
- Real use cases (pre-commit checks, auto-formatting, notifications)
- Configuration example

## Impact
This creates confusion for viewers who see 'Hooks' listed but never explained. Given that hooks are a core extensibility feature of Claude Code, they deserve their own slide.

## Location
Between current slides 7 (Slash Commands) and 8 (Custom Agents), or after Agents.

## Priority
**High** - Listed feature is never explained
