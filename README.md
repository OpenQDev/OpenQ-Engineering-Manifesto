# OpenQ-Engineering-Manifesto

## One Click DevEx + UX
There is a singularity to developer and user experience: <i>one click</i>. 

Every click above that first click must justify itself, and it's the developer and product managers job to try to return to one click whenever possible.

<i>OpenQ Implementation</i>

[boot.sh](https://github.com/OpenQDev/OpenQ-Fullstack/blob/main/boot.sh): Clones all microservices, boots with docker-compose in one click.

## Security Through Cryptography, Not Obscurity

Leaked source code should never expose your app to exploits. Only leaked secrets should be.

Open Source (even read-only permissioned open source) is a challenge more corporates should take on.

<i>OpenQ Implementation</i>

Everything from our auth server to our TLS certificate manager is open source.

## Work Where Developers Already Work

Readership of documentation drops with every click away from the codebase. So does usership.

Put your documentation and product at the place where it is most useful.

<i>OpenQ Implementation</i>

[OpenQ-Bot](https://github.com/OpenQDev/OpenQ-Bot)

## Fully Externalize Your Configuration
Configuration consists of variables which define how external services are access.

Configuration should be fully externalized from the application, provided to the application via environment variables, and version controlled.

Failing to externalize all configuration makes it operationally onerous or impossible to:
- Run your full stack locally
- Separate test, development, staging and production environments
- Run mock local environments when you want to focus on design and frontend
- Unit test
- Support multiple blockchains (contract addresses and ABIs, network provider URLs, and chain identifiers)

Failure to version control configuration leads to:
- Inability to atomically upgrade and rollback multiple interrelated services in unison
- (Second Order Consequence of the above ^) Fear of making changes for lack of a Ctrl+Z undo option.

<i>OpenQ Implementation</i>

[OpenQ-Helm](https://github.com/OpenQDev/OpenQ-Helm): `values` files

Loading environmnet in Kubernetes from secrets, ConfigMaps, and JSON provided at build time.

## Use Decentralized Platforms For Utility, not Marketing

You would never see a tech company brag about how they use Postgres or MongoDB on their main consumer website. So why do they do so with blockchain?

Often it is to extract marketing value from what should be an implementation detail of the software stack.

Blockchain is a decentralized compute and storage platform with the potential for societal impact rivalled in recent decades only by the advent of the Internet.

But it is still meant to do the same thing as all other software: provide humans with something valuable.

Where blockchain is round-peg-square-holed into products which benefit little or negatively from decentralization, one's red flag 🚩 alert should go off.

The areas in which OpenQ leverages decentralized options:
- **Smart escrow through smart contracts**: Programmable money lets OpenQ pay out bounties only to the rightful contributors, refund bounties for uncompleted tasks, all without intermediaries.
- **Decentralized accounting with ERC20/ERC721**: ERC20 and ERC721 have everything we need to accept all kinds of cryptocurrencies and digital assets as bounties
- **Indexing, event sourcing and data aggregation with The Graph**

Better technical solutions should win on utility, not marketing value.

Though we are not fully decentralized yet, we have a roadmap to get there as soon as it is technologically possible to do so without compromising on user experience. 

- **Internet Computer**: Deploy our microservices to workers running on Internet Computer
- **API3 Airnode for Github**: Work with Github and API3 to help Github expose public user and repository data directly on-chain using Airnode. Since Github is an inherently centralized data source (unlike price feeds or weather data), using Chainlink's impressive Decentralized Oracle Networks (DONs) infrastrucutre would be redundant, adding higher cost for bounty withdrawls with limited to no increase in security.
- **Use Handshake for DNS Resolution**

In the meantime, a healthy mix of centralization and decentralization provides the best developer and user experience.

<i>OpenQ Implementation</i>

### Where we leverage decentralized solutions:

- [OpenQ-Contracts](https://github.com/OpenQDev/OpenQ-Contracts)
- [OpenQ-Graph](https://github.com/OpenQDev/OpenQ-Graph)

### Where we still leverage centralized solutions:

- [OpenQ-Oracle](https://github.com/OpenQDev/OpenQ-Oracle)
- Coingeck API
- Caching coin prices with Redis