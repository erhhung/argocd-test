# argocd-test

## `root-appset.yaml`

Creates root apps for each environment (`dev` and `test`) in the main cluster where Argo CD is installed (`in-cluster`). Each root app (`app-of-apps-dev` and `app-of-apps-test`), in turn, deploys a Helmfile release ([`/root-helmfile`](./root-helmfile)) using the root Helm chart ([`/root-chart`](./root-chart)).

The root Helm chart creates another appset containing two apps (`app1` and `app2`) in the main cluster. Each app (`dev-app1` and `dev-app2`, and `test-app1` and `test-app2`), in turn, deploys a standard Helm release ([`/app-charts`](./app-charts)) in vClusters for each environment (`vcluster-dev` and `vcluster-test`) using corresponding values files ([`/app-values`](./app-values)).

## `guest-appset.yaml`

Creates two apps, `guestbook-dev` and `guestbook-test` ([`/operators`](./operators)), in local `in-cluster` using the `Guestbook` CRD deployed by the local Operator SDK project **`guest-operator`** _(see `~/dev/learning/kubernetes/operators/helm/NOTES`)_.
