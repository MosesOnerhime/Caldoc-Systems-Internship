```mermaid
---
config:
  theme: redux
---
flowchart TD
 subgraph s1["Admin Dashboard Form"]
    A[Admin Logs In] --> B[Verify Admin Privileges via API]
    B --> C{Valid Admin?}
    C -->|No| D[Redirect to Login]
    C -->|Yes| E[Load Dashboard from API]
    
    E --> F["1.User Management"]
    E --> G["2.Content Management"]
    E --> H["3.Analytics"]
    E --> I["4.System Settings"]
    
    F --> J{Admin Action?}
    J -->|Search Users| K[Fetch Users via API]
    J -->|Edit User| L[Get User Details via API]
    J -->|Ban User| M[Update Status via API]
    
    G --> N{Content Action?}
    N -->|Upload Material| O[Post Content via API]
    N -->|Remove Content| P[Delete via API]
    N -->|Update Course| Q[Patch via API]
    
    H --> R{Report Type?}
    R -->|User Growth| S[Fetch Metrics via API]
    R -->|Course Stats| T[Get Analytics via API]
    R -->|Revenue| U[Pull Payment Data via API]
    
    I --> V{Setting Changed?}
    V -->|Email Config| W[Update SMTP via API]
    V -->|Password Policy| X[Modify Rules via API]
    V -->|API Keys| Y[Rotate Keys via API]
    
    K --> Z[Display Paginated Results]
    L --> AA[Show Edit Form]
    M --> AB[Confirm Action]
    O --> AC[Validate & Store]
    P --> AD[Confirm Deletion]
    Q --> AE[Preview Changes]
    
    AB -->|Confirm| AF[Log Action via API]
    AD -->|Confirm| AG[Purge from CDN]
    AE -->|Save| AH[Update Database via API]
    
    S --> AI[Render Charts]
    T --> AJ[Generate Reports]
    U --> AK[Export CSV via API]
    
    W --> AL[Test Connection]
    X --> AM[Enforce Policy]
    Y --> AN[Notify Services]
  end
