# Terragrunt deploy GitHub Action

## Inputs

<!-- AUTO-DOC-INPUT:START - Do not remove or modify this section -->

|       INPUT        |  TYPE  | REQUIRED |         DEFAULT         |                             DESCRIPTION                              |
|--------------------|--------|----------|-------------------------|----------------------------------------------------------------------|
|      actions       | string |  false   |      `"plan-only"`      |      What action to take: 'plan-only' <br>or 'plan-and-apply'        |
|   devops-folder    | string |  false   |         `"./"`          |            The root folder of the <br>devops repository              |
|       engine       | string |  false   |        `"z/tg"`         | The Terragrunt engine. Valid inputs <br>are 'z/tg' and 'terragrunt'  |
| terraform-version  | string |  false   |        `"1.2.5"`        |                        The Terraform version                         |
| terragrunt-version | string |  false   |       `"0.38.7"`        |                        The Terragrunt version                        |
|       token        | string |  false   | `"${{ github.token }}"` |                           The GitHub token                           |
|    working-dir     | string |   true   |                         |                   The Terragrunt working directory                   |
|     z-version      | string |  false   |        `"1.0.0"`        |                           The z/tg version                           |

<!-- AUTO-DOC-INPUT:END -->

## Outputs
