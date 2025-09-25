# 📌proyecto-fhir

Este proyecto implementa un servidor HAPI FHIR JPA Starter asegurado con Keycloak, desplegado en Docker.
Incluye la configuración necesaria para exponer el API FHIR y validar la autenticación vía OAuth2.

⚙️ Requisitos

Docker instalado
Git instalado
Navegador web

🚀 Cómo levantar el proyecto
1.Clonar el repositorio:
git clone https://github.com/TU-USUARIO/proyecto-parcial.git
cd proyecto-parcial/hapi-fhir-jpaserver-starter

2.Construir y levantar el contenedor (ejemplo con Docker Compose o Docker run según tengas configurado):
docker run -p 8080:8080 hapiproject/hapi:latest

3.Verifica que el servidor está corriendo:

curl http://localhost:8080/fhir/metadata

🔑 Autenticación con Keycloak

El servidor está protegido con Keycloak.
Al acceder a la API, serás redirigido al login de Keycloak.
Ingresa con las credenciales configuradas en el realm de pruebas.

Ejemplo de Realm configurado:

Realm: fhir-realm
Cliente: fhir-client
Roles: user, admin

📖 Swagger / OpenAPI

El servidor expone la especificación OpenAPI en:
JSON: http://localhost:8080/fhir/openapi.json

🧪 Ejemplo de prueba con curl
1.Obtener metadata del servidor FHIR:
curl http://localhost:8080/fhir/metadata

2.Crear un recurso Patient:
curl -X POST http://localhost:8080/fhir/Patient \
-H "Content-Type: application/fhir+json" \
-d '{
  "resourceType": "Patient",
  "id": "12345",
  "name": [{ "family": "Doe", "given": ["John"] }],
  "gender": "male",
  "birthDate": "1980-01-01"
}'

3.Consultar el paciente creado:
curl http://localhost:8080/fhir/Patient/12345 -H "Accept: application/fhir+json"

📂 Estructura del repositorio
Proyecto_Parcial/
├── hapi-fhir-jpaserver-starter/   # Proyecto base de HAPI FHIR
├── application.yaml               # Configuración personalizada
└── README.md                      # Este archivo
