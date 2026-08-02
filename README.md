# Gravie

Gravie is a Minneapolis, Minnesota health benefits company founded in 2013 that designs and administers health
plans for small and midsize employers — the Comfort level-funded plan (zero deductible, zero copay on most
common services), Gravie ICHRA administration, Gravie Pay, Gravie Care and a pharmacy benefit. Gravie operates
as a third-party administrator on top of partner networks (Aetna Signature Administrators, Cigna, Cigna OAP,
HPS/Paymedix, historically PreferredOne).

- Website: https://www.gravie.com/
- GitHub: https://github.com/gravieinc
- Secondary market listing: https://forgeglobal.com/gravie_stock/

## API surface

Gravie publishes **no public developer program, API documentation, OpenAPI/AsyncAPI/GraphQL spec, SDK, CLI,
sandbox, changelog or status page.** Contract discovery on 2026-08-01 probed `www.gravie.com`,
`api.gravie.com`, `static.gravie.com`, `member.gravie.com` and `employer.gravie.com` for OpenAPI, Swagger,
GraphQL, MCP, A2A agent cards and the full `/.well-known/` set — every probe missed. `api.gravie.com` is an
authenticated gateway backing the Gravie member apps and returns `403 {"message":"Forbidden"}` for every
anonymous path.

The one real public machine-readable surface is the **CMS Transparency in Coverage** file set Gravie posts on
behalf of plan sponsors at `static.gravie.com/MRFs/`, indexed at
https://www.gravie.com/compliance/transparency-in-coverage/. Provider-side integration is EDI rather than
HTTP: X12 837 claims under payer IDs **GRV01** (Aetna Signature Administrators) and **62308** (Cigna).

## Artifacts

| Path | What it is |
|---|---|
| `apis.yml` | APIs.json index — identity, Transparency in Coverage data surface, link properties |
| `conformance/gravie-conformance.yml` | Regulatory + technical conformance (TiC, No Surprises Act, HIPAA, SOC 2 Type 1, X12 837, CCPA) |
| `security/gravie-domain-security.yml` | TLS/HSTS/DNSSEC/CAA/SPF/DMARC probe |
| `well-known/gravie-well-known.yml` | `/.well-known/` probe record across five hosts (no documents found) |
| `llms/gravie-llms.txt` | Generated llms.txt for agents |
