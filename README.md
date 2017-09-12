# Iron Functions on Rancher
An implementation of [IronFunctions](https://github.com/iron-io/functions) on [Rancher](http://rancher.com). This implementation helps you to build "serverless" (also known as Functions as a Service) applications on Rancher.

Uses Postgres for data persistence and Redis for queueing. The stack provides two interfaces, a UI and an API HTTP interface. This blog post has more details about working with the stack: http://rancher.com/running-serverless-applications-rancher/

## Requirements
Rancher container environment. See [Rancher QuickStart Guide](http://docs.rancher.com/rancher/v1.5/en/quick-start-guide/) for details on setting this up

## Deploying

You first need to install Rancher, see above quick start guide for details on how to do this. Once you have rancher running, you can deploy IronFunctions as an [application stack](http://rancher.com/docs/rancher/v1.6/en/cattle/stacks/).

#### Using Rancher CLI
This uses the `docker-compose.yml` & `rancher-compose.yml` located in this repo.

1. Clone this repo locally

```
git clone https://github.com/wjimenez5271/rancher-iron-functions.git
```

2. Using the [Rancher CLI](https://docs.rancher.com/rancher/v1.2/en/cli/) from the root directory of this repo run:

```
rancher up -s iron-functions -d
```


#### Using the Community Catalog
1. Open the Rancher UI and select "Community Catalog" from the "Catalog" menu at the top
2. Use the search box in the upper right to find the IronFunctions catalog item
3. Select launch!

The code for this in the catalog can be found [here](https://github.com/rancher/community-catalog/tree/master/templates/iron-functions)

## First use

Once it is running, you should be able to interface with the API at

```
http://<RANCHER_LB_ENDPOINT>:8080
```

and the [UI](https://github.com/iron-io/functions-ui) at

```
http://<RANCHER_LB_ENDPOINT>:4000
```

To find the Rancher LB Endpoint, navigate to `Stacks` > `User` from the navigation bar in Rancher. Then select the name of the stack you created. Find the service named `api-lb` and then click the info icon next to it. This should bring up a panel which has a section called "Ports". The IP of the endpoints should be here.

See https://github.com/iron-io/functions#quickstart for more details on using IronFunctions.

### Scaling
By default, the stack creates 2 instances of `iron/functions`. As request count increases you will need to scale this count, see this guide for more information on scaling best practices: https://github.com/iron-io/functions/blob/master/docs/operating/production.md


### What can I do with this?
Once you got the stack running, its time to start writing your own functions! See https://github.com/iron-io/functions#write-a-function or for a quick demo see: https://github.com/wjimenez5271/iron-func-demo.

### Limitations
- Persistence: The database currently stores data in ephemeral container storage. For a production deploy you should consider using docker volumes or external database solution.
- HA: The `postgres` and `redis` containers in this stack are QTY 1. For high availability and performance these would need to be scaled as well, however replication/clustering would need to be addressed.

### Feedback

Using FaaS for something cool on top of Rancher? We'd love to hear about it. Have suggestions for how to make this beter? Let us know (or send a pull request :-) )

- [Rancher Users Slack](https://slack.rancher.io/)
- [Rancher Forums](https://forums.rancher.com/)


This project is based on https://github.com/iron-io/functions and work of the team at Iron.io. Thanks for the great work!
