# Add Project Items By Content

Creates new project items from new issues with given titles and bodies in the given repository.

## Inputs

| name | required | default | description | example |
| --- | --- | --- | --- | --- |
| organization | `true` | `null` | The name of the organization that owns the project and the repository | `github` |
| project | `true` | `null` | The name or the number of the project to which the items should be added | `1` |
| repository | `true` | `null` | The ID of the repository in which the issues should be created | `VXNlci0xMA==` |
| content | `true` | `null` | The list of content objects with title and body keys | `[{"title": "ISSUE TITLE", "body": "ISSUE BODY"}]` |

## Outputs

| name | description | example |
| --- | --- | --- |
| added-item-ids | The list of project IDs that were successfully added to the project | `["VXNlci0xMA=="]` |
| failed-content-ids | The list of issue IDs that failed to be added to the project | `["VXNlci0xMA=="]` |
| issues | The list of issues that were added | `[{"id": "VXNlci0xMA=="}]` |
