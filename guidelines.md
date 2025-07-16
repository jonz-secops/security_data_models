# Guidelines for the Project

### Contributing

```mermaid

flowchart LR
    %% ───── Branches (subgraphs make swim-lanes) ─────
    subgraph FEATURE_BRANCH ["feature/*"]
        direction TB
        F1["commit<br/>`feature: add-widget`"]
        F2["commit<br/>`feature: update-api`"]
    end

    subgraph SECURITY_BRANCH ["security/*"]
        direction TB
        S1["commit<br/>`security: patch-CVE`"]
    end

    subgraph FIX_BRANCH ["fix/*"]
        direction TB
        X1["commit<br/>`fix: null-ptr`"]
    end

    subgraph RELEASE_BRANCH ["release"]
        direction TB
        R0["merge&nbsp;feature/*&nbsp;+&nbsp;fix/*"]
        R1["commit<br/>`release: bump-version`"]
    end

    subgraph MASTER_BRANCH ["master (prod)"]
        direction TB
        M1["deploy tag<br/>`v1.2.0`"]
    end

    %% ───── Flows ─────
    F2  -- PR -->  R0
    S1  -- PR -->  X1
    X1  -- PR -->  R0
    R1  -- merge --> M1

```
