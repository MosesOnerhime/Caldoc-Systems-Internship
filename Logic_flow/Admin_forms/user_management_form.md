```mermaid
---
config:
  theme: redux
---
flowchart TD
 subgraph s1["User Management Form"]
    A[Admin Opens User Management] --> B[Fetch User List via API]
    B --> C{Load Success?}
    C -->|No| D[Show Error + Retry]
    D --> B
    C -->|Yes| E[Display User Table]
    
    E --> F["Columns:<br>• Name<br>• Email<br>• Status<br>• Last Active"]
    E --> G["Controls:<br>• Search<br>• Filter<br>• Sort"]
    
    G --> H{Admin Action?}
    H -->|Search| I[Query Users via API]
    H -->|Filter| J[Apply Filters via API]
    H -->|Sort| K[Reorder via API]
    
    E --> L{Row Actions?}
    L -->|View| M[Get Full Profile via API]
    L -->|Edit| N[Load Edit Form via API]
    L -->|Ban/Unban| O[Toggle Status via API]
    L -->|Impersonate| P[Generate Token via API]
    
    M --> Q[Show Modal with:<br>• Activity Log<br>• Certificates<br>• Payments]
    N --> R[Display Form with:<br>• Current Values<br>• Validation Rules]
    R --> S{Submit?}
    S -->|Yes| T[Update User via API]
    S -->|No| U[Discard Changes]
    
    O --> V{Confirm?}
    V -->|Yes| W[Send Ban/Unban via API]
    V -->|No| X[Cancel]
    
    P --> Y[Log Impersonation via API]
    Y --> Z[Redirect as User]
    
    T --> AA[Refresh User List]
    W --> AA
    I --> AA
    J --> AA
    K --> AA
  end
