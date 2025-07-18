```mermaid
flowchart TD
 subgraph s1["Registration Form"]
    A[Start Registration] --> B[Get registration form from API]
    B --> C[User submits data]
    C --> D[Validate email via API]
    D -->|Invalid| E[Get error from API]
    D -->|Valid| F[Check email uniqueness via API]
    
    F -->|Exists| G[Get error from API]
    F -->|Available| H[Validate password via API]
    
    H -->|Weak| I[Get rules from API]
    H -->|Strong| J[Create account via API]
    
    J --> K[Send verification via API]
    K --> L[Show message from API]
    
    L --> M{User clicks link?}
    M -->|Yes| N[Activate via API]
    N --> O[Redirect to login]
    M -->|No| P[Expire link via API]
  end


