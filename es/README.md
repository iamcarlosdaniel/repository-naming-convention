# Convención de nomenclatura de repositorios

Con el fin de estandarizar la identificación de activos de software y garantizar la trazabilidad de los proyectos, se establece la siguiente convención de nomenclatura. Esta estructura permite comprender inmediatamente el dominio, la responsabilidad y el stack tecnológico de cada repositorio.

> [!IMPORTANT]
> El contenido de este repositorio se distribuye bajo la **Licencia Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0)**.
> Todos los términos se rigen por lo establecido en el archivo [LICENSE](/LICENSE).

> [!NOTE]
> This document is also available in its **english version** at [en/README.md](/en/README.md)

El nombre del repositorio se organiza utilizando el nombre del proyecto y tres bloques lógicos separados por un doble guion (`--`). Esta separación crea una jerarquía visual que permite a los desarrolladores distinguir entre el contexto del proyecto, la identidad funcional y la implementación técnica específica:

```txt
[project_name_block] -- [identity_block] -- [stack_block](optional) -- [flag_block](optional)
```

El primer bloque, `[project_name_block]`, corresponde al nombre del proyecto. A diferencia de los demás bloques, actúa como el identificador único del proyecto. Para nombres compuestos por múltiples palabras, debe utilizarse el formato _kebab-case_ (palabras separadas por guiones).

El `[identity_block]` es el núcleo de la nomenclatura. Se construye utilizando segmentos separados por guiones simples (`-`), siguiendo un orden jerárquico estricto para asegurar que los proyectos relacionados se agrupen lógicamente y sean fácilmente identificables por su propósito principal:

```txt
[client/server] - [interface_type] - [protocol](optional) - [architecture]
```

- `client/server`: Define la responsabilidad del componente dentro del modelo cliente-servidor.

- `interface_type`: Clasifica el punto de entrada o la naturaleza del proyecto:
  - `web`: Aplicaciones basadas en navegador.
  - `mobile`: Aplicaciones móviles nativas o híbridas.
  - `api`: Servicios backend (REST, GraphQL, gRPC).
  - `proxy`: Intermediarios para redirección de tráfico o terminación SSL (Reverse Proxies).
  - `gateway`: Puntos de entrada para ecosistemas de microservicios (API Gateways).
  - `cli`: Herramientas de interfaz de línea de comandos.

- `protocol`: Especifica el protocolo de comunicación o transferencia de datos (Requerido para `api`, `proxy` y `gateway`):
  - `rest`, `graphql`, `grpc`, `soap` (APIs estándar).
  - `http`, `tcp`, `udp` (Componentes de red/infraestructura).
  - `ws` (Comunicación en tiempo real).
  - `mqtt`, `amqp` (Arquitecturas orientadas a eventos o IoT).

- `architecture`: Especifica el patrón arquitectónico predominante para orientar a los desarrolladores sobre la organización del código:
  - `layered`: Arquitectura tradicional en capas.
  - `microservices`: Componente desacoplado dentro de un ecosistema distribuido.
  - `hexagonal`: Arquitectura de puertos y adaptadores.

> [!IMPORTANT]
> Para mejorar la legibilidad y garantizar una separación clara entre los segmentos lógicos, debe utilizarse un doble guion (`--`) para prefijar las secciones de stack y flags.

> [!TIP]
> Un ejemplo de esta convención de nomenclatura puede encontrarse en el siguiente proyecto: [keep--server-api-rest-layered](https://github.com/iamcarlosdaniel/keep--server-api-rest-layered).

Para proyectos que requieren mayor granularidad, el `[stack_block]` actúa como una especificación técnica de la implementación del proyecto. Si un campo no aplica, el segmento se omite manteniendo el orden lógico:

```txt
[language/base] - [framework/base_library] - [auth_type] - [database] - [ORM] - [message_broker]
```

1. `language/base`: Lenguaje de programación base (ej.: node, java, python).
2. `framework/base_library`: Framework o librería principal (ej.: express, spring, react).
3. `auth_type`: Mecanismo de seguridad o protocolo de identidad (ej.: jwt, oauth2, firebase).
4. `database`: Motor principal de persistencia (ej.: postgres, mongodb, redis).
5. `ORM`: Capa de abstracción de datos para interactuar con la base de datos mediante objetos (ej.: prisma, hibernate, sqlalchemy).
6. `message_broker`: Infraestructura de mensajería para sistemas asíncronos (ej.: rabbitmq, kafka).

> [!TIP]
> Un ejemplo de esta convención de nomenclatura puede encontrarse en el siguiente proyecto:
> [basic-notes-app--server-api-rest-layered--javascript-express-jwt-mongodb-mongoose](https://github.com/iamcarlosdaniel/basic-notes-app--server-api-rest-layered--javascript-express-jwt-mongodb-mongoose).

El `[flag_block]` proporciona metadatos críticos del ciclo de vida o indicadores de estado. Este segmento garantiza que los activos experimentales, obsoletos o versionados sean identificables inmediatamente sin necesidad de inspeccionar el contenido del repositorio:

`flag`: Metadato adicional o indicador de estado (ej.: legacy, poc, v2).

> [!NOTE]
> Todos los campos deben escribirse estrictamente en minúsculas, evitando caracteres especiales o espacios. De forma consistente con la sección anterior, debe utilizarse un doble guion (`--`) para indicar el segmento de Flag.
