```mermaid
---
config:
  theme: redux
---
flowchart TD
 subgraph s1["Profile Settings Form"]
    A[User Opens Profile] --> B[Get profile data from API]
    B --> C[Show profile sections]
    
    C --> D["Basic Info Section"]
    D --> E{User edits info?}
    E -->|Yes| F[Send updated data to API]
    E -->|No| G[Keep displaying]
    
    C --> H["Password Section"]
    H --> I{User changes password?}
    I -->|Yes| J[Verify current password with API]
    J --> K[Send new password to API]
    
    C --> L["Notifications Section"]
    L --> M{User toggles settings?}
    M -->|Yes| N[Send preference changes to API]
    
    C --> O["Delete Account"]
    O --> P{User confirms?}
    P -->|Yes| Q[Send verification to API]
    Q --> R[Send delete request to API]
  end
