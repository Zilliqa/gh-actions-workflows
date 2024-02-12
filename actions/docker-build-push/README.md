# Docker build and push GitHub Action

## Inputs

<!-- AUTO-DOC-INPUT:START - Do not remove or modify this section -->

|   INPUT    |  TYPE  | REQUIRED | DEFAULT  |                                      DESCRIPTION                                       |
|------------|--------|----------|----------|----------------------------------------------------------------------------------------|
| build-args | string |  false   |          |                              Arguments to build the image                              |
| cache-from | string |  false   |          |                                    Docker registry                                     |
|  cache-to  | string |  false   |          |                        The username to access the <br>registry                         |
|  context   | string |  false   |          |                        The context to build the <br>Dockerfile                         |
|    file    | string |   true   |          |                               The path to the Dockerfile                               |
|    pull    | string |  false   | `"true"` |                               Enable/disable image pull                                |
|    push    | string |  false   | `"true"` |                               Enable/disable image push                                |
|  secrets   | string |  false   |          | List of secrets to expose <br>to the build (e.g., key=string, GIT\_AUTH\_TOKEN=mytoken)  |
|    tags    | string |   true   |          |                                 The tags of the image                                  |
|   target   | string |  false   |          |                         The target to build in <br>the image                           |

<!-- AUTO-DOC-INPUT:END -->

## Outputs

<!-- AUTO-DOC-OUTPUT:START - Do not remove or modify this section -->

|  OUTPUT  |  TYPE  |      DESCRIPTION      |
|----------|--------|-----------------------|
|  digest  | string |     Image digest      |
| imageid  | string |       Image ID        |
| metadata | string | Build result metadata |

<!-- AUTO-DOC-OUTPUT:END -->
