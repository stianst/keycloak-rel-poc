# Keycloak release workflows

This repository contains workflows for releasing Keycloak, including:

* Feature releases
* Patch releases
* Nightly releases

## Feature release

Keycloak doesn't currently leverage the `minor` component in [Semantic Versioning](https://semver.org/), but rather always bumps the `major` version.

To prepare for a new feature release the first step is to prepare release branches. This will be done through a workflow that creates release branches for all repositories.

```mermaid
sequenceDiagram
    participant main
    participant branch1 as 18.0
    participant tag1 as 18.0.0
    participant tag2 as 18.0.1
    participant branch2 as 19.0
    participant tag3 as 19.0.0
    main->>branch1: Create release branch
    branch1->>tag1: Create release tag
    loop
      main->>branch1: Cherry-pick commit
    end
    branch1->>tag2: Create release tag
    main->>branch2: Create release branch
    branch2->>tag3: Create release tag
    loop
      main->>branch2: Cherry-pick commit
    end
```
