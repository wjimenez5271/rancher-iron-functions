# Iron Functions on Rancher
An implementation of [IronFunctions](https://github.com/iron-io/functions) on [Rancher](http://rancher.com). This implementation helps you to build "serverless" applications on Rancher.

Uses Postgres for data persistence and Redis for queueing. The stack provides two interfaces, a UI and an API HTTP interface.

### Requirements
Rancher container environment. See [Rancher QuickStart Guide](http://docs.rancher.com/rancher/v1.5/en/quick-start-guide/) for details on setting this up

### Usage
Create a stack in rancher using `docker-compose.yml` & `rancher-compose.yml`. Using the [Rancher CLI](https://docs.rancher.com/rancher/v1.2/en/cli/) from the root directory of this repo run:

```
rancher up -s iron-functions -d
```

Once it is running, you should be able to interface with the API at

```
http://<RANCHER_LB_ENDPOINT>:8080
```

and the UI at

```
http://<RANCHER_LB_ENDPOINT>:4000
```

To find the Rancher LB Endpoint, navigate to `Stacks` > `User` from the navigation bar in Rancher. Then select the name of the stack you created. Find the service named `api-lb` and then click the info icon next to it. This should bring up a panel which has a section called "Ports". The IP of the endpoints should be here.

See https://github.com/iron-io/functions#quickstart for more details on using IronFunctions.

### Scaling
By default, the stack creates 2 instances of `iron/functions`. As request count increases you will need to scale this count, see this guide for more information on scaling best practices: https://github.com/iron-io/functions/blob/master/docs/operating/production.md

The `postgres` and `redis` containers in this stack are QTY 1. For high availability and performance these would need to be scaled as well, however replication/clustering would need to be addressed.

### What do I do with this?
Once you got the stack running, its time to start writing your own functions! See https://github.com/iron-io/functions#write-a-function or for a quick demo see: https://github.com/wjimenez5271/iron-func-demo.
