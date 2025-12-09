# Microservicios de Crédito y Riesgo

Este proyecto contiene dos microservicios orquestados con Docker:

1.  **credit-application-service**: El servicio principal para solicitar créditos (Puerto 8080).
2.  **risk-central-mock-service**: Un servicio simulado (mock) para evaluar riesgo crediticio (Puerto 8081).

## Requisitos Previos

*   Docker
*   Docker Compose

## Cómo Ejecutar

Para construir y levantar ambos servicios, ejecuta el siguiente comando en la raíz de este directorio:

```bash
sudo docker compose up -d --build
```

Esto descargará las dependencias, compilará los proyectos Java y creará los contenedores Docker.

## Verificación

### 1. Verificar el Servicio de Riesgo (Mock)

Puedes probar que el servicio de riesgo responde correctamente:

```bash
curl -X POST http://localhost:8081/api/risk/evaluate \
-H "Content-Type: application/json" \
-d '{"document":"12345678", "amount": 1000, "term": 12}'
```

Debería responder con un JSON que incluye el puntaje y nivel de riesgo.

### 2. Verificar el Servicio de Aplicación de Crédito

Puedes simular una solicitud de crédito completa:

```bash
curl -X POST http://localhost:8080/api/credit/request \
-H "Content-Type: application/json" \
-d '{"document":"12345678", "amount": 1000, "term": 12}'
```

## Estructura del Proyecto

*   `docker-compose.yml`: Archivo de orquestación principal.
*   `/credit-application-service`: Código fuente del servicio de créditos.
*   `/risk-central-mock-service`: Código fuente del simulador de riesgo.
# credit-docker
# docker-credit
