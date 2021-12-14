# OpenQ-Engineering-Manifesto

## One Click
There is a singularity to developer and user experience: <i>one click</i>. 

Every click above that first click must justify itself, and it's the developer and product managers job to try to return to one click.

<i>OpenQ Implementation</i>

[boot.sh](https://github.com/OpenQDev/OpenQ-Fullstack/blob/main/boot.sh): Clones all microservices, boots with docker-compose in one click.

## Externalized Configuration
Configuration should be fully externalized from the application, provided to the application via environment variables, and version controlled.
This means No hard coded values in application code

Failing to externalize all configuration makes it near operationally onerous or impossible to:
- Run your full stack locally
- Set up multi-environment
- Run mock local environments when you want to work exclusively on design and frontend
- Unit test
- Support multiple blockchains - contract addresses and ABIs, network provider URLs, and chainIds are key here

Failure to version control configuration leads to:
- Inability to atomically upgrade and rollback multiple interrelated services in unison
- (Second Order Consequence of the above ^) Fear of making changes for lack of a Ctrl+Z undo option.

<i>OpenQ Implementation</i>

[OpenQ-Helm](https://github.com/OpenQDev/OpenQ-Helm): `values` files

Loading environmnet in Kubernetes from secrets, ConfigMaps, and JSON provided at build time.

