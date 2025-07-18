```mermaid
---
config:
  theme: redux
---
flowchart TD
 subgraph s1["Training Progress form"]
        A[User Opens Progress Page] --> B[Get progress data from API]
    B --> C[Show loading state]
    C -->|Success| D[Check completion via API]
    D -->|Incomplete| E[Display progress charts]
    D -->|Complete| F[Show certificate options]
    
    E --> G["Circular Chart: Get % from API"]
    E --> H["Module Bars: Fetch details from API"]
    E --> I["Time Graph: Get analytics from API"]
    
    G --> J{User clicks segment?}
    J -->|Yes| K[Load module details from API]
    
    H --> L{User hovers bar?}
    L -->|Yes| M[Get tooltip data from API]
    
    I --> N{User clicks point?}
    N -->|Yes| O[Compare with cohort via API]
    
    K --> P[Show module metrics from API]
    P --> Q{Continue learning?}
    Q -->|Yes| R[Get last lesson from API]
    
    F --> S{User purchases?}
    S -->|Yes| T[Initiate payment via API]
    S -->|No| U[Keep displaying]
    
    T -->|Success| V[Generate cert via API]
    T -->|Failed| W[Get error from API]
    V --> X[Download certificate from API]
  end
    