# Service Mesh: Troubleshooting Tutorial Resources

Service Mesh: Troubleshooting Tutorial Resources

## 01 - Setup

- Modified params.env with the parameters provided by the Instructor at the beginning of this tutorial

```$bash
vi params.env
USER_NAMESPACE="userXX_namespace"
OCP_APPS_DOMAIN="apps.labs.mydomain.com"
```

## 02 - Deploy _Jump App_ Microservices

- Deploy _Jump App_ using an Openshift Template 

```$bash
oc process -f 02-jump-app-deploy/jump-app-template.yml --param-file=params.env --ignore-unknown-parameters | oc apply -f -
```

## 03 - Create _Jump App_ Istio Objects

- Deploy _Jump App_ Gateways using an Openshift Template 

```$bash
oc process -f 03-jump-app-flows/00-jump-app-gws.yaml --param-file=params.env --ignore-unknown-parameters | oc apply -f -
```

- Deploy _Jump App_ Virtual Services using an Openshift Template 

```$bash
oc process -f 03-jump-app-flows/01-jump-app-vss.yaml --param-file=params.env --ignore-unknown-parameters | oc apply -f -
```

- Deploy _Jump App_ Destination Rules using an Openshift Template 

```$bash
oc process -f 03-jump-app-flows/02-jump-app-drs.yaml --param-file=params.env --ignore-unknown-parameters | oc apply -f -
```

- Deploy _Jump App_ K8s Services using an Openshift Template 

```$bash
oc process -f 03-jump-app-flows/03-jump-app-services.yaml --param-file=params.env --ignore-unknown-parameters | oc apply -f -
```

- Create _ServiceMeshMember_ Object 

```$bash
oc process -f 03-jump-app-flows/04-jump-app-ns-smr.yaml--param-file=params.env --ignore-unknown-parameters | oc apply -f -
```

- Deploy _Jump App_ Routes using an Openshift Template 

```$bash
oc process -f 03-jump-app-flows/05-jump-app-routes.yaml --param-file=params.env --ignore-unknown-parameters | oc apply -f - -n istio-system
```

## 04 - Ingress Traffic Troubleshooting 

- Customize _Jump App_ with day 2 operations

```$bash
oc process -f 04-ingress-traffic-troubleshooting/00-jump-app-ingress-customization.yaml --param-file=params.env --ignore-unknown-parameters | oc apply -f 
```

- Modify _Jump App_ back-golang k8s service

```$bash
oc process -f 04-ingress-traffic-troubleshooting/01-jump-app-back-golang-svc.yaml --param-file=params.env --ignore-unknown-parameters | oc apply -f -
oc process -f 04-ingress-traffic-troubleshooting/01-jump-app-back-golang-svc.yaml --param-file=params.env --ignore-unknown-parameters | oc delete -f -
```

## 05 - Secure Traffic Troubleshooting 

 

## 06 - Egress Traffic Troubleshooting 


## Author Information

Asier Cidon @Red Hat

asier.cidon@gmail.com
