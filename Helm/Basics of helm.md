# Helm


- Helm is a package manager for kubernetes.

- It helps to install applications on kubernetes.

- Helm is part of CNCF projects.


## Three big concepts

- **Helm charts**: 
  - Helm uses a pacakging format called charts.
  
  - A chart is a collection of files that describe a related set of K8 resources.

  - It contains all of the resource definitions necessary to run an application, tool, or service inside of a Kubernetes cluster.

- **Repository**: 
  - A *Repository* is the place where charts can be collected and shared. It's like *Perl's CPAN archive* or the *Fedora Package Database*, but for Kubernetes packages.

  - The charts of all the images used by Helm are stored in a registry called **Helm workspace**.

- **Release**:
  - A Release is an instance of a chart running in a Kubernetes cluster. 
  
  - One chart can often be installed many times into the same cluster. And each time it is installed, a new release is created.

Helm can:

- Install software.

- Automatically install software dependencies.

- Upgrade software.

- Configure software deployments.

- Fetch software packages from repositories.

Helm provides this functionality through the following components:

- A command line tool, ```helm```, which provides the user interface to all Helm functionality.

- A companion server component, ```tiller``` (V2 has Tiller. V3 this component has been removed), that runs on your Kubernetes cluster, listens for commands from helm, and handles the configuration and deployment of software releases on the cluster.

- The Helm packaging format, called charts.

- An official curated charts repository with prepackaged charts for popular open-source software projects.


## Charts directory structure.

Helm packages are called charts, and they consist of a few YAML configuration files and some templates that are rendered into Kubernetes manifest files. Here is the basic directory structure of a chart:

- package-name/
  - charts/
  - templates/
  - chart.yaml
  - LICENSE
  - README.md
  - requirements.yaml
  - values.yaml

These directories and files have the following functions:

- **charts/:** Manually managed chart dependencies can be placed in this directory, though it is typically better to use requirements.yaml to dynamically link dependencies.

- **templates/:** This directory contains template files that are combined with configuration values (from values.yaml and the command line) and rendered into Kubernetes manifests. The templates use the Go programming language’s template format.

- **Chart.yaml:** A YAML file with metadata about the chart, such as chart name and version, maintainer information, a relevant website, and search keywords.

- **LICENSE:** A plaintext license for the chart.

- **README.md:** A readme file with information for users of the chart.

- **requirements.yaml:** A YAML file that lists the chart’s dependencies.

- **values.yaml:** A YAML file of default configuration values for the chart.

## Chart Repositories

A Helm chart repo is a simple HTTP site that serves an ```index.yaml``` file and ```.tar.gz``` packaged charts. The helm command has subcommands available to help package charts and create the required ```index.yaml``` file. These files can be served by any web server, object storage service, or a static site host such as GitHub Pages.

Helm comes preconfigured with a default chart repository, referred to as ```stable```. This repo points to a Google Storage bucket at ```https://kubernetes-charts.storage.googleapis.com.``` The source for the stable repo can be found in the helm/charts Git repository on GitHub.

Alternate repos can be added with the ```helm repo add``` command.


## Chart Configuration

A chart usually comes with default configuration values in its values.yaml file. Some applications may be fully deployable with default values, but you’ll typically need to override some of the configuration to meet your needs.

The values that are exposed for configuration are determined by the author of the chart. Some are used to configure Kubernetes primitives, and some may be passed through to the underlying container to configure the application itself.

```
values.yaml

service:
  type: ClusterIP
  port: 3306

```

These are options to configure a Kubernetes Service resource. You can use ```helm inspect values chart-name``` to dump all of the available configuration values for a chart.

These values can be overridden by writing your own YAML file and using it when running ```helm install```, or by setting options individually on the command line with the ```--set``` flag. You only need to specify those values that you want to change from the defaults.

A Helm chart deployed with a particular configuration is called a release. 

## Creating Charts

If you can’t find an existing chart for the software you are deploying, you may want to create your own. Helm can output the scaffold of a chart directory with ```helm create chart-name.``` This will create a folder with the files and directories given above in Charts session.

From there, you’ll want to fill out your chart’s metadata in Chart.yaml and put your Kubernetes manifest files into the templates directory. You’ll then need to extract relevant configuration variables out of your manifests and into values.yaml, then include them back into your manifest templates using the templating system.

The helm command has many subcommands available to help you test, package, and serve your charts.

## list deployed helm charts

```
$ ./helm3 list -n grafana

NAME   	NAMESPACE	REVISION	UPDATED                                	STATUS  	CHART         	APP VERSION
grafana	grafana  	1       	2021-06-07 10:00:40.165633666 +0000 UTC	deployed	grafana-6.11.0	7.5.5      
$ 
```