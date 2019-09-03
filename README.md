# Sample Controller(Foo Controller)

This Controller is developed by Operator SDK v0.10.0

技術書典7で頒布した「実践入門 Kubernetesカスタムコントローラへの道」の第六章に掲載したサンプルコード用のリポジトリです。

## What is this Controller

This Controller reconcile foo custom resource.

Foo resource owns deployment object.

We define foo.spec.deploymentName & foo.spec.replicas.
When we apply foo, then deployment owned by foo is created.

If we delete deployment object like 'kubectl delete deployment/\<deployment name\>',
foo reconcile it and the deployment is created again.

Or if we scale deployment object like 'kubectl scale deployment/\<deployment name\> --replicas 0',
foo reconcile it and the deployment keeps the foo.spec.replicas.

## How to run

Clone source code

```
$ mkdir -p $GOPATH/src/github.com/govargo
$ cd $GOPATH/src/github.com/govargo
$ git clone https://github.com/govargo/sample-controller-operatorsdk.git
$ cd sample-controller-operatorsdk
```

Run localy

```
$ kubectl apply -f deploy/crds/samplecontroller_v1alpha1_foo_crd.yaml
$ OPERATOR_NAME=foo-controller operator-sdk up local
$ kubectl apply -f deploy/crds/samplecontroller_v1alpha1_foo_cr.yaml
```

Run container as Deployment

```
$ kubectl apply -f deploy/crds/samplecontroller_v1alpha1_foo_crd.yaml
$ kubectl apply -f deploy/
$ kubectl apply -f deploy/crds/samplecontroller_v1alpha1_foo_cr.yaml
```

## Reference

This project is inspired by

 * https://github.com/kubernetes/sample-controller
