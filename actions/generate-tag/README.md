# Generate tag

## Inputs

<!-- AUTO-DOC-INPUT:START - Do not remove or modify this section -->

|       INPUT       |  TYPE  | REQUIRED | DEFAULT  |             DESCRIPTION             |
|-------------------|--------|----------|----------|-------------------------------------|
|    build-args     | string |  false   |          |    Arguments to build the image     |
|      context      | string |   true   |          | The context to build the Dockerfile |
|       file        | string |   true   |          |     The path to the Dockerfile      |
|    image-name     | string |   true   |          |        The name of the image        |
|     image-tag     | string |  false   |          |        The tag of the image         |
|       push        | string |  false   | `"true"` |      Enable/disable image push      |
|     registry      | string |   true   |          |           Docker registry           |
| registry-password | string |   true   |          | The password to access the registry |
| registry-username | string |   true   |          | The username to access the registry |
|      target       | string |  false   |          | The target to build in the<br>image |

<!-- AUTO-DOC-INPUT:END -->

## Outputs

<!-- AUTO-DOC-OUTPUT:START - Do not remove or modify this section -->

|  OUTPUT   |  TYPE  |      DESCRIPTION       |
|-----------|--------|------------------------|
| image-tag | string | Tag given to the image |

<!-- AUTO-DOC-OUTPUT:END -->
