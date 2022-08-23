# GitHub API Action Library

This library consists of actions that call GitHub API(mainly GraphQL).

## Actions

- [Add Issues By Content](add-issues-by-content/README.md)
- [Add Project Items By Content](add-project-items-by-content/README.md)
- [Add Project Items By Content ID](add-project-items-by-content-id/README.md)
- [Add Project Items By Content Query](add-project-items-by-content-query/README.md)
- [Find Content By Query](find-content-by-query/README.md)
- [Find Recent References For Project Items](find-recent-references-for-project-items/README.md)
- [Get Project](get-project/README.md)
- [Get Project Field](get-project-field/README.md)
- [Get Repository](get-repository/README.md)
- [Update Project Field](update-project-field/README.md)
- [Update Project Field With Recent References](update-project-field-with-recent-references/README.md)

## Examples

### Add Project Items By Content Query Every Week

Adds new project items matching query every week. If it fails to do that, it creates an issue that lists URLs to content items that failed to be added.

```yml
name: Add Project Items Periodically
on:
  schedule:
    - cron: '0 0 * * 0'
jobs:
  add:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        # https://docs.github.com/en/search-github/searching-on-github/searching-issues-and-pull-requests
        query:
          - is:issue repo:github/github is:open
      fail-fast: false
    env:
      ORGANIZATION: github
      PROJECT: GitHub Project
      REPOSITORY: github
      SINCE: -7days
    steps:
      - id: query
        env:
          QUERY: ${{ matrix.query }}
        run: |
          echo "::set-output name=value::${QUERY} created:>=$(date --date="${SINCE}" +"%Y-%m-%d")"
        shell: bash
      - id: items
        uses: protocol/github-api-action-library/add-project-items-by-content-query@v1.1.0
        with:
          organization: ${{ env.ORGANIZATION }}
          project: ${{ env.PROJECT }}
          query: ${{ steps.query.outputs.value }}
      - id: content
        if: ${{ steps.items.outputs.failed-content-ids != '[]' }}
        env:
          FAILED_CONTENT_IDS: ${{ steps.items.outputs.failed-content-ids }}
          ISSUES_OR_PULL_REUQESTS: ${{ steps.items.outputs.issues-or-pull-requests }}
        run: |
          title='Add project items manually'
          body=$'```\n'"$(jq -r "[.[] | {\"\\(.id)\":.url}] | add | $(jq -r '[.[] | ".\"\(.)\""] | join(",")' <<< "${FAILED_CONTENT_IDS}")" <<< "${ISSUES_OR_PULL_REQUESTS}")"$'\n```'
          body="${body//$'\n'/\\\\n}"
          echo "::set-output name=value::[{\"title\":\"${title}\",\"body\":\"${body}\"}]"
        shell: bash
      - if: ${{ steps.items.outputs.failed-content-ids != '[]' }}
        uses: protocol/github-api-action-library/add-project-items-by-content@v1.1.0
        with:
          organization: ${{ env.ORGANIZATION }}
          project: ${{ env.PROJECT }}
          repository: ${{ env.REPOSITORY }}
          content: ${{ steps.content.outputs.value }}

```

### Update Project Field With Recent References Every Week

Updates at most 3 recent references on all the project items every week. If it fails to do that, it outputs the list of failed project item IDs.

```yml
name: Update Recent References Periodically
on:
  schedule:
    - cron: '0 0 * * 0'
jobs:
  add:
    runs-on: ubuntu-latest
    env:
      ORGANIZATION: github
      PROJECT: GitHub Project
      FIELD: Cross References
      MAX: 3
      SINCE: -7days
    steps:
      - id: items
        uses: protocol/github-api-action-library/update-project-field-with-recent-references@v1.1.0
        with:
          organization: ${{ env.ORGANIZATION }}
          project: ${{ env.PROJECT }}
          field: ${{ env.FIELD }}
          max: ${{ env.MAX }}
          since: ${{ env.SINCE }}
      - if: ${{ steps.items.outputs.failed-item-ids != '[]' }}
        env:
          FAILED_ITEM_IDS: ${{ steps.items.outputs.failed-item-ids }}
        run: |
          echo "${FAILED_ITEM_IDS}"
          exit 1

```
