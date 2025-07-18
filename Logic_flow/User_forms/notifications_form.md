```mermaid
---
config:
  theme: redux
---
flowchart TD
 subgraph s1["Notifications Form"]
    A[User Opens Notifications] --> B[Fetch notifications from API]
    B --> C{Load Success?}
    C -->|No| D[Show Error + Retry Button]
    D -->|Retry| B
    C -->|Yes| E[Display Notifications]
    E --> F["1.Unread (Highlighted)"]
    E --> G["2.Read (Normal)"]
    E --> H["3.Group by Type:<br>- System<br>- Course<br>- Certificate"]
    
    F --> I{User clicks notification?}
    I -->|Yes| J[Mark as read via API]
    J --> K[Load related content from API]
    K --> L[Open relevant page]
    
    G --> M{User clicks notification?}
    M -->|Yes| K
    
    H --> N{User filters?}
    N -->|Yes| O[Fetch filtered list from API]
    O --> E
    
    A --> P{New push notification?}
    P -->|Yes| Q[Add to top via WebSocket]
    Q --> E
    
    E --> R{User clears all?}
    R -->|Yes| S[Send bulk delete to API]
    S --> T[Refresh list from API]
  end
