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

To find the Rancher LB Endpoint, navigate to "Stacks" > "User" from the navigation bar in Rancher. Then select the name of the stack you created. Find the service named `api-lb` and then click the info icon next to it. This should bring up a panel which has a section called "Ports". The IP of the endpoints should be here.

See https://github.com/iron-io/functions#quickstart for more details on using IronFunctions.
