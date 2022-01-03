# Find Recent References For Project Items

Finds a given number of recent cross reference objects for the content behind the project items.

## Inputs

| name | required | default | description | example |
| --- | --- | --- | --- | --- |
| organization | `true` | `null` | The name of the organization that owns the project | `github` |
| project | `true` | `null` | The number of the project | `1` |
| max | `true` | `1` | The max number of references that should be fetched for each issue or pull request | `1` |
| since | `false` | `null` | Issues or pull requests updated before the date will not be included in the results  | `-7days` |

## Outputs

| name | description | example |
| --- | --- | --- |
| items | The list of items that were fetched | `[{"id": "", "content": { "timelineItems": { "totalCount": 2, updatedAt: "DATE", nodes: [{"source": {"number": "1", "repository": {"nameWithOwner": "github/github#1"}, "url": "URL"}}] }}}]` |
