```mermaid
---
config:
  theme: redux
---
flowchart TD
 subgraph s1["Password Reset Form"]
    A[User Accesses Reset Page] --> B[Display Reset Form]
    B --> C{User Submits Email?}
    C -->|No| D[Show Form Validation Error]
    C -->|Yes| E[Verify Email via API]
    
    E --> F{Email Registered?}
    F -->|No| G['Show Email Not Found Error']
    F -->|Yes| H[Generate Token via API]
    H --> I[Send Reset Link via API]
    I --> J[Show Success Message]
    
    J --> K{User Clicks Link?}
    K -->|Yes| L[Validate Token via API]
    L --> M{Token Valid?}
    M -->|No| N[Show 'Invalid Link' Error]
    M -->|Yes| O[Display Password Form]
    
    O --> P{User Submits New Password?}
    P -->|No| Q[Show Validation Errors]
    P -->|Yes| R[Validate Strength via API]
    R --> S{Meets Policy?}
    S -->|No| T[Show Password Rules]
    S -->|Yes| U[Update Password via API]
    
    U --> V{Success?}
    V -->|No| W[Show 'Update Failed' Error]
    V -->|Yes| X[Invalidate Token via API]
    X --> Y[Auto-Login via API]
    Y --> Z[Redirect to Dashboard]
  end
