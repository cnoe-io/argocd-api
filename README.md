# ArgoCD API

Types for ArgoCD's Kubernetes API.

## Description

ArgoCD does not have a separate repository for its API types which means that any go application (such as a controller) which wishes to create Argo resources must import **all** of ArgoCD. Furthermore, ArgoCD imports private and older Kubernetes libraries which in the setting of a controller create major headaches such as the inability to use recent library versions and the need to specify a large number of library version overrides.

To overcome this, we have copied the API types for ArgoCD out to this separate Go module which can be depended on, with the specific goal of supporting the Kubernetes controller use case.

## READ THIS FIRST

All files here were copied from the Argocd project (https://github.com/argoproj/) and then modified to be able to build without ArgoCD as a dependency. This is not a great pattern and is a total hack. It is likely that this will be a maintanence nightmare as ArgoCD changes its API, so its not necessarily a good idea to make use of this module unless you know what you are getting in to. However, one mitigating factor is that while this library may break, the API types should match ArgoCD and therefore a better system to resolve this can be implemented without the need for downstream applications to update their usage.