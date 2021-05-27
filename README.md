# GitHub Estimates Action ![Update project estimates](https://github.com/mathiasjakobsen/github-estimates-action/workflows/Update%20project%20estimates/badge.svg)

Used to working with estimation JIRA style, and want to do something like that in GitHub? This is for you.

![Demo](https://github.com/mathiasjakobsen/github-estimates-action/blob/master/demo.gif)

This [action](https://help.github.com/en/actions) automatically updates project column titles with issue estimate (i.e. story points, hours, etc.) totals, based on `labels` attached on issues. Use this action together with the `issues::labeled`, `issues::unlabeled`, `project_card::moved` and `project_card::created` [events](https://help.github.com/en/actions/reference/events-that-trigger-workflows#about-workflow-events), and have your project boards update within a couple of seconds after updating cards/issues/estimates.

## Requirements

Project **must** have one or more labels with a description named "Story Point" and a numeric value, such as `0.5` or `10`. Use these labels on issues, to estimate them, and let the workflow provide the overview.

![Issue](https://github.com/mathiasjakobsen/github-estimates-action/blob/master/issue.png)

## Inputs

- `token` **(required)** GitHub repository token (`$GITHUB_TOKEN`)
- `owner` **(required)** GitHub user or organisation.
- `repo` **(required)** GitHub repository name.
- `prefix` Aggregate labels that start with this prefix, like `points/3` instead of labels described as "Story Points".

## Usage

```yml
name: Update project estimates

on:
  issues:
    types: [labeled, unlabeled]
  project_card:
    types: [moved, created]

jobs:
  run:
    runs-on: ubuntu-latest
    name: Update project column estimates
    steps:
      - uses: actions/checkout@v1

      - name: Use API to calculate and update total estimates in each column
        id: run
        uses: ./
        with:
          owner: 'mathiasjakobsen'
          repo: 'github-estimates-action'
          token: ${{ secrets.GITHUB_TOKEN }}
```

## License

![WTFPL](http://www.wtfpl.net/wp-content/uploads/2012/12/wtfpl-badge-3.png)
