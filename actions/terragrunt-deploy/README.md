# Terragrunt deploy GitHub Action

## Inputs

<!-- AUTO-DOC-INPUT:START - Do not remove or modify this section -->

|       INPUT        |  TYPE  | REQUIRED |         DEFAULT         |                            DESCRIPTION                             |
|--------------------|--------|----------|-------------------------|--------------------------------------------------------------------|
|      actions       | string |  false   |      `"plan-only"`      |      What action to take: 'plan-only' or<br>'plan-and-apply'       |
|       engine       | string |  false   |        `"z/tg"`         | The Terragrunt engine. Valid inputs are<br>'z/tg' and 'terragrunt' |
| terraform-version  | string |  false   |        `"1.2.5"`        |                       The Terraform version                        |
| terragrunt-version | string |  false   |       `"0.38.7"`        |                       The Terragrunt version                       |
|       token        | string |  false   | `"${{ github.token }}"` |                          The GitHub token                          |
|    working-dir     | string |   true   |                         |                  The Terragrunt working directory                  |
|     z-version      | string |  false   |        `"1.0.0"`        |                          The z/tg version                          |

<!-- AUTO-DOC-INPUT:END -->

## Outputs
