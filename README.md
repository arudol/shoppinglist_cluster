# K8 to run a shoppinglist with backend

K8 yaml files and argo cd integration for the shoppinglist application https://github.com/arudol/shoppinglist, including a mongodb backend. 

# Structure

## app
K8 yaml config for the shoppinglist frontend (including LoadBalancer)

## mongo
K8 yaml config for the shoppinglist mongodb backend (including internal Service). Can either be with mongo as a deployment, or with mongo as stateful set bound to a persistent volume. For the latter, apply both `mongo_statefulset_with_volume.yaml` and `persistent_volume.yaml`. 

## namespace
Both the app as well as the backend expect a namespace `shoppinglinst`. If they are deployed via argo, this will be automatically created. Otherwise, apply `namespace.yaml` to create it.

## argo cd configs
Three argo configs are available: 
- `application_argo`: Will apply and monitor the deployment of the frontend, stored in `shoppinglist_app.yaml`
- `backend_argo`: Will apply and monitor mongodb in a deployment, stored in `mongo_deployment.yaml`
- `backend_pv:argo`: Will apply and monitor mongodb as a stateful set connected to a pv, stored in `mongo_statefulset_with_volume.yaml` and `persistent_volume.yaml`