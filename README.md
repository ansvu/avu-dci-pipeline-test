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

Output:
```ShellSession
$ oc -n oneshot get po -w
NAME                                    READY   STATUS    RESTARTS   AGE
finalchart-3h7v3xu07e-69cc977ff-lvqq9   0/1     Pending   0          0s
finalchart-3h7v3xu07e-69cc977ff-lvqq9   0/1     Pending   0          0s
finalchart-3h7v3xu07e-69cc977ff-lvqq9   0/1     Pending   0          0s
finalchart-3h7v3xu07e-69cc977ff-lvqq9   0/1     ContainerCreating   0          0s
finalchart-3h7v3xu07e-69cc977ff-lvqq9   0/1     ContainerCreating   0          1s
finalchart-3h7v3xu07e-69cc977ff-lvqq9   1/1     Running             0          1s
finalchart-3h7v3xu07e-69cc977ff-lvqq9   1/1     Terminating         0          2s
finalchart-3h7v3xu07e-69cc977ff-lvqq9   0/1     Terminating         0          4s
finalchart-3h7v3xu07e-69cc977ff-lvqq9   0/1     Terminating         0          4s
finalchart-3h7v3xu07e-69cc977ff-lvqq9   0/1     Terminating         0          4s

DCI CI Job(finalchart_0_report.yaml):
https://www.distributed-ci.io/jobs/2433c2dd-cde4-40dd-9682-49ea9eef1132/files
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

