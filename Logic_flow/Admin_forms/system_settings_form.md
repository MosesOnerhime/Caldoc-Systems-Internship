```mermaid
---
config:
  theme: redux
---
flowchart TD
 subgraph s1["System Settings Form"]
    A[Admin Opens Settings] --> B[Load Configurations via API]
    B --> C{Load Success?}
    C -->|No| D[Show Error + Retry]
    D --> B
    C -->|Yes| E[Display Settings Dashboard]

    E --> F["Sections:<br>• Security<br>• Payment<br>• Notifications<br>• System<br>• API Keys"]
    
    F --> G{Admin Edits?}
    G -->|Security| H["Password Policies:<br>• Min Length<br>• Complexity<br>• Expiry"]
    G -->|Payment| I["Gateway Config:<br>• API Keys<br>• Webhooks<br>• Currency"]
    G -->|Notifications| J["Templates:<br>• Email<br>• SMS<br>• Push"]
    G -->|System| K["Maintenance:<br>• Mode Toggle<br>• Backups<br>• Logs"]
    G -->|API Keys| L["Key Rotation:<br>• Generate<br>• Revoke<br>• History"]

    H --> M{Save?}
    M -->|Yes| N[Update Security via API]
    M -->|No| O[Reset Form]
    
    I --> P{Test Connection?}
    P -->|Yes| Q[Validate Gateway via API]
    P -->|No| R[Save Payment Config via API]
    
    J --> S{Preview?}
    S -->|Yes| T[Render Template via API]
    S -->|No| U[Update Templates via API]
    
    K --> V{Execute Action?}
    V -->|Backup| W[Trigger Backup via API]
    V -->|Maintenance| X[Toggle Mode via API]
    
    L --> Y{Rotate Key?}
    Y -->|Yes| Z[Generate New Key via API]
    Y -->|No| AA[View Current Key]

    N --> AB[Audit Log Change]
    R --> AB
    U --> AB
    X --> AB
    Z --> AC[Notify Services via Webhook]
    AC --> AB

    AB --> AD[Confirm Update]
    AD --> E
  end
