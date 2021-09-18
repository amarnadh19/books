# Azure Traffic Manager

- It is Global service which acts a Load Balancer while using services in different regions.

- We can configure Traffic Manager to route all requests to our primary region. If app fails in Primary region then Traffic Manager auto reroutes user requests to the app service in the secondary region.

- This reroute execute the failover that failover that ensures continous service. We call this arrangement the priority routing mode.

- It uses DNS, So route any Protocol.

- Cannot route or filter traffic based on HTTP properties.

- It also cannot do TLS protocol termination.

- Traffic Manager uses highly configurble and point monitoring.

## How Traffic Manager works

When a client attempts to connect to a service, first it resolves the DNS name of the service as an IP address. The client then connects to that IP address to access the service.

## Traffic Manager endpoints

An endpoint is the destination location that is returned to the client. You configure each application deployment as an 'endpoint' in Traffic Manager.

An endpoint is the destination location that is returned to the client. You configure each application deployment as an 'endpoint' in Traffic Manager. When Traffic Manager receives a DNS request, it chooses an available endpoint to return in the DNS response.

There are three types of endpoint supported by Traffic Manager:

**Azure endpoints** are used for services hosted in Azure. These can be services like Azure App Service, as well as public IP resources that are associated with load balancers or virtual machines.

**External endpoints** are used for IPv4/IPv6 addresses, FQDNs, or for services hosted outside Azure that can either be on-premises or with a different hosting provider.

**Nested endpoints** are used to combine Traffic Manager profiles to create more flexible traffic-routing schemes to support the needs of larger, more complex deployments.

