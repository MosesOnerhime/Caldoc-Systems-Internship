```mermaid
---
config:
  theme: redux
---
flowchart TD
 subgraph s1["User Dashboard Form"]
    A[User Logs In] --> B[Check if it is user's first login via API]
    B -->|Yes| C[Get onboarding data from API]
    B -->|No| D[Load dashboard from API]
    
    D --> E[Fetch user progress via API]
    E --> F[Display progress from API]
    F --> G["1.Progress: Get % from API"]
    F --> H["2.Trainings: Get active from API"]
    F --> I["3.Notifications: Get unread from API"]
    F --> J["4.Certificates: Get status from API"]
    
    G --> K{User clicks progress?}
    K -->|Yes| L[Get detailed progress from API]
    
    H --> M{User selects training?}
    M -->|Yes| N[Load module from API]
    
    I --> O{User clicks notification?}
    O -->|Yes| P[Mark read via API + Get context from API]
    
    J --> Q{User clicks certificate?}
    Q -->|Available| R[Get download link from API]
    Q -->|Pending| S[Initiate payment via API]
    
    D --> T[User actions]
    T --> U[Edit profile via API]
    T --> V[Logout via API]
  end
