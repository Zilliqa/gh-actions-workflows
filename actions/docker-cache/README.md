# Docker cache GitHub Action

## Inputs

<!-- AUTO-DOC-INPUT:START - Do not remove or modify this section -->

<<<<<<< HEAD
|  INPUT   |  TYPE  | REQUIRED |                DEFAULT                |                 DESCRIPTION                 |
|----------|--------|----------|---------------------------------------|---------------------------------------------|
|  bucket  | string |  false   | `"298213327629-github-actions-cache"` | The AWS bucket where is hosted<br>the cache |
|   key    | string |   true   |                                       |     The key to store/retrieve the cache     |
| password | string |  false   |                                       |      The password to access the cache       |
|  region  | string |  false   |             `"us-west-2"`             | The AWS region where is hosted<br>the cache |
|   type   | string |   true   |                `"gha"`                |     The password to access the registry     |
| username | string |  false   |                                       |      The username to access the cache       |
=======
| INPUT |  TYPE  | REQUIRED | DEFAULT |             DESCRIPTION             |
|-------|--------|----------|---------|-------------------------------------|
|  key  | string |   true   |         | The key to store/retrieve the cache |
>>>>>>> d23892b (feat: add auto-doc action to document the private actions (#18))

<!-- AUTO-DOC-INPUT:END -->

## Outputs
<<<<<<< HEAD
=======

<!-- AUTO-DOC-OUTPUT:START - Do not remove or modify this section -->

|  OUTPUT   |  TYPE  |          DESCRIPTION           |
|-----------|--------|--------------------------------|
| cachefrom | string | Docker layers Cache from value |
|  cacheto  | string |  Docker layers Cache to value  |

<!-- AUTO-DOC-OUTPUT:END -->
>>>>>>> d23892b (feat: add auto-doc action to document the private actions (#18))
