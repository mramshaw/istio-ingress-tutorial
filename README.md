# Istio Ingress Tutorial

This tutorial demonstrates how to run the Istio Ingress Controller in a Kubernetes Cluster.

[I watched Kelsey Hightower present this tutorial, which seemed like a good reason to try it myself.]

## Rationale

The [Istio project](https://istio.io/) hosts multiple components including: [Pilot](https://istio.io/docs/concepts/traffic-management/pilot.html), [Mixer](https://istio.io/docs/concepts/policy-and-control/mixer.html), and [Istio Auth](https://istio.io/docs/concepts/what-is-istio/overview.html#istio-auth). When combined these components provide a complete platform to connect, manage, and secure [microservices](https://github.com/mramshaw/Microservices). However, adopting Istio is not an all or nothing proposition. You can adopt only the parts you need. In this tutorial the Istio Pilot, which is responsible for the lifecycle of [Envoy](https://www.envoyproxy.io/) instances, and the Istio Ingress, a [Kubernetes Ingress Controller](https://kubernetes.io/docs/concepts/services-networking/ingress/) based on Envoy, will be used to provide a robust Ingress solution.

[Ingress controllers are really interesting plus [Istio](https://istio.io/docs/concepts/traffic-management/rules-configuration.html) offers some very interesting possibilities also.]

## Architecture

![Istio Ingress Architecture](images/istio-ingress.png)

* Istio Pilot managed by a Deployment 
* Istio Ingress Controller managed by a DaemonSet
  * Runs on each node in a dedicated Istio Ingress node pool
* Frontend Load Balancer distributes traffic across multiple Istio Ingress Controllers

## Tutorial

* [Prerequisites](docs/01-prerequisites.md)
* [Install Client Tools](docs/02-client-tools.md)
* [Provision the Kubernetes Infrastructure](docs/03-kubernetes-infrastructure.md)
* [Provision the Istio Pilot](docs/04-istio-pilot.md)
* [Provision the Istio Ingress Controller](docs/05-istio-ingress-controller.md)
* [Using Istio Route Rules](docs/06-istio-route-rules.md)

## Clean Up

Run the clean-up bash script to remove all compute resources created by this tutorial:

```
bash clean-up
```

## TODO

- [ ] Convert deprecated [ThirdPartyResource](https://kubernetes.io/docs/tasks/access-kubernetes-api/extend-api-third-party-resource/) to a [CustomResourceDefinition](https://kubernetes.io/docs/tasks/access-kubernetes-api/migrate-third-party-resource/)
