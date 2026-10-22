|- **DMZ**
  - Subnät: `10.20.10.0/24`
  - Gateway: `10.20.10.1`
  - Webbserver: `10.20.10.10`
  
- **Applikationszon**
  - Subnät: `10.20.20.0/24`
  - Gateway: `10.20.20.1`
  - Applikationsserver: `10.20.20.10`

- **Datazon**
  - Subnät: `10.20.30.0/24`
  - Gateway: `10.20.30.1`
  - Kunddatabas: `10.20.30.10`

- **Drift- och förvaltningszon**
  - Subnät: `10.20.40.0/24`
  - Gateway: `10.20.40.1`
  - Jump-server: `10.20.40.10`
  - Loggserver: `10.20.40.20`

- **Klientzon**
  - Subnät: `10.20.50.0/24`
  - Gateway: `10.20.50.1`
  - Klientdatorer: `10.20.50.10–10.20.50.254`