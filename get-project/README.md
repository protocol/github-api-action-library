# Get Project

Get project by name or number.

## Inputs

| name | required | default | description | example |
| --- | --- | --- | --- | --- |
| organization | `true` | `null` | The name of the organization that owns the project and the repository | `github` |
| project | `true` | `null` | The name or the number of the project to which the items should be added | `1` |

## Outputs

| name | description | example |
| --- | --- | --- |
| project | The project object | `{"id": "VXNlci0xMA==", "number": 1}` |
