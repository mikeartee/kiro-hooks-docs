# Kiro Hooks Docs

Community library of Kiro agent hooks, distributed via the Kiro Hooks Browser extension.

## Structure

Hooks are organized by category. Each hook is a JSON file following the official Kiro hook schema.

## Categories

- `code-quality/` — Linting, formatting, and coding standards enforcement
- `testing/` — Test generation and test suite execution
- `documentation/` — API docs and README sync
- `security/` — Secret scanning and vulnerability checks
- `workflow/` — Gap analysis, task validation, and progress tracking
- `maintenance/` — Dependency audits and on-demand checks

## Hook Schema

```json
{
  "name": "Hook Name",
  "version": "1.0.0",
  "description": "What this hook does",
  "when": {
    "type": "fileEdited|fileCreated|fileDeleted|userTriggered|promptSubmit|agentStop|preToolUse|postToolUse|preTaskExecution|postTaskExecution",
    "patterns": ["**/*.ts"],
    "toolTypes": ["write", "read", "shell"]
  },
  "then": {
    "type": "askAgent|runCommand",
    "prompt": "string (askAgent only)",
    "command": "string (runCommand only)"
  }
}
```

## Contributing

Add a JSON file to the appropriate category folder. Follow the schema above.
Run `npm run validate` (coming soon) to verify your hook before submitting a PR.

