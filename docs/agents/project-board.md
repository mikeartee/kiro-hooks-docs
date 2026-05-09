# Project Board — GitHub Projects v2

## Board

| Field   | Value                                              |
|---------|----------------------------------------------------|
| Title   | kiro-hooks-docs                                    |
| URL     | https://github.com/users/mikeartee/projects/3      |
| Node ID | `PVT_kwHOBIHFbs4BXJvN`                             |
| Owner   | mikeartee                                          |
| Number  | 3                                                  |

## Status Field

| Field      | Value                                    |
|------------|------------------------------------------|
| Field name | Status                                   |
| Field ID   | `PVTSSF_lAHOBIHFbs4BXJvNzhSYph0`        |

## Status Options

| Option name | Option ID  |
|-------------|------------|
| Backlog     | `70a3f49e` |
| Ready       | `f2a4b39f` |
| In progress | `c51ca6bd` |
| In review   | `825eb3a7` |
| Done        | `edb2e3eb` |

## Skill → Status Mapping

| Skill action                                                        | Status      |
|---------------------------------------------------------------------|-------------|
| `/triage` → `needs-triage` or `needs-info`                          | Backlog     |
| `/triage` → `ready-for-agent` or `ready-for-human`                  | Ready       |
| `/triage` → `tracking` / `/to-issues` parent issue                  | In progress |
| `/tdd` step 1 — work begins                                         | In progress |
| `/tdd` — PR opened                                                  | In review   |
| `/tdd-parallel` step 4 — integration PR opened (parent + all slices)| In review   |
| `/triage` → `wontfix`                                               | Done        |

Issue closure (PR merged, direct-push commit, or manual close) moves the card to **Done** automatically via the board's built-in **Auto-close issue** workflow — skills do not write `Done` themselves.

## Recommended Built-in Workflows

Enable these at https://github.com/users/mikeartee/projects/3/workflows:

- **Auto-add to project** — filter: `repo:mikeartee/kiro-hooks-docs is:issue,pr is:open`
- **Auto-close issue** — moves card to Done when the linked issue is closed

## GraphQL Snippet

To update a card's Status programmatically:

```bash
gh api graphql -f query='
  mutation($projectId: ID!, $itemId: ID!, $fieldId: ID!, $optionId: String!) {
    updateProjectV2ItemFieldValue(input: {
      projectId: $projectId
      itemId: $itemId
      fieldId: $fieldId
      value: { singleSelectOptionId: $optionId }
    }) {
      projectV2Item { id }
    }
  }
' \
  -f projectId="PVT_kwHOBIHFbs4BXJvN" \
  -f itemId="<PVTI_...>" \
  -f fieldId="PVTSSF_lAHOBIHFbs4BXJvNzhSYph0" \
  -f optionId="<option-id-from-table-above>"
```
