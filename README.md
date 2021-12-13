![image](../images/confluent-logo-300-2.png)

# Overview

This Confluent Cloud Quickstart demo is based on the [Confluent Platform Quickstart](https://github.com/confluentinc/examples/tree/7.0.0-post/cp-quickstart)

![image](images/quickstart.png)

You can use this quickstart demo to setup Confluent Cloud demo within your Confluent Cloud account.

# Prerequisites

* Create a user account in [Confluent Cloud](https://www.confluent.io/confluent-cloud/tryfree/).
* Local install of the [Confluent CLI](https://docs.confluent.io/confluent-cli/current/install.html) v2.2.0 or later.

# Setup

* Clone the examples GitHub repository and check out the 7.0.0-post branch.
```bash
git clone https://github.com/hendrasutanto/examples
cd examples
git checkout 7.0.0-post
```

* Change directory to the cp-quickstart:
```bash
cd cp-quickstart
```

* Log in to Confluent Cloud with the command confluent login, and use your Confluent Cloud username and password. The --save argument saves your Confluent Cloud user login credentials or refresh token (in the case of SSO) to the local netrc file.
```bash
confluent login --save
```

# Run demo

## Confluent Cloud

* This quickstart for Confluent Cloud leverages 100% Confluent Cloud services, including a [ksqlDB application](statements-cloud.sql) which builds streams and tables using Avro, Protobuf and JSON based formats. After logging into the Confluent CLI, run the command below and open your browser navigating to https://confluent.cloud. Note: the demo creates real cloud resources and incurs charges.

```bash
./start-cloud.sh
```

* The above command will create a new environment in Confluent Cloud with the name "GSKO". If you have an existing environment with the same name, the script will fail to run.

### Advanced usage

You may explicitly set the cloud provider and region. For example:

```bash
CLUSTER_CLOUD=aws CLUSTER_REGION=us-west-2 ./start-cloud.sh
```

Here are the variables and their default values:

| Variable | Default |
| --- | --- |
| CLUSTER_CLOUD | aws |
| CLUSTER_REGION | us-west-2 |

### Cleaning Up

To destroy this demo and its Confluent Cloud resources, call the bash script stop-cloud.sh and pass in the client propoerties file auto-generated in the step above. By Default, this deletes all resources, including the Confluent Cloud environment specified by the service account ID in the configuration file.

```bash
./stop-cloud.sh stack-configs/java-service-account-<SERVICE_ACCOUNT_ID>.config
```

Any Confluent Cloud example uses real Confluent Cloud resources. After you are done running a Confluent Cloud example, manually verify that all Confluent Cloud resources are destroyed to avoid unexpected charges.
