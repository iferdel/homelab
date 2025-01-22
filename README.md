# Homelab

This repo contains all of the configuration and documentation of my homelab.

The whole idea of having a homelab is to have a place where I can try out and learn new things using Kubernetes and GitOps as backbone. On the other hand, by self-hosting some applications, it makes me feel responsible for the entire process of deploying and maintaining an application from A to Z. It forces me to think about backup strategies, security, scalability and the ease of deployment and maintenance.

(Diagram of GitOps powered homelab)

## Principles

I have a few principles that guide my choices for my homelab.

* I try to keep in the Azure Kubernetes Service (AKS) ecosystem. This is why I chose Flux for GitOps, for example
* Everything is deployed through GitOps

## Cluster Provisioning

I use [Talos Linux](https://www.talos.dev/) to set up my machines (kudos to ventoy tooling, since it makes easier for the installation). Talos is so lightweight and minimal, and it provides production grade security right out of the box. It also forces me to use all my servers as Kubernetes nodes only, so I need to figure out ways to run all my desired workloads and services on Kubernetes, such as one may expect in a cloud based scenario.

## Hardware

I'm currently running a staging cluster, with plans to scale up by adding new hardware for a production cluster as well. Maintaining two clusters ensures I stay in the habit of separating environments.

I’ve developed an interest in mini PCs because of their ergonomic design and relatively low cost when purchased refurbished from a reseller. These mini PCs serve as worker nodes, as they lack built-in batteries. For control-plane nodes, however, I use a laptop with a healthy battery to prevent shutdowns caused by power outages or other issues. That said, I’m not opposed to turning to virtual machines to scale up further if necessary.

### Staging

This is the place where I can destroy things freely. Databases in staging don't contain data. In staging I allow workload pods to be scheduled on the control plane.

* controlplane-1    SAMSUNGN P470R5E-X02CL i5-3230M/8GB/1TB HDD (Functional Battery)
* worker-1          HP PRODESK MINI 600 G2, i3-6100T/8GB/240GB SSD (Reacconditioned)
* worker-2          SONY VAIO PCG 61311u i3/4GB/120GB SSD (Functional Battery)

I also use a IdeaPad 3 15ARH05 with 16GB of memory running Windows with WSL2. This is my personal machine.

### Production

In development...

## Databases

In development...

## Secrets

* Secrets are synced to Azure Key Vault
* SAS tokens for Storage Account Access

## Repo Structure

Set up the repo according to this guide:

https://fluxcd.io/flux/guides/repository-structure/

And following the following examples:

https://github.com/fluxcd/flux2-kustomize-helm-example
https://github.com/yoandl/fluxv2-infrastructure-stack-example

The namespaces folder in the root of the repository clarifies the active processes managed by the clusters.
