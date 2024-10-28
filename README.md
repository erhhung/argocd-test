# argocd-test

## `root-appset.yaml`

Deploys root apps for each environment (`dev`=`in-cluster` and `test`=`do-sfo2-k8s-basic`), whereby each root app deploys a root chart ([`/root-chart`](./root-chart)) that, in turn, deploys an appset containing two Helm chart apps ([`/app-charts`](./app-charts)) using corresponding values files ([`/app-configs`](./app-configs)).

## `guest-appset.yaml`

Deploys two apps, `guestbook-dev` and `guestbook-test` ([`/operators`](./operators)), in local `in-cluster` using the `Guestbook` CRD deployed by the local Operator SDK project **`guest-operator`** _(see `~/dev/learning/kubernetes/operators/helm/NOTES`)_.
