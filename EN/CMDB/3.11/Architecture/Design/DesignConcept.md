# Design Concept 

 BK-CMDB 3.0 is designed based on service architecture, which is divided into four layers as a whole. In addition to API gateway and the lowest storage, the middle logic part is layered according to the operation boundary of resources, which is divided into Business Name Scene layer and Resource Management layer. 

 There are various scenario service close to the business in the Business Name Scene layer, and each service has a clear boundary.  There is no direct coupling between scene service, and each scene service is status and deployment. 

 In the resource management layer, there are various abstract controllers that manage resources, which we call controller, and this controller delegates all operation on the resource. 

 For the service of each scene layer, the logic of the service is the combination of operation on various resources; for a service in the resource management layer, the caller of the service is a variety of scene. 

 This resource layer design gives full play to the characteristics of service reuse in the service architecture, and has several advantages in practical application: Scalable, easy to monitor, hot system update 

 ## Scalability 

 If the business name scene needs to be extended, it is only necessary to develop a new scenario layer service and reuse the service and interface of the resource management layer.  The new service does not affect the functionality of the existing services. Similarly, if a new Manage Resource type needs to be added, only the corresponding Resource Management service needs to be re-developed, and the execution of the existing Resource Management service and the functionality of the Scene layer service are not affected. 

 ## Simple monitoring 

 By separating the atomic management of resources from the complex scene, the resource operation can be standard and fluid, and the capture and push of resource changes can be more accurate.  At the same time, the scene layer focuses only on the business name logic of the proprietary scenario, and the link monitoring processing is clearer and more concise. 

 ## System Hot Update 

 Thanks to the characteristics of the service architecture, after the resource management and scene services are layered, the new scenario services and the newly added resource management services can be increment release without affecting the existing deployment of the online environment, and the gray scale process can be controlled to approve a similar blue-green release or canary release.