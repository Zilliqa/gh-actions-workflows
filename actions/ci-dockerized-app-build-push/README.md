# CI Dockerized app build and push

## Inputs

<!-- AUTO-DOC-INPUT:START - Do not remove or modify this section -->

|                                                     INPUT                                                      |  TYPE  | REQUIRED |   DEFAULT    |                                      DESCRIPTION                                       |
|----------------------------------------------------------------------------------------------------------------|--------|----------|--------------|----------------------------------------------------------------------------------------|
|                         <a name="input_build-args"></a>[build-args](#input_build-args)                         | string |  false   |              |                              Arguments to build the image                              |
|                    <a name="input_cache-backend"></a>[cache-backend](#input_cache-backend)                     | string |  false   | `"registry"` |                      The cache storage backend for <br>the cache                       |
|                          <a name="input_cache-key"></a>[cache-key](#input_cache-key)                           | string |  false   |              |                        The key to store/retrieve the <br>cache                         |
|                             <a name="input_context"></a>[context](#input_context)                              | string |  false   |              |                        The context to build the <br>Dockerfile                         |
|                                  <a name="input_file"></a>[file](#input_file)                                  | string |  false   |              |       The path to the Dockerfile. <br>If not set, it uses <br>the context path.        |
|                                  <a name="input_pull"></a>[pull](#input_pull)                                  | string |  false   |   `"true"`   |                               Enable/disable image pull                                |
|                                  <a name="input_push"></a>[push](#input_push)                                  | string |  false   |   `"true"`   |                               Enable/disable image push                                |
|                            <a name="input_registry"></a>[registry](#input_registry)                            | string |   true   |              |                                    Docker registry                                     |
|              <a name="input_registry-password"></a>[registry-password](#input_registry-password)               | string |  false   |              |                        The password to access the <br>registry                         |
|              <a name="input_registry-username"></a>[registry-username](#input_registry-username)               | string |  false   |              |                        The username to access the <br>registry                         |
|                             <a name="input_secrets"></a>[secrets](#input_secrets)                              | string |  false   |              | List of secrets to expose <br>to the build (e.g., key=string, GIT\_AUTH\_TOKEN=mytoken)  |
|                 <a name="input_service-account"></a>[service-account](#input_service-account)                  | string |  false   |              |                     The GCP service account trusting <br>the OIDC                      |
|                                   <a name="input_tag"></a>[tag](#input_tag)                                    | string |   true   |              |                                  The tag of the image                                  |
|                         <a name="input_tag-latest"></a>[tag-latest](#input_tag-latest)                         | string |  false   |              |                            If true add the tag <br>latest                              |
|                         <a name="input_tag-length"></a>[tag-length](#input_tag-length)                         | string |  false   |    `"7"`     |        The number of chars composing <br>the tag from the short <br>commit sha         |
|                               <a name="input_target"></a>[target](#input_target)                               | string |  false   |              |                         The target to build in <br>the image                           |
|                         <a name="input_trivy-scan"></a>[trivy-scan](#input_trivy-scan)                         | string |  false   |  `"false"`   |             Run Trivy vulnerability scanner before <br>pushing the image               |
| <a name="input_workload-identity-provider"></a>[workload-identity-provider](#input_workload-identity-provider) | string |  false   |              |            The GCP workload identity provider <br>to login to the registry             |

<!-- AUTO-DOC-INPUT:END -->

## Outputs

<!-- AUTO-DOC-OUTPUT:START - Do not remove or modify this section -->

|                            OUTPUT                             |  TYPE  |      DESCRIPTION      |
|---------------------------------------------------------------|--------|-----------------------|
|     <a name="output_digest"></a>[digest](#output_digest)      | string |     Image digest      |
|    <a name="output_imageid"></a>[imageid](#output_imageid)    | string |       Image ID        |
| <a name="output_imagetags"></a>[imagetags](#output_imagetags) | string |     Generated tag     |
|  <a name="output_metadata"></a>[metadata](#output_metadata)   | string | Build result metadata |

<!-- AUTO-DOC-OUTPUT:END -->
