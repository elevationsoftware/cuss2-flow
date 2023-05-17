# CUSS 2.0.2 Flow

This document explains the different steps required to communicate with a CUSS 2.0.2 complaint platform, including but not limited to all the available devices 

## Authentication Diagram

```mermaid
sequenceDiagram
    participant CUSS App
    participant OAuth Server
    CUSS App->>OAuth Server: 1. Request Access Token
    loop 
        OAuth Server->>OAuth Server: 2. Verify Client
    end
    OAuth Server->>CUSS App: 3. Return Access Token
    CUSS App->>CUSS Platform: 4. Send Access Token
    CUSS Platform->>OAuth Server: 5. Validate Token
    OAuth Server->>CUSS Platform: 6. Valid Token
    Note right of CUSS Platform: Handling expired<br/>tokens
    CUSS Platform->>CUSS App: 7. Protected Payload
    CUSS App->>CUSS Platform: 8. Send Expired Token
    CUSS Platform->>CUSS App: 9. Invalid Token Response
    CUSS App->>OAuth Server: 10. Request New Access Token
    OAuth Server->>CUSS App: 11. Return Access Token
```
