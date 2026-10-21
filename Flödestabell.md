| Rad | Källzon | Målzon | Protokoll | Port | Riktning | Motivering (verksamhetsfunktion) | Filtreras var (molnplattform/värd) |
|---:|---|---|---|---|---|---|---|
| 1 | Klientzon `10.20.50.0/24` | Webbserver `10.20.10.10` | TCP | 443 | → | Klienter måste kunna nå webbservern. | Molnplattformens brandvägg |
| 2 | Klientzon `10.20.50.0/24` | Jump-server | SSH | 22 | → | Administratörer på klientsidan behöver kunna nå jump-servern för administration. | Molnplattformens brandvägg samt konfiguration av användargrupper |
| 3 | DMZ `10.20.10.0/24` | Applikationsserver `10.20.20.10` | Applikationsprotokoll | Endast godkänd port | → | Nödvändig applikationstrafik. | Molnplattformens brandvägg |
| 4 | Applikationszon `10.20.20.10` | Kunddatabas `10.20.30.10` | TCP | Fastställs av databastyp | → | Applikationszonen behöver tillgång till kunddata. | Molnplattformens brandvägg och/eller värdbrandvägg |
| 5 | Drift- och förvaltningszon, jump-server `10.20.40.10` | Alla hanterade servrar | SSH | 22 | → | Administratörer måste kunna administrera servrar. | Molnplattformens brandvägg och/eller värdbrandvägg |
| 6 | Alla | Drift- och förvaltningszon, loggserver `10.20.40.20` | Syslog UDP/TCP | 514 | ← | Loggar måste analyseras och sparas. | Molnplattformens brandvägg och/eller värdbrandvägg |
| 7 | Alla | Alla | Alla | Alla | ↔ | All trafik som inte uttryckligen tillåts i reglerna ovan ska blockeras. | Molnplattformens brandvägg och/eller värdbrandvägg |