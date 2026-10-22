| # | Källa | Destination | Protokoll / Port | Åtgärd | Kommentar |
|---|-------|-------------|------------------|--------|-----------|
| 1 | Klientzon (10.40.50.0/24) | Webbserver (10.40.10.10) | HTTPS, TCP 443 | Tillåt | Användare når webbtjänsten |
| 2 | Klientzon (10.40.50.0/24) | Jump-server (10.40.40.10) | SSH TCP 22 / RDP TCP 3389 | Tillåt | Endast behöriga administratörer |
| 3 | Klientzon (10.40.50.0/24) | Applikationsserver (10.40.20.10) | Alla | Blockera | Ingen direktåtkomst |
| 4 | Klientzon (10.40.50.0/24) | Kunddatabas (10.40.30.10) | Alla | Blockera | Ingen direktåtkomst |
| 5 | Webbserver (10.40.10.10) | Applikationsserver (10.40.20.10) | Godkänd applikationsport | Tillåt | Endast nödvändig applikationstrafik |
| 6 | Applikationsserver (10.40.20.10) | Kunddatabas (10.40.30.10) | Databasport | Tillåt | Enda tillåtna källan till databasen | 
| 7 | Jump-server (10.40.40.10) | Hanterade servrar | SSH TCP 22 / RDP TCP 3389 | Tillåt | Endast nödvändiga portar |
| 8 | Hanterade servrar | Loggserver (10.40.40.20) | Loggtrafik (t.ex. syslog 514) | Tillåt | Central loggning |
| 9 | Alla | Alla | Alla | Blockera | Standardregel: allt som inte uttryckligen tillåts nekas |