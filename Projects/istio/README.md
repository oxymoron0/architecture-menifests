# Istio Resource Management

This directory contains Istio-specific configurations such as `VirtualService`, `Gateway`, and `DestinationRule`. These resources are managed through GitOps and deployed using Argo CD.

## Examples

### HTTP Traffic Management

```yaml
# HTTP Gateway Example
apiVersion: networking.istio.io/v1beta1
kind: Gateway
metadata:
  name: <GatewayName>
  namespace: <Namespace>
spec:
  selector:
    istio: <GatewaySelector>
  servers:
  - port:
      number: <GatewayPort>
      name: http
      protocol: HTTP
    hosts:
    - "<HostName>"
---
# HTTP VirtualService Example
apiVersion: networking.istio.io/v1alpha3
kind: VirtualService
metadata:
  name: <VirtualServiceName>
  namespace: <Namespace>
spec:
  hosts:
  - "<HostName>"
  gateways:
  - <GatewayName>
  http:
  - match:
    - uri:
        prefix: <URIPrefix>
    route:
    - destination:
        host: <TargetService>
        port:
          number: <TargetServicePort>
```

### TCP Traffic Management

```yaml
# TCP Gateway Example
apiVersion: networking.istio.io/v1beta1
kind: Gateway
metadata:
  name: <GatewayName>
  namespace: <Namespace>
spec:
  selector:
    istio: <GatewaySelector>
  servers:
  - port:
      number: <GatewayPort>
      name: tcp
      protocol: TCP
    hosts:
    - "<HostName>"
---
# TCP VirtualService Example
apiVersion: networking.istio.io/v1alpha3
kind: VirtualService
metadata:
  name: <VirtualServiceName>
  namespace: <Namespace>
spec:
  hosts:
  - "<HostName>"
  gateways:
  - <GatewayName>
  tcp:
  - match:
    - port: <GatewayPort>
    route:
    - destination:
        host: <TargetService>
        port:
          number: <TargetServicePort>
```

## Configuration Parameters

### Common Parameters
- `<Namespace>`: Kubernetes namespace where resources will be deployed
- `<HostName>`: Domain name or host for the service (e.g., "example.com")
- `<GatewayName>`: Name of the Gateway resource
- `<VirtualServiceName>`: Name of the VirtualService resource
- `<GatewaySelector>`: Istio ingress gateway selector (e.g., "ingressgateway" or "tcp-ingress")

### HTTP Specific Parameters
- `<GatewayPort>`: Port number for HTTP traffic (typically 80 or 443)
- `<URIPrefix>`: URI path prefix for routing (e.g., "/api")
- `<TargetService>`: Name of the target Kubernetes service
- `<TargetServicePort>`: Port number of the target service

### TCP Specific Parameters
- `<GatewayPort>`: Port number for TCP traffic (e.g., 3307 for MySQL)
- `<TargetService>`: Name of the target Kubernetes service
- `<TargetServicePort>`: Port number of the target service

## Configuration Guidelines

1. **Gateway Configuration**
   - Define ingress points for both HTTP and TCP traffic
   - Specify appropriate selectors for Istio ingress gateways
   - Configure ports and protocols according to service requirements

2. **VirtualService Configuration**
   - Route traffic based on hostnames and paths (HTTP) or ports (TCP)
   - Define destination services and ports
   - Apply traffic management rules as needed

3. **Best Practices**
   - Use meaningful names for Gateways and VirtualServices
   - Organize resources by namespace
   - Document any special routing rules or requirements
   - Keep configurations version-controlled and reviewed

## Common Use Cases

1. **HTTP Traffic**
   - Web application routing
   - API gateway patterns
   - Path-based routing
   - Header-based routing

2. **TCP Traffic**
   - Database connections
   - Custom TCP services
   - Legacy application support
   - Non-HTTP protocols

## Notes

- Ensure proper namespace configuration
- Verify gateway selectors match your Istio installation
- Test configurations in a staging environment before production
- Monitor traffic patterns after deployment