# CI Dockerized app build and push

## Inputs

<!-- AUTO-DOC-INPUT:START - Do not remove or modify this section -->

|         INPUT         |  TYPE  | REQUIRED | DEFAULT  |          DESCRIPTION          |
|-----------------------|--------|----------|----------|-------------------------------|
|      aws-region       | string |   true   |          |        The AWS region         |
|       oidc-role       | string |   true   |          |   The identity provide role   |
|     profile-name      | string |  false   |          | The AWS configuration profile |
| role-duration-seconds | string |  false   | `"1200"` | Assume role session duration  |
|    role-to-assume     | string |   true   |          |      The role to assume       |

<!-- AUTO-DOC-INPUT:END -->

## Outputs

<!-- AUTO-DOC-OUTPUT:START - Do not remove or modify this section -->

|  OUTPUT   |  TYPE  |      DESCRIPTION       |
|-----------|--------|------------------------|
| image-tag | string | Tag given to the image |

<!-- AUTO-DOC-OUTPUT:END -->
