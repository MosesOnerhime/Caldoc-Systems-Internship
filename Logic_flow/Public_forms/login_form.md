```mermaid
---
config:
  theme: redux
  layout: dagre
---
flowchart TD
 subgraph s1["Login Form"]
    A[User Visits Login] --> B[Check session via API]
    B -->|Logged In| C[Redirect to dashboard]
    B -->|Not Logged In| D[Display form]
    
    D --> E{User submits?}
    E -->|Yes| F[Validate inputs client-side]
    F -->|Invalid| G[Show errors]
    F -->|Valid| H[Send credentials to API]
    
    H --> I[Verify credentials via API]
    I -->|Invalid Email| J[Get error from API]
    I -->|Wrong Password| K[Track attempt via API]
    K --> L{Attempts ≥5?}
    L -->|Yes| M[Lock account via API + Send reset via API]
    L -->|No| N[Get error from API]
    
    I -->|Unverified| O[Get verification status from API]
    O --> P[Show resend option from API]
    
    I -->|Valid| Q[Create session via API]
    Q --> R[Redirect to dashboard]
    
    D --> S{User clicks forgot password?}
    S -->|Yes| T[Get reset form from API]
    T --> U[Submit email to API]
    U --> V{Email exists?}
    V -->|Yes| W[Send reset link via API]
    V -->|No| X[Get error from API]
  end
