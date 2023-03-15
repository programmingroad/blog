```
证书认证和token认证查看pod日志获取exec pod报401 ==> apiserver kubelet证书配置问题 因为上述操作需要访问kubelet
```

```
k top po 拿不到某些节点pod指标或者报错 ==> 通过kubectl get --raw /api/v1/nodes/$NODE_NAME/proxy/metrics/resource查看节点是否吐出指标，没有重启kubelet后解决

https://github.com/kubernetes-sigs/metrics-server/blob/master/KNOWN_ISSUES.md#kubelet-doesnt-report-pod-metrics
```