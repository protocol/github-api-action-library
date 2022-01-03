# Add Project Items By Content Query

Finds content that matches given query and creates new project items for it in the given repository.

## Inputs

| name | required | default | description | example |
| --- | --- | --- | --- | --- |
| organization | `true` | `null` | The name of the organization that owns the project | `github` |
| project | `true` | `null` | The name or the number of the project to which the items should be added | `1` |
| query | `true` | `null` | The [content search query](https://docs.github.com/en/search-github/searching-on-github/searching-issues-and-pull-requests) | `is:pr is:open` |

## Outputs

| name | description | example |
| --- | --- | --- |
| added-item-ids | The list of project IDs that were successfully added to the project | `["VXNlci0xMA=="]` |
| failed-content-ids | The list of issue IDs that failed to be added to the project | `["VXNlci0xMA=="]` |
| issues-or-pull-requests | The list of issues or pull requests that were added | `[{"id": "VXNlci0xMA=="}]` |
