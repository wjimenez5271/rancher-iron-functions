# Iron Functions on Rancher
An implementation of [IronFunctions](https://github.com/iron-io/functions) on [Rancher](http://rancher.com)

Uses Postgres for data persistence and Redis for queueing 

### Usage
Create a stack in rancher using `docker-compose.yml` & `rancher-compose.yml`

Once it is running, you should be able to interface with the API at

```
http://<RANCHER_LB_ENDPOINT>:8080
```

and the UI at

```
http://<RANCHER_LB_ENDPOINT>:4000
```
