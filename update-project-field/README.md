# Update Project Field

Updates project field for given item value pairs.

## Inputs

| name | required | default | description | example |
| --- | --- | --- | --- | --- |
| project | `true` | `null` | The ID of the project in which the items should be updated | `VXNlci0xMA==` |
| field | `true` | `null` | The ID of the field that should be updated | `VXNlci0xMA==` |
| map | `true` | `null` | The map from project item IDs to field values that should be set | `{"VXNlci0xMA==": "VALUE"}` |

## Outputs

| name | description | example |
| --- | --- | --- |
| updated-item-ids | The list of project item IDs that were successfully updated | `["VXNlci0xMA=="]` |
| failed-item-ids | The list of project item IDs that failed to be updated | `["VXNlci0xMA=="]` |
