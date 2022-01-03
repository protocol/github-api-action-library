# Add Issues By Content

Creates new issues with given titles and bodies in the given repository.

## Inputs

| name | required | default | description | example |
| --- | --- | --- | --- | --- |
| repository | `true` | `null` | The ID of the repository in which the issues should be created | `VXNlci0xMA==` |
| content | `true` | `null` | The list of content objects with title and body keys | `[{"title": "ISSUE TITLE", "body": "ISSUE BODY"}]` |

## Outputs

| name | description | example |
| --- | --- | --- |
| issues | The list of issues that were added | `[{"id": "VXNlci0xMA=="}]` |
