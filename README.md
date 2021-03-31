# Line Logger

For every line of input provided to `lnlogger`, the time is printed followed by the line provided. If the input is paused for a second or more, lnlogger prints out one blank line. This effectively groups input lines into separate sections of 'activity'.

## Examples

`while true; do kubectl get pods -w; echo "-- Restarting --"; done | lnlogger`
Outputs:
```
[30/03/2021 11:05:44] NAME                                                    READY   STATUS    RESTARTS   AGE
[30/03/2021 11:05:44] alertmanager-kps-kube-prometheus-stack-alertmanager-0   2/2     Running   22         32d
[30/03/2021 11:05:44] kps-prometheus-node-exporter-9bpph                      1/1     Running   12         32d
[30/03/2021 11:05:44] prom-promtail-lt7tp                                     1/1     Running   9          28d
[30/03/2021 11:05:44] prometheus-kps-kube-prometheus-stack-prometheus-0       2/2     Running   19         28d
[30/03/2021 11:05:44] test-5978c9d4bd-zdnms                                   1/1     Running   0          22h
[30/03/2021 11:05:44] web-5b9845df5-hvvq2                                     1/1     Running   0          22h
[30/03/2021 11:05:45] 
[30/03/2021 11:11:59] cicd-shared-secrets-1-k0z-fjkq2                         0/1     Pending   0          0s
[30/03/2021 11:12:00] 
[30/03/2021 11:12:00] cicd-shared-secrets-1-k0z-fjkq2                         0/1     Pending   0          1s
[30/03/2021 11:12:01] cicd-shared-secrets-1-k0z-fjkq2                         0/1     ContainerCreating   0          2s
[30/03/2021 11:12:02] 
[30/03/2021 11:15:30] cicd-shared-secrets-1-k0z-fjkq2                         1/1     Running             0          3m31s
[30/03/2021 11:15:31] 
[30/03/2021 11:15:54] cicd-shared-secrets-1-k0z-fjkq2                         0/1     Completed           0          3m55s
[30/03/2021 11:15:55] 
[30/03/2021 11:15:57] cicd-shared-secrets-1-k0z-fjkq2                         0/1     Terminating         0          3m58s
[30/03/2021 11:15:57] cicd-shared-secrets-1-k0z-fjkq2                         0/1     Terminating         0          3m58s
[30/03/2021 11:15:58] 
```

## Motivation

I often found myself tabbing back and forth between terminal windows and hitting enter in the middle of a tail -f, just to distinguish logs from a particular action I was doing in another window. lnlogger has bypassed that need entirely and provides the practical interface needed to more quickly decipher logs.
