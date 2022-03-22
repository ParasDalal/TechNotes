### Orchesterator:

![01_ReasonsToSplitMicroservices](CloudArchitecture.assets/01_ReasonsToSplitMicroservices.png)

- Manages cluster of hardware and their lifecycles
- Manages the health monitoring of various things running
- Manage scale - add/remove instances of the services
- Detects the crash and restart the service
- If the resource is not available, informs the load balancer of the situation (so that new requests can be sent to remaining resources)
- If new machine (resource) is available, inform load balancer, so that the new resource can be used
- Can support auto-scaling based on the load on the existing resources

![02_MicroservicesMyths](CloudArchitecture.assets/02_MicroservicesMyths.png)

### Overall Architecture:

Each service solves its own domain specific problem and has exclusive access to its own data storage

You may need to separate services for various reasons
-	Can scale independently
-	Can use different technology stacks (e.g. .Net vs Java)
-	More than one clients want to use the same service (in which case, we can separate it as a service) We can version the service in case changes are needed
-	May need different version of technology to be loaded for different version of services 

### Autoscale services![03_AutoscalingServiceInstances](CloudArchitecture.assets/03_AutoscalingServiceInstances.png)

- 	Check the queued messages and scale up if the queue is having larger backlog
-	Check resource usage and scale up if resource usage is higher
-	Based on schedule/load estimate, proactively upscale

### 12factor.net

![04_12Factor-1](CloudArchitecture.assets/04_12Factor-1.png)

![05_12Factor-2](CloudArchitecture.assets/05_12Factor-2.png)

![06_12Factor-3](CloudArchitecture.assets/06_12Factor-3.png)

![07_Container1](CloudArchitecture.assets/07_Container1.png)

![08_Container2](CloudArchitecture.assets/08_Container2.png)

![09_Container3](CloudArchitecture.assets/09_Container3.png)

![](CloudArchitecture.assets/10_Container4.png)

![](CloudArchitecture.assets/11_Container5.png)

![](CloudArchitecture.assets/12_Container6.png)

![](CloudArchitecture.assets/13_Container7.png)

![](CloudArchitecture.assets/14_Container8.png)

![](CloudArchitecture.assets/15_CI_CD1.png)



### Networking:

![](CloudArchitecture.assets/16_NetworkingFallacies.png)

![](CloudArchitecture.assets/17_ServiceEndPoints.png)

![](CloudArchitecture.assets/18_ServiceAvailability.png)

![](CloudArchitecture.assets/19_ForwardAndReverseProxies.png)

![20_ProxyExample](CloudArchitecture.assets/20_ProxyExample.png)

![21_LoadBalancer](CloudArchitecture.assets/21_LoadBalancer.png)

![21_MonolithToMicroService1](CloudArchitecture.assets/21_MonolithToMicroService1.png)

![22_APIVersioning](CloudArchitecture.assets/22_APIVersioning.png)

![23_Contract](CloudArchitecture.assets/23_Contract.png)

![24_RPCAbstractions](CloudArchitecture.assets/24_RPCAbstractions.png)

![25_FailedOperations](CloudArchitecture.assets/25_FailedOperations.png)

![26_Idempotent1](CloudArchitecture.assets/26_Idempotent1.png)

![27_Idempotent2](CloudArchitecture.assets/27_Idempotent2.png)
