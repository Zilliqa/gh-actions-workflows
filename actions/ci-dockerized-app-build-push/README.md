# CI Dockerized app build and push

## Inputs

<!-- AUTO-DOC-INPUT:START - Do not remove or modify this section -->

|       INPUT       |  TYPE  | REQUIRED | DEFAULT  |                            DESCRIPTION                             |
|-------------------|--------|----------|----------|--------------------------------------------------------------------|
|    aws-region     | string |  false   |          |                           The AWS region                           |
|    build-args     | string |  false   |          |                    Arguments to build the image                    |
|     cache-key     | string |  false   |          |                The key to store/retrieve the cache                 |
|      context      | string |  false   |          |                The context to build the Dockerfile                 |
|       file        | string |   true   |          |                     The path to the Dockerfile                     |
|     oidc-role     | string |  false   |          |                   The AWS role trusting the OIDC                   |
|       pull        | string |  false   | `"true"` |                     Enable/disable image pull                      |
|       push        | string |  false   | `"true"` |                     Enable/disable image push                      |
|     registry      | string |   true   |          |                          Docker registry                           |
| registry-password | string |  false   |          |                The password to access the registry                 |
| registry-username | string |  false   |          |                The username to access the registry                 |
|  role-to-assume   | string |  false   |          |         The AWS role to assume to<br>login to the registry         |
|        tag        | string |   true   |          |                        The tag of the image                        |
|    tag-latest     | string |  false   |          |                     If true add the tag latest                     |
|    tag-length     | string |  false   |          | The number of chars composing the<br>tag from the short commit sha |
|      target       | string |  false   |          |                The target to build in the<br>image                 |

<!-- AUTO-DOC-INPUT:END -->

## Outputs

<!-- AUTO-DOC-OUTPUT:START - Do not remove or modify this section -->

|  OUTPUT   |  TYPE  |      DESCRIPTION      |
|-----------|--------|-----------------------|
|  digest   | string |     Image digest      |
|  imageid  | string |       Image ID        |
| imagetags | string |     Generated tag     |
| metadata  | string | Build result metadata |

<!-- AUTO-DOC-OUTPUT:END -->
