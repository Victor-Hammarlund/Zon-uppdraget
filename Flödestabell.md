| # | Källa | Riktning | Destination | Port | Åtgärd | Filtreras var | Motivering |
|---|-------|:--------:|-------------|------|--------|---------------|------------|
| 1 | Klientzon | → | Webbserver | TCP 443 (HTTPS) | ✅ Tillåt | Brandvägg, klientzon | Användarna behöver använda webbtjänsten |
| 2 | Klientzon | → | Jump-server | TCP 22 / 3389 | ✅ Tillåt | Brandvägg, klientzon | Admins behöver logga in för att förvalta servrarna |
| 3 | Klientzon | ⛔ | Applikationsserver | Alla | ❌ Blockera | Brandvägg, klientzon | Inget behov, klienter går via webbservern |
| 4 | Klientzon | ⛔ | Kunddatabas | Alla | ❌ Blockera | Brandvägg, klientzon | Inget behov, data hämtas via applikationen |
| 5 | Webbserver | → | Applikationsserver | Applikationsport | ✅ Tillåt | Brandvägg, DMZ | Webbservern skickar användarnas förfrågningar till applikationen |
| 6 | Applikationsserver | → | Kunddatabas | Databasport | ✅ Tillåt | Brandvägg, applikationszon | Applikationen behöver läsa och spara kunddata |
| 7 | Jump-server | → | Hanterade servrar | TCP 22 / 3389 | ✅ Tillåt | Brandvägg, driftzon | Servrarna behöver uppdateras och underhållas |
| 8 | Hanterade servrar | → | Loggserver | Syslog 514 | ✅ Tillåt | Brandvägg, källzon | Händelser måste loggas för felsökning och incidentutredning |
| 9 | Alla | ⛔ | Alla | Alla | ❌ Blockera | Brandvägg, alla zoner | Inget behov, all övrig trafik nekas |

**→** = tillåten riktning (svar tillåts tillbaka) · **⛔** = blockeras