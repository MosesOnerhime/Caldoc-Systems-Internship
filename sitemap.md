```mermaid
flowchart TD
 subgraph s1["Sitemap"]
        B["Registration"]
        C["Login"]
        A["Landing Page"]
        D["Client Dashboard"]
        E["Training Modules"]
        F["Certificate Purchase"]
        G["Profile Settings"]
        I["User Management"]
        J["Content Management"]
        K["Payment Reports"]
        H["Admin Dashboard"]
  end
    A --> B & C
    C --> D & H
    D --> E & F & G
    H --> I & J & K
    B --> C