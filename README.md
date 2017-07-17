# electrumx-kubernetes
Kubernetes config files for Electrumx

## How to deploy

```
$ kubectl create ns electrumx
$ kubectl create -f electrumx-monacoin.configmap.yaml
$ kubectl create -f electrumx-monacoin.svc.yaml
$ kubectl create -f electrumx-monacoin.deploy.yaml
```

(And you may need to setup your load balancer. Ask your network administorators for more details.)

After 10 minutes and more.

```
$ curl http://{your external IP}:50001/
```

You will get the expected error like this.

```
{"jsonrpc": "2.0", "id": null, "error": {"message": "cannot decode JSON: Expecting value: line 1 column 1 (char 0)", "code": -32700}}
```

## Additional info

You may need to setup the load balancer on your cloud.
There is no config for Ingress.

All db directories are mounted as `emptyDir`.
Modify to use another volume drivers if you want to keep datum into persistent storages.

There is no settings for HTTPS. Our team is planning to implement Let's Encrypt support. (Due date is unknown, sorry).


## How to contribute

Pull requests are welcome.

