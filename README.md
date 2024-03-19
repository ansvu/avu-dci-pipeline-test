# avu-dci-pipeline-test
This is dci-pipeline test and exploration

## Launching a DCI job with dci-pipeline-schedule

```ShellSession
$ export KUBECONFIG=/var/lib/dci-openshift-app-agent/kubeconfig
```

For only the workload with one-shot preflight+helmchart+merge:

```ShellSession
$ KUBECONFIG=$KUBECONFIG dci-pipeline-schedule certify-oneshot-automation
```

To run only the workload preflight:

```ShellSession
$ KUBECONFIG=$KUBECONFIG dci-pipeline-schedule container-e2e
```

To run only the workload chart-verifer (report.yaml):

```ShellSession
$ KUBECONFIG=$KUBECONFIG dci-pipeline-schedule helmchart-verifier-report
```

To run the workload create helmchart project:

```ShellSession
$ KUBECONFIG=$KUBECONFIG dci-pipeline-schedule create-helmchart
```

To run the workload create openshift-cnf vendor-validate:

```ShellSession
$ KUBECONFIG=$KUBECONFIG dci-pipeline-schedule create-openshift-cnf
```

## How to test PR
```ShellSession
$ dci-pipeline-check https://github.com/redhatci/ansible-collection-redhatci-ocp/pull/213 $KUBECONFIG container-hooks
```

