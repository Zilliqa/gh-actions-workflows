# Docker cache GitHub Action

## Inputs

<!-- AUTO-DOC-INPUT:START - Do not remove or modify this section -->

|  INPUT   |  TYPE  | REQUIRED |                DEFAULT                |                 DESCRIPTION                 |
|----------|--------|----------|---------------------------------------|---------------------------------------------|
|  bucket  | string |  false   | `"298213327629-github-actions-cache"` | The AWS bucket where is hosted<br>the cache |
|   key    | string |   true   |                                       |     The key to store/retrieve the cache     |
| password | string |  false   |                                       |      The password to access the cache       |
|  region  | string |  false   |             `"us-west-2"`             | The AWS region where is hosted<br>the cache |
|   type   | string |   true   |                `"gha"`                |     The password to access the registry     |
| username | string |  false   |                                       |      The username to access the cache       |

<!-- AUTO-DOC-INPUT:END -->

## Outputs

<!-- AUTO-DOC-OUTPUT:START - Do not remove or modify this section -->

|  OUTPUT   |  TYPE  |      DESCRIPTION       |
|-----------|--------|------------------------|
| image-tag | string | Tag given to the image |

<!-- AUTO-DOC-OUTPUT:END -->
