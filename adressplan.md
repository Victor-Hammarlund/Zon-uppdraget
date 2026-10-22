## Adressplan

**Uppdragsgivarens adressutrymme:** `10.40.0.0/16`

**Förutsättningar:**
- Samtliga övningar, CTF-labbar och teamens adressplaner använder IPv4-adressutrymmet `10.40.0.0/16`.
- IPv6 är avstängt på labbservrarna.
- Varje nätverkszon har ett separat `/24`-subnät.
- Gateway-adresser reserveras som `10.40.X.1` i respektive subnät.

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

