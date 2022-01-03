# Add Project Items By Content ID

Creates new project items for given content IDs in the given repository.

## Inputs

| name | required | default | description | example |
| --- | --- | --- | --- | --- |
| project | `true` | `null` | The ID of the project to which the items should be added | `VXNlci0xMA==` |
| content-ids | `true` | `null` | The list of content IDs | `["VXNlci0xMA=="]` |

## Outputs

| name | description | example |
| --- | --- | --- |
| added-item-ids | The list of project IDs that were successfully added to the project | `["VXNlci0xMA=="]` |
| failed-content-ids | The list of issue IDs that failed to be added to the project | `["VXNlci0xMA=="]` |
