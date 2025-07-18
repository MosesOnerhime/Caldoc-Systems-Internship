```mermaid
---
config:
  theme: redux
---
flowchart TD
  subgraph s1["Certificate Purchase Page"]
    A[User Requests Certificate] --> B[Get certificate template from API]
    B --> C[Display purchase options]
    
    C --> D{User selects payment method?}
    D -->|Bank Transfer| E[Generate transaction reference via API]
    E --> F[Set up payment webhook via API]
    F --> G[Show bank details from API]
    
    D -->|Card Payment| H[Initialize payment gateway via API]
    
    G --> I{Payment detected via API?}
    I -->|Yes| J[Verify payment via API]
    I -->|No| K[Check timeout via API]
    
    H --> L{3D Secure completed?}
    L -->|Yes| M[Process payment via API]
    L -->|No| N[Handle failure via API]
    
    J -->|Valid| O[Confirm payment via API]
    J -->|Invalid| P[Flag discrepancy via API]
    
    O --> Q[Generate certificate via API]
    Q --> R[Download PDF from API]
    R --> S[Send email via API]
    
    M --> Q
    N --> T[Retry payment via API]
  end
