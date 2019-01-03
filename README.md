# OpenShift Applier for the Strimzi Operator + a Kafka Cluster

This is an OpenShift applier inventory.

## Parameters

Make sure that `inventory/group_vars/all.yml` contains the project you would like to deploy to, and that `params/kafka_cluster` contains the desired name of the new cluster.

Additional parameters for cluster/PV sizing and such are available in `templates/kafka_cluster.yaml`, but are defaulted to a reasonable value for you.

Note that the Strimzi operator supports many more parameters, but these seemed the most logical to include in the template at this time.

## Usage

Right now limited to using ansible on your localhost.

1. `[.openshift-applier]$ ansible-galaxy install -r requirements.yml --roles-path=roles --f`

2. `[.openshift-applier]$ ansible-playbook apply.yml -i inventory/`

See the inventory for the filter tag options.

## Final Remarks

`templates/strimzi_operator.yaml` is a bit of a beast. I would be careful about modifying it. It is essentially [this file](https://github.com/strimzi/strimzi-kafka-operator/releases/download/0.9.0/strimzi-cluster-operator-0.9.0.yaml) turned into a template, so that we can deploy to any project we desire. `templates/kafka_cluster.yaml` should be more flexible and approachable.