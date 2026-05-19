# Repository naming convention

In order to standardize software asset identification and ensure project traceability, the following naming convention is established. This structure enables immediate understanding of the domain, responsibility, and technology stack of each repository.

> [!IMPORTANT]
> The content of this repository is distributed under the **Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License (CC BY-NC-SA 4.0)**.
> All terms are governed by what is stated in the [LICENSE](/LICENSE) file.

> [!NOTE]
> Este documento también se encuentra disponible en su **versión en español** en [es/README.md](/es/README.md)

The repository name is organized using the project name and three logical blocks separated by a double hyphen (--). This separation creates a visual hierarchy that allows developers to distinguish between the project context, the functional identity, and the specific technical implementation:

```txt
[project_name_block] -- [identity_block] -- [stack_block](optional) -- [flag_block](optional)
```

The first block, `[project_name_block]`, corresponds to the project name. Unlike the other blocks, it acts as the project's unique identifier. For names composed of multiple words, the _kebab-case_ format (words separated by hyphens) must be used.

The `[identity_block]` is the core of the nomenclature. It is constructed using segments separated by single hyphens (-), following a strict hierarchical order to ensure that related projects are logically grouped and easily identifiable by their primary purpose:

```txt
[client/server] - [interface_type] - [protocol](optional) - [architecture]
```

- `client/server`: Defines the component’s responsibility within the client-server model.

- `interface_type`: Classifies the entry point or nature of the project:
  - `web`: Browser-based applications.
  - `mobile`: Native or hybrid mobile applications.
  - `api`: Backend services (REST, GraphQL, gRPC).
  - `proxy`: Intermediaries for traffic redirection or SSL termination (Reverse Proxies).
  - `gateway`: Entry points for microservices ecosystems (API Gateways).
  - `cli`: Command-line interface tools.

- `protocol`: Specifies the communication or data transfer protocol (Required for api, proxy, and gateway):
  - `rest`, `graphql`, `grpc`, `soap` (Standard APIs).
  - `http`, `tcp`, `udp` (Network/Infrastructure components).
  - `ws` (Real-time communication).
  - `mqtt`, `amqp` (Event-driven or IoT).

- `architecture`: Specifies the predominant architectural pattern to guide developers on code organization:
  - `layered`: Traditional layered architecture.
  - `microservices`: Decoupled component within a distributed ecosystem.
  - `hexagonal`: Ports-and-adapters architecture.

> [!IMPORTANT]
> To improve readability and ensure a clear separation between logical segments, a double hyphen (--) must be used to prefix the stack and flag sections.

> [!TIP]
> An example of this naming convention can be found in the following project: [keep--server-api-rest-layered](https://github.com/iamcarlosdaniel/keep--server-api-rest-layered).

For projects requiring greater granularity, the `[stack_block]` acts as a technical specification of the project's implementation. If a field is not applicable, the segment is omitted while maintaining logical order:

```txt
[language/base] - [framework/base_library] - [auth_type] - [database] - [ORM] - [message_broker]
```

1. `language/base`: Base programming language (e.g., node, java, python).
2. `framework/base_library`: Primary framework or library (e.g., express, spring, react).
3. `auth_type`: Security mechanism or identity protocol (e.g., jwt, oauth2, firebase).
4. `database`: Primary persistence engine (e.g., postgres, mongodb, redis).
5. `ORM`: Data abstraction layer for database interaction via objects (e.g., prisma, hibernate, sqlalchemy).
6. `message_broker`: Messaging infrastructure for asynchronous systems (e.g., rabbitmq, kafka).

> [!TIP]
> An example of this naming convention can be found in the following project: <br />
> [basic-notes-app--server-api-rest-layered--javascript-express-jwt-mongodb-mongoose](https://github.com/iamcarlosdaniel/basic-notes-app--server-api-rest-layered--javascript-express-jwt-mongodb-mongoose).

The `[flag_block]` provides critical lifecycle metadata or status indicators. This segment ensures that experimental, deprecated, or versioned assets are immediately identifiable without inspecting the repository content:

`flag`: Additional metadata or status indicator (e.g., legacy, poc, v2).

> [!NOTE]
> All fields must be written strictly in lowercase, avoiding special characters or spaces. Consistent with the previous section, a double hyphen (--) must be used to indicate the Flag segment.
