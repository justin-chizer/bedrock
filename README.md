# Omakase

We are living in a period of a virtual cambrian explosion of cloud native platform projects that individually promise to greatly improve our lives as developers. At the same time, it is currently very difficult to start from stratch and stitch all of these projects together into a coherent whole.

In Japanese, Omakase means "I'll leave it up to you" and is commonly used to trust a chef to design a dining experience for you that best utilizes their culinary skills and minimizing of stress on you so you to make this determination from looking at a large menu and triangulating what is best given the season.

In that vein, this project is our humble attempt to combine the collective wisdom of our cloud native community into a recipe for building best practice cloud native Kubernetes clusters based on the real world experience that we have of deploying cloud native applications at Microsoft with our largest customers. That said, we do not claim to have all the answers (and recognize that there many pieces missing) and would greatly appreciate your ideas and pull requests.

## What's included in the box?

Omakase is a currently set of Terraform based devops scripts for automated deployment of the best production-ready cloud native platforms on a Kubernetes cluster including:

Cluster Management

-   [Kured](https://github.com/weaveworks/kured) (automatic cordon/drain/reboot after node level patches are applied)

Monitoring

-   [Prometheus](https://prometheus.io/) metrics monitoring and aggregation
-   [Grafana](https://grafana.com/) metrics visualization with Kubernetes monitoring dashboards preconfigured

Log Management

-   [Fluentd](https://www.fluentd.org/) log collection and forwarding
-   [Elasticsearch](https://www.elastic.co/) log aggregation
-   [Kibana](https://www.elastic.co/products/kibana) querying and visualization

Ingress

-   [Traefik](https://traefik.io/) ingress controller

## Getting Started

1. Install the following tool dependencies per their instructions below for your platform and ensure that they are in your path.

-   [terraform](https://www.terraform.io/intro/getting-started/install.html)
-   [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
-   [helm](https://helm.sh/)

2. If you haven't, create a new Kubernetes cluster with RBAC enabled and ensure that it is the default context `kubectl` is using.

3. Clone this project locally:

```
$ git clone https://github.com/Microsoft/omakase
```

4. Check that everything is setup correctly:

```
$ tools/check-prereqs
```

5. Deploy with the dev sized environment! (This will take a while. I recommend making yourself a delicious cup of coffee as a reward.)

```
$ ./deploy dev
```

6. Take it for a test spin!

```
$ tools/grafana
```

Grafana is already connected to our cluster's Prometheus service and we've included a couple of dashboards so you can start monitoring the critical metrics in your Kubernetes cluster right away.

```
$ tools/kibana
```

Omakase has configured a full Fluentd, Elasticsearch, and Kibana logging stack ready for you to create your first index and start querying and visualizing text logs immediately.

```
$ tools/traefik
```

Traefik is configured as an ingress controller and it includes a management console for monitoring the health and performance of your externally exposed services.

# Contributing

This project welcomes contributions and suggestions. Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.microsoft.com.

When you submit a pull request, a CLA-bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., label, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

For project related questions or comments, please contact (Tim Park)[https://github.com/timfpark].