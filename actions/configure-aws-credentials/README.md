# Configure AWS credentials GitHub Action

## Inputs

<!-- AUTO-DOC-INPUT:START - Do not remove or modify this section -->

|         INPUT         |  TYPE  | REQUIRED | DEFAULT  |          DESCRIPTION          |
|-----------------------|--------|----------|----------|-------------------------------|
|      aws-region       | string |   true   |          |        The AWS region         |
|       oidc-role       | string |   true   |          |   The identity provide role   |
|     profile-name      | string |  false   |          | The AWS configuration profile |
| role-duration-seconds | string |  false   | `"3600"` | Assume role session duration  |
|    role-to-assume     | string |   true   |          |      The role to assume       |

<!-- AUTO-DOC-INPUT:END -->

## Outputs

<!-- AUTO-DOC-OUTPUT:START - Do not remove or modify this section -->

No outputs.

<!-- AUTO-DOC-OUTPUT:END -->
