# [Microservices](https://martinfowler.com/articles/microservices.html)
by Martin Fowler and James Lewis (2014)

## Characteristic of a Microservice Architecture

1. Componentization via services
  - Applications become independently upgradeable and replaceable components that communicate via some mechanism such as a web request (HTTP) or remote procedure call
  - Facilitate structured communication via service contracts
  - Hard to reorganize service responsibilities so initial organization is crucial
2. Organized around business capabilities
  - Smaller teams that are focused on their specific products
  - Requires more of a full stack team approach rather than division based on specialty
3. Products not Projects
  - Teams are responsible for products over their entire lifetime rather than just projects to completion
  - Easier to facilitate an ongoing relationship between developers and users
4. Smart endpoints and dumb pipes
  - Communication between services is simple and any middleware should contain no logic
  - Most often communication is done via HTTP
5. Decentralized Governance
  - Responsibility is shifted from centralized management to the individual teams
  - Applies to everything from technology choices and clean code responsibility to service contract management
6. Decentralized data management
  - Services do not share access to any data store, data is only shared via service to service communication
  - In recognition that inconsistencies may occur we emphasize using transactionless coordination between services
7. Infrastructure automation
  - Automation via CI, CD, testing, etc is always good and can be done more efficiently when using microservices
8. Design for failure
  - With the disjointed architecture of microservices failed communication will happen applications must be able to handle this elegantly
  - Services should also have good real time monitoring and any failure should automatically trigger appropriate actions for restoration
9. Evolutionary design
  - Services need to be tolerable to change
  - Functionality that changes at a similar pace can often be bundled into a single service 
