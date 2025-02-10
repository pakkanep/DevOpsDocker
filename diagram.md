```mermaid
graph TD;
  A[Dockerfile] -->|Build| B[Image]
  B -->|Run| C[Container]
  C -->|Persists Data| D[Volume]
  C -->|Connects to| E[Network]
  B -->|Push/Pull| F[Docker Hub/Registry]
  F -->|Stores| B
  C -->|Communicates via| G[Docker Daemon]
  G -->|Manages| B & C

  subgraph "Docker Compose"
    H[Docker Compose docker-compose.yml]
    H -->|Defines Services| C
    H -->|Manages Multiple Containers| I[Multi-Container App]
    I -->|Database| J[PostgreSQL Container]
    J -->|Stores Data| D
  end

  J -->|Connects to| E
