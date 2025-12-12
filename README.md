# apim-domain-finanzas

Repositorio Git para almacenamiento de APIs del dominio **Finanzas / Pagos**.

## Propósito

Este repositorio almacena las definiciones de APIs que pertenecen al subdominio `finanzas-pagos`. Las APIs son registradas automáticamente por el sistema APIOps cuando se aprueba un CRQ en Helix ITSM.

## Estructura

```
apim-domain-finanzas/
├── apis/
│   └── {APIName}/
│       └── {Version}/
│           └── revisions/
│               └── rev-{N}/
│                   ├── {APIName}-{Version}/
│                   │   ├── api.json        # Definición completa de la API
│                   │   ├── api_meta.yaml   # Metadata adicional
│                   │   └── Definitions/
│                   │       └── swagger.json # OpenAPI spec
│                   └── request.yaml        # Metadata de la solicitud
├── repo-config.yaml                        # Configuración del dominio
└── README.md
```

## Flujo de Trabajo

1. Un desarrollador solicita registrar una API en UAT desde el Publisher de WSO2
2. El sistema extrae la API y crea un CRQ en Helix ITSM
3. Cuando el CRQ es aprobado, se crea automáticamente un PR en este repositorio
4. El PR es auto-merged (Helix ya aprobó)
5. La API queda versionada en Git

## Configuración

Ver `repo-config.yaml` para:
- Owners del dominio
- Políticas por entorno (UAT, NFT, PRO)
- Configuración de notificaciones

## Trazabilidad

Cada `request.yaml` contiene la trazabilidad completa:
- Request ID
- CRQ de Helix
- Usuario solicitante
- Links a workflows de GitHub Actions

