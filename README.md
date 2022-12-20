## Installation
The files in this repo have only been tested with a local minikube cluster, but should general enough to work more or less in any vanilla Kubernetes.

To set things up do the following:

1) Install argocd by installing the files in the k8s-components/argocd folder one by one in the numbered order. (Some of the higher numbered files are overrides for stuff that is in the 01-argocd-install file.)

2) After installing the last file, restart argocd by killing the argocd-application-* and argocd-server-* pods. This is to make sure it will use the new config from one of the last files that got applied.

3) Install Kyverno by installing the files in the k8s-components/kyverno folder one by one in the numbered order.

-- At this point the system have all the service components installed and ready --

4) Install the Kyverno policies that we tell Kyverno to actually do its thing. These are located in runtime-template. Two rules that will generate resources (generate-*) and one rule to slightly modify any application resource that our users add (mutate-*)

In the runtime-instances folder there are two example namespaces tagged and ready to deploy to test it all.
