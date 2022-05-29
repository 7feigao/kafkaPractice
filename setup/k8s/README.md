1. setup cluster: `sh setup.sh`
2. setup cluster, allow access from ourside cluster:
   1. with LoadBalancer: `sh setup_loadBalancer.sh`
      * after setup in docker desktop k8s cluster, you can access cluster through `localhost:9094` from local.
   2. with NodePort: 
      1. with random port: `sh setup_NodePort_RandomPort.sh`
         * get services info by run `k get services`:
            ```log
            NAME                            TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)                      AGE
            kubernetes                      ClusterIP   10.96.0.1        <none>        443/TCP                      10d
            my-release-kafka                ClusterIP   10.97.221.225    <none>        9092/TCP                     7m7s
            my-release-kafka-0-external     NodePort    10.108.57.221    <none>        9094:31647/TCP               7m7s
            my-release-kafka-1-external     NodePort    10.96.132.83     <none>        9094:31508/TCP               7m6s
            my-release-kafka-2-external     NodePort    10.104.200.201   <none>        9094:30478/TCP               7m6s
            my-release-kafka-headless       ClusterIP   None             <none>        9092/TCP,9093/TCP            7m7s
            my-release-zookeeper            ClusterIP   10.105.189.33    <none>        2181/TCP,2888/TCP,3888/TCP   7m7s
            my-release-zookeeper-headless   ClusterIP   None             <none>        2181/TCP,2888/TCP,3888/TCP   7m7s
            ```
            from the log can find the random port, and can access the cluster from address: `localhost:30478,localhost:31647,localhost:31508`
1. refer to https://github.com/bitnami/charts/tree/master/bitnami/kafka
            https://github.com/bitnami/bitnami-docker-kafka
2. to access the brokers inside cluster from localhost, please refer to 
   * https://docs.bitnami.com/kubernetes/infrastructure/kafka/administration/external-access/
   * https://github.com/bitnami/charts/tree/master/bitnami/kafka#accessing-kafka-brokers-from-outside-the-cluster