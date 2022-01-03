# Find Content By Query

Finds content that matches given query.

## Inputs

| name | required | default | description | example |
| --- | --- | --- | --- | --- |
| query | `true` | `null` | The [content search query](https://docs.github.com/en/search-github/searching-on-github/searching-issues-and-pull-requests) | `is:pr is:open` |

## Outputs

| name | description | example |
| --- | --- | --- |
| issues-or-pull-requests | The list of issues or pull requests that were added | `[{"id": "VXNlci0xMA=="}]` |
