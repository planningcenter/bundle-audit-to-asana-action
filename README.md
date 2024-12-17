# Bundle Audit To Asana Action

This is a GitHub action that runs `bundle-audit check --update`, and then, if vulnerabilities are detected, creates an Asana task. It's recommended to run it on a schedule (which will, by definition, only run it on the default branch).

## Example usage

```
name: Nightly Bundler Audit

on:
  schedule:
    - cron: '0 0 * * *'  # Run daily at midnight UTC

jobs:
  nightly-audit:
    runs-on: ubuntu-latest

    steps:
      - name: Run Nightly Bundler Audit Action
        uses: planningcenter/bundle-audit-to-asana-action@v1
        with:
          asana_token: ${{ secrets.ASANA_PAT }}
          asana_project_id: ${{ secrets.ASANA_PROJECT_ID }}
          asana_section_id: ${{ secrets.ASANA_SECTION_ID }}
```


## Inputs

| Name | Description | Required |
|:-:|:-:|:-:|
| `asana_token` | An Asana Personal Access Token (generate one [here](https://app.asana.com/0/my-apps)) | yes |
| `asana_project_id` | The project ID of the Asana Project | yes |
| `asana_section_id` | The section ID of the section in the Asana Project | yes |
