```mermaid
graph TD;
  A[Dockerfile] -->|Build| B[Image]
  B -->|Run| C[Container]
  C -->|Persists Data| D[Volume]
  C -->|Connects to| E[Network]
  B -->|Push/Pull| F[Docker Hub or Private Registry]
  F -->|Stores| B
  C -->|Communicates via| G[Docker Daemon]
  G -->|Manages| B & C

  subgraph Docker_Compose
    H[Docker Compose Config]
    H -->|Defines Services| C
    H -->|Manages Multiple Containers| I[Multi-Container App]
    I -->|Database| J[PostgreSQL Container]
    J -->|Stores Data| D
  end

  J -->|Connects to| E

  subgraph Docker_Engine
    K[Docker CLI] -->|Sends Commands| L[Docker REST API]
    L -->|Communicates with| G
  end

  style L fill:#ffcc00,stroke:#333,stroke-width:2px;
