# Quick Start

The **Federator.ai Operator** is an operator that manages **Federator.ai** in ways of:
- Deployment
- Upgrade
- Application lifecycle and storage

And this document helps you to get started.




## Deployment

Please deploy **Federator.ai Operator** from **NKS Solutions**.

> **Note**: The minimum requirement to run Federator.ai Operator is 4 CPUs and 8GB Memory of single worker node (for example: AWS t2.xlarg, GCP N1 Standard 4, and Azure Standard A3). 


## Using Federator.ai

After **Federator.ai** is installed, it does not orchestrate any pod resources by default. Users use _alamedascaler_ [CRD](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/) as a channel to tell **Federator.ai** which pods needs be managed. The resource usage metrics of managed pods will then be gathered and predicted.

Here is an example _alamedascaler_ CR:

```alamedaautoscaler.yaml
apiVersion: autoscaling.containers.ai/v1alpha1
kind: AlamedaScaler
metadata:
  name: alameda-nginx
  namespace: nginx    ## application namespace
spec:
  selector:
    matchLabels:
    app: nginx     ## application label
```



In this example, it creates an _AlamedaScaler_ CR with name _alameda-nginx_ in namespace _nginx_. With this CR, **Federator.ai** will look for K8s deployment and _deploymentconfig_ resource objects with label _app: nginx_ in the same _nginx_ namespace. Any containers derivated from the found objects will be managed for their resource usages by **Federator.ai**.



## Federator.ai Extension

**Federator.ai Extension** is a Chrome Extension to provide **NetApp Kubernetes Service** ([NKS](https://nks.netapp.io)) users both Cost Recommendation for Day 1 - Deployment and Cost Monitoring/Analysis/Recommendation for Day 2 - Operation of Kubernetes cluster on public cloud.

Please refer [**Federator.ai Extension**](https://github.com/containers-ai/federatorai-extension) document for the deployment.
