# Finanzas-Pagos

Repositorio de dominio para APIs del área **Finanzas**, subdominio **Pagos**.

## Propósito

Este repositorio almacena exclusivamente datos de APIs:
- Artefactos exportados (ZIPs)
- Configuraciones por entorno (params.yaml)
- Metadata de registro

**No contiene lógica de negocio.** Toda la orquestación la realiza el GIT-Helix-Processor.

## Estructura

```
Finanzas-Pagos/
├── apis/
│   ├── PaymentAPI/
│   │   ├── v1.0/
│   │   │   ├── uat/
│   │   │   │   ├── Artifact/
│   │   │   │   │   └── PaymentAPI_1.0.0.zip
│   │   │   │   ├── Conf/
│   │   │   │   │   └── params-uat.yaml
│   │   │   │   └── metadata.json
│   │   │   ├── nft/
│   │   │   │   └── ...
│   │   │   └── pro/
│   │   │       └── ...
│   │   └── v2.0/
│   │       └── ...
│   └── InvoiceAPI/
│       └── ...
├── .github/
│   └── workflows/
│       └── (vacío - la lógica está en GIT-Helix-Processor)
└── repo-config.yaml
```

## Convenciones

### Nomenclatura de versiones

| Versión completa | Carpeta |
|------------------|---------|
| 1.0.0 | v1.0 |
| 1.1.0 | v1.1 |
| 2.0.0 | v2.0 |

### Entornos

| Entorno | Descripción |
|---------|-------------|
| `uat` | User Acceptance Testing |
| `nft` | Non-Functional Testing |
| `pro` | Producción |

## Flujo de Vida de un API

```
1. Usuario pulsa "Registrar UAT" en WSO2 Publisher
   │
   ▼
2. WSO2-Processor recibe webhook
   │
   ▼
3. GIT-Helix-Processor detecta domain=Finanzas, subdomain=Pagos
   │
   ▼
4. Crea carpeta en Finanzas-Pagos/apis/{name}/{version}/uat/
   │
   ▼
5. (Futuro) Promoción a NFT y PRO con aprobación Helix
```

## Configuración del Repositorio

Ver `repo-config.yaml` para configuración de dominio, notificaciones y políticas.
