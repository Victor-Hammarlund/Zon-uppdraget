# Lateral nätverksöversikt

Detta är en provisorisk kartläggning.

Översikten visar vilka system som får kommunicera med varandra enligt ett exempel på en restriktiv brandväggsdesign.

## Översikt över nätverkszonerna

```text
┌──────────────────────────────────────────────┐
│ KLIENTZON                                    │
│ Subnät: 10.20.50.0/24                        │
│ Klientdatorer: 10.20.50.10–10.20.50.254      │
└──────────────────────────────────────────────┘
          │
          ├── HTTPS (TCP 443) ────────────────► Webbserver
          │
          ├── SSH/RDP ────────────────────────► Jump-server
          │   (endast behöriga administratörer)
          │
          └── BLOCKERAS ──────────────────────► Kunddatabas
                                                Applikationsserver


┌──────────────────────────────────────────────┐
│ DMZ                                          │
│ Subnät: 10.20.10.0/24                        │
│ Gateway: 10.20.10.1                          │
│ Webbserver: 10.20.10.10                      │
└──────────────────────────────────────────────┘
          │
          └── Nödvändig applikationstrafik ───► Applikationsserver
              (endast godkänd port)


┌──────────────────────────────────────────────┐
│ APPLIKATIONSZON                              │
│ Subnät: 10.20.20.0/24                        │
│ Gateway: 10.20.20.1                          │
│ Applikationsserver: 10.20.20.10              │
└──────────────────────────────────────────────┘
          │
          └── Databasanslutning ──────────────► Kunddatabas
              (endast nödvändig databasport)


┌──────────────────────────────────────────────┐
│ DATAZON                                      │
│ Subnät: 10.20.30.0/24                        │
│ Gateway: 10.20.30.1                          │
│ Kunddatabas: 10.20.30.10                     │
└──────────────────────────────────────────────┘
          ▲
          │
          └── Tillåten anslutning endast från
              applikationsservern


┌──────────────────────────────────────────────┐
│ DRIFT- OCH FÖRVALTNINGSZON                   │
│ Subnät: 10.20.40.0/24                        │
│ Gateway: 10.20.40.1                          │
│ Jump-server: 10.20.40.10                     │
│ Loggserver: 10.20.40.20                      │
└──────────────────────────────────────────────┘
          │
          ├── SSH/RDP ────────────────────────► Hanterade servrar
          │   (endast nödvändiga portar)
          │
          └── Log