# Framework - Design Approach
The framework components attempt to follow the principle of pragmatic (KISS) design. Practically, it means that each 
the component must follow given rules:
- avoid cross dependencies when possible
- prioritize composition over inheritance
- prefer smaller but richer interfaces
- avoid magic

## Hybrid Runtime
The framework relies on the application server to run some of its services. PHP codebase mostly centered around quick delivery
of efficient business logic. The application server, Golang based, is focused on efficiently solving the infrastructure tasks.

> Spiral application server is a customized version of [RoadRunner](https://roadrunner.dev).

![High Level Architecture Diagram](https://user-images.githubusercontent.com/796136/64451724-762d0800-d0ed-11e9-8c34-9c054a7bb0bd.png)

> Read about application lifecycle [here](/start/workers.md).
