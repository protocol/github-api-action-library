# Update Project Field With Recent References

Updates project field that holds recent references.

## Inputs

| name | required | default | description | example |
| --- | --- | --- | --- | --- |
| organization | `true` | `null` | The name of the organization that owns the project | `github` |
| project | `true` | `null` | The number of the project | `1` |
| field | `true` | `null` | The ID of the field that should be updated | `VXNlci0xMA==` |
| max | `true` | `1` | The max number of references that should be fetched for each issue or pull request | `1` |
| since | `false` | `null` | Issues or pull requests updated before the date will not be included in the results  | `-7days` |

## Outputs

| name | description | example |
| --- | --- | --- |
| updated-item-ids | The list of project item IDs that were successfully updated | `["VXNlci0xMA=="]` |
| failed-item-ids | The list of project item IDs that failed to be updated | `["VXNlci0xMA=="]` |
