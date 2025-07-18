```mermaid
---
config:
  theme: redux
---
flowchart TD
 subgraph s1["Content Management Form"]
    A[Admin Opens CMS] --> B[Fetch Content List via API]
    B --> C{Load Success?}
    C -->|No| D[Show Error + Retry]
    D --> B
    C -->|Yes| E[Display Content Dashboard]
    
    E --> F["Sections:<br>• Courses<br>• Videos<br>• Documents<br>• Certificates"]
    E --> G["Tools:<br>• Search<br>• Filter by Type<br>• Sort by Date"]
    
    G --> H{Admin Action?}
    H -->|Upload| I[Initiate Upload via API]
    H -->|Edit| J[Fetch Content Meta via API]
    H -->|Delete| K[Confirm Deletion]
    
    I --> L["Upload Form:<br>• Title/Description<br>• File (PDF/MP4/ZIP)<br>• Thumbnail<br>• Tags"]
    L --> M{Validate?}
    M -->|Valid| N[Upload to CDN via API]
    M -->|Invalid| O[Show Errors]
    N --> P[Create DB Entry via API]
    
    J --> Q["Edit Form:<br>• Metadata<br>• Status (Draft/Published)<br>• Version Control"]
    Q --> R{Submit?}
    R -->|Yes| S[Update via API]
    R -->|No| T[Discard Changes]
    
    K --> U{Confirm?}
    U -->|Yes| V[Delete from CDN+DB via API]
    U -->|No| W[Cancel]
    
    P --> X[Refresh List]
    S --> X
    V --> X
    
    X --> Y[Update Audit Log via API]
    
    E --> Z["Bulk Actions:<br>• Publish All<br>• Archive Old<br>• Rebuild Index"]
    Z --> AA[Confirm Bulk Operation]
    AA --> AB[Process via Background Job API]
    AB --> AC[Notify Completion via Webhook]
  end
