# Configure AWS profile GitHub Action

## Inputs

<!-- AUTO-DOC-INPUT:START - Do not remove or modify this section -->

|    INPUT     |  TYPE  | REQUIRED | DEFAULT |                 DESCRIPTION                  |
|--------------|--------|----------|---------|----------------------------------------------|
|  aws-region  | string |   true   |         |                The AWS region                |
| profile-name | string |   true   |         | The profile to add to the<br>AWS config file |

<!-- AUTO-DOC-INPUT:END -->

## Outputs

<!-- AUTO-DOC-OUTPUT:START - Do not remove or modify this section -->

|  OUTPUT   |  TYPE  |      DESCRIPTION       |
|-----------|--------|------------------------|
| image-tag | string | Tag given to the image |

<!-- AUTO-DOC-OUTPUT:END -->
