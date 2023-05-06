kubernetes 1 day 2
------------------

Topics

* phippy goes to the zoo
* kubernetes components
* pods
* controllers
* services
* intall `oc` client

phippy goes to the zoo
----------------------

[Part 2 of Phippy's Journey](https://www.cncf.io/phippy/phippy-goes-to-the-zoo-book/)

kubernetes components
---------------------

A Kubernetes cluster consists of a set of worker machines, called nodes, that run containerized applications. Every cluster has at least one worker node.

The worker node(s) host the Pods that are the components of the application workload. The control plane manages the worker nodes and the Pods in the cluster. In production environments, the control plane usually runs across multiple computers and a cluster usually runs multiple nodes, providing fault-tolerance and high availability.

Control Plane Components
* kube-apiserver
* etcd
* kube-scheduler
* kube-controller-manager
* cloud-controller-manager

Node Components
* kubelet
* kube-proxy
* [container runtime via CRI](https://github.com/kubernetes/community/blob/master/contributors/devel/sig-node/container-runtime-interface.md)


Links
* [Kubernetes Components](https://kubernetes.io/docs/concepts/overview/components/)
* [Overview of Kube Components](https://medium.com/@karthikeyan_krishnaswamy/overview-of-kubernetes-34d8e0e59b26)

pods
----

Pods are the smallest deployable units of computing that you can create and manage in Kubernetes.

A Pod (as in a pod of whales or pea pod) is a group of one or more containers, with shared storage/network resources, and a specification for how to run the containers. A Pod's contents are always co-located and co-scheduled, and run in a shared context. A Pod models an application-specific "logical host": it contains one or more application containers which are relatively tightly coupled. In non-cloud contexts, applications executed on the same physical or virtual machine are analogous to cloud applications executed on the same logical host.

Links
* [Pods](https://kubernetes.io/docs/concepts/workloads/pods/)
* [Managing Resources](https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/)

controllers
-----------

In Kubernetes, controllers are control loops that watch the state of your cluster, then make or request changes where needed. Each controller tries to move the current cluster state closer to the desired state.

Links
* [Controllers](https://kubernetes.io/docs/concepts/architecture/controller/)
* [ReplicationController](https://kubernetes.io/docs/concepts/workloads/controllers/replicationcontroller/)
* [Deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)
* [ReplicaSet](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/)
* [ReplicatonController vs Deployment](https://ryaneschinger.com/blog/rolling-updates-kubernetes-replication-controllers-vs-deployments/)

services
--------

A service can be defined as a logical set of pods. It provides a single IP address and DNS name by which pods can be accessed. This ip and dns entry load balance accross all of the pods.

Link
* [Services](https://kubernetes.io/docs/concepts/services-networking/service/)

intall `oc` client
------------------

1. Install the Openshift oc client
    * Pick the binary for your platform from the [okd release page](https://github.com/openshift/okd/releases/tag/4.5.0-0.okd-2020-09-04-180756) and put it in your PATH
        * [Mac](https://github.com/openshift/okd/releases/download/4.5.0-0.okd-2020-09-04-180756/openshift-client-mac-4.5.0-0.okd-2020-09-04-180756.tar.gz)
        * [Windows](https://github.com/openshift/okd/releases/download/4.5.0-0.okd-2020-09-04-180756/openshift-client-windows-4.5.0-0.okd-2020-09-04-180756.zip)
        * [Linux](https://github.com/openshift/okd/releases/download/4.5.0-0.okd-2020-09-04-180756/openshift-client-linux-4.5.0-0.okd-2020-09-04-180756.tar.gz)
        * Mac homebrew - `brew install openshift-cli`
    * Log into the class Openshift cluster
    * See class Slack for credentials
2. Log in on the command line `oc login`
    * Run `oc get nodes`
    * Log into the Web UI
3. Create a project/namespace that matches your name
first initial + last name e.g. Timothy Allen = tallen
    * Run `oc new-project <myname>`

create and understand basic kubernetes resources
------------------------------------------------

Fill in the missing information for each resource

Fill in the pod.

    kubectl apply -f pod.yml

Fill in and apply the service to target the pod.

    kubectl apply -f svc.yml

Fill in and apply the replication controller.

    kubectl apply -f replicationcontroller.yml

Fill in and apply the Deployment

    kubectl apply -f deployment.yml
