# Docker cache GitHub Action

## Inputs

<!-- AUTO-DOC-INPUT:START - Do not remove or modify this section -->

|  INPUT  |  TYPE  | REQUIRED | DEFAULT |                                 DESCRIPTION                                 |
|---------|--------|----------|---------|-----------------------------------------------------------------------------|
| backend | string |  false   | `"gha"` |                The cache storage backend for <br>the cache                  |
|   key   | string |   true   |         | The key to store/retrieve the <br>cache or the Docker cache <br>repository  |

<!-- AUTO-DOC-INPUT:END -->

## Outputs

<!-- AUTO-DOC-OUTPUT:START - Do not remove or modify this section -->

|      OUTPUT       |  TYPE  |                   DESCRIPTION                    |
|-------------------|--------|--------------------------------------------------|
|     cachefrom     | string |          Docker layers Cache from value          |
| cachefromfallback | string | Docker layers Cache from fallback <br>tag value  |
|      cacheto      | string |           Docker layers Cache to value           |

<!-- AUTO-DOC-OUTPUT:END -->
