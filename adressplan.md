## Adressplan

**Uppdragsgivarens adressutrymme:** `10.40.0.0/16`

### DMZ
- Subnät: `10.40.10.0/24`
- Gateway: `10.40.10.1`
- Webbserver: `10.40.10.10`

### Applikationszon
- Subnät: `10.40.20.0/24`
- Gateway: `10.40.20.1`
- Applikationsserver: `10.40.20.10`

### Datazon
- Subnät: `10.40.30.0/24`
- Gateway: `10.40.30.1`
- Kunddatabas: `10.40.30.10`

### Drift- och förvaltningszon
- Subnät: `10.40.40.0/24`
- Gateway: `10.40.40.1`
- Jump-server: `10.40.40.10`
- Loggserver: `10.40.40.20`

### Klientzon
- Subnät: `10.40.50.0/24`
- Gateway: `10.40.50.1`
- Klientdatorer: `10.40.50.10–10.40.50.254`
