# Capsule8 Helm Chart

This is a chart to install Capsule8 in a kubernetes cluster.

## Install Helm

A precursor to installing Capsule8 with [Helm](https://github.com/kubernetes/helm) is installing Helm itself. If you do not have Helm installed on the machine with which you will be connecting to your cluster, follow [the installation instructions](https://docs.helm.sh/using_helm/#installing-helm) followed by the [quickstart guide](https://docs.helm.sh/using_helm/#quickstart-guide) from Helm. This is an easy process where the binary for Helm is installed on the local machine which automatically uses the kubernetes configuration file to connect to the desired cluster.

Once Helm is installed and has been initialized with the target cluster, it will be used to install Capsule8 in a single command.

## Simple Installation

The simplest version of a helm install of Capsule8 will be the following command.

```
helm install .
```

This command will take all of the default values in the `helm-chart/values.yaml` file and create all of the resources described in `helm-chart/templates`. Starting with that basic installation, any variations on the default values can be adjusted either in directly editing the `helm-chart/values.yaml` file, or at the command line as arguments. For most uses the bare default values will not be sufficient. At a minimum the `image` and `tag` values for most Capsule8 components will need to be set for a proper installation.

## Setting Values at the Command Line

When installing with values other than the default ones all that is needed is the name of the value and the `--set` argument.
This example sets the sensor image as `my-docker/repository/capsule8-sensor:0.1.58`:

```
helm install . --set repository=my-docker/repository --set tag=0.1.58
```

### Release Naming

The release name is the only exception to the `--set` convention. The release name is instead set by the `--name` flag. By default Helm sets a release name to every installation. If a release name is not explicitly set, Helm will auto generate a whimsical name involving animals and attributes. To install Capsule8 with the release name `my-name-capsule8` run the following:

```bash
helm install --name my-name .
```

### Capsule8 Values to Set

When installing Capsule8 most values are taken care of and little additional configuration should be necessary. There are, however, a few sets of values which will need to be set either through the `helm-chart/values.yaml` file, or at the command line as arguments.

