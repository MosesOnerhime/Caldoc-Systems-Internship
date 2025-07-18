```mermaid
flowchart TD
 subgraph s1["Training Module Form"]
    A[User Opens Module] --> B[Check prerequisites via API]
    B -->|No| C[Get incomplete modules from API]
    B -->|Yes| D[Load content from API]
    
    D --> E[Display Module]
    E --> F["Video: Get stream URL from API"]
    E --> G["PDF: Get download link from API"]
    E --> H["Quiz: Load questions from API"]
    
    F --> I{User watches?}
    I -->|Yes| J[Send progress updates to API every 5s]
    
    G --> K{User interacts?}
    K -->|Zoom/Download| L[Request permissions from API]
    
    H --> M{User starts quiz?}
    M -->|Yes| N[Submit answers to API]
    N --> O[Get scoring results from API]
    O --> P{Passed?}
    P -->|Yes| Q[Send completion to API]
    P -->|No| R[Check retry count via API]
    R -->|Under limit| M
    R -->|Limit reached| S[Lock module via API]
    
    Q --> T[Get next module from API]
  end


