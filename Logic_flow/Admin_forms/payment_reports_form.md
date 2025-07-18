```mermaid
---
config:
  theme: redux
---
flowchart TD
 subgraph s1["Payment Reports Form"]
    A[Admin Opens Reports] --> B[Fetch Payment Data via API]
    B --> C{Load Success?}
    C -->|No| D[Show Error + Retry]
    D --> B
    C -->|Yes| E[Display Payment Dashboard]

    E --> F["Columns:<br>• Transaction ID<br>• User<br>• Amount (₦)<br>• Date<br>• Status<br>• Certificate Linked"]
    E --> G["Filters:<br>• Date Range<br>• Payment Method<br>• Status<br>• Amount Range"]

    G --> H{Admin Action?}
    H -->|Search| I[Query Payments via API]
    H -->|Filter| J[Apply Filters via API]
    H -->|Export| K[Generate CSV via API]

    E --> L{Row Actions?}
    L -->|View Details| M[Get Full Receipt via API]
    L -->|Refund| N[Initiate Refund Flow]
    L -->|Flag Fraud| O[Mark Suspicious via API]

    M --> P["Modal Shows:<br>• User Details<br>• Payment Gateway Data<br>• Certificate Info<br>• IP/Location"]
    N --> Q{Confirm Refund?}
    Q -->|Yes| R[Process Refund via API]
    Q -->|No| S[Cancel]
    O --> T["Fraud Report:<br>• Reason<br>• Evidence<br>• Notify Security"]

    R --> U[Update Transaction Status]
    U --> V[Notify User via API]
    T --> W[Freeze Account if Needed]

    I --> X[Refresh Table]
    J --> X
    K --> Y[Download CSV File]
    R --> X
    O --> X

    E --> Z["Analytics:<br>• Daily Revenue<br>• Method Distribution<br>• Failed Transactions"]
    Z --> AA[Fetch Analytics via API]
    AA --> BB[Render Charts]
  end
