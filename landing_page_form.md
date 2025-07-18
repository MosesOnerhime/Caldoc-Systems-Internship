```mermaid
---
config:
  theme: redux
---
flowchart TD
 subgraph s1["Landing Page Form"]
        A[User Visits Site] --> B[Check auth status via API]
    B -->|Logged In| C[Redirect to dashboard]
    B -->|Guest| D[Load landing page content from API]
    
    D --> E["Display:<br>- Hero content from API<br>- Features from API<br>- CTAs from API"]
    
    E --> F{User clicks action?}
    F -->|Register| G[Get registration form from API]
    F -->|Login| H[Get login form from API]
    F -->|Verify| I[Initiate verification via API]
    
    I --> J[Submit certificate ID to API]
    J --> K{Valid via API?}
    K -->|Yes| L[Show certificate details from API]
    K -->|No| M[Get error from API]
    
    D --> N["Load static sections from API:<br>- About Us<br>- FAQ<br>- Contact"]
  end
