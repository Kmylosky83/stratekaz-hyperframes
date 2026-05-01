# Data

JSON de prueba para inyectar en plantillas de composiciones (especialmente `reports/`).

Convención: un archivo por caso de uso, nombrado igual que la composición que lo consume.

```
data/
├── reports/
│   ├── monthly-template.sample.json
│   └── client-acme.json
└── compliance/
    └── sg-sst-stats.json
```

Los datos sensibles o de clientes reales **no** deben commitearse — usar `.env` o un store externo.
