```mermaid
---
config:
  theme: redux
---
flowchart TD
 subgraph s1["Certificate Verification Form"]
    A[User Opens Verification] --> B{Input Method?}
    B -->|Certificate ID| C[Send code to API for validation]
    B -->|QR Code| D[Decode and send to API]
    
    C --> E[Validate format via API]
    D --> E
    
    E -->|Invalid| F[Get error from API]
    E -->|Valid| G[Query certificate via API]
    
    G -->|Not Found| H[Get 'not found' from API]
    G -->|Found| I[Check status via API]
    
    I -->|Invalid| J[Get reason from API]
    I -->|Valid| K[Display verification from API]
    
    K --> L["Show:<br>- Name from API<br>- Date from API<br>- Course from API<br>- ID from API"]
    
    A --> M{New verification?}
    M -->|Yes| A
 end
