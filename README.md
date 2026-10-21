# Data Product Publishing \_ Sample Data

*Sample Data for publishing File and Streaming Data Products*

This repository contains a sample dataset that can be used to test the publication and exchange of Data Products through the DPN via the following integration pathways:

- **File-Based Data Product**
- **Streaming Data Product**

The sample can be used to validate the end-to-end process from onboarding data into the DPN and configuring the pipeline to support data exchange, to publishing the data product in the DSM so it is available on the DSM Data Catalogue for consumer to request access to it.

---

## Overview: Data Product Publishing Journey

*The following provides a summary of the steps involved in publishing a Data Product for sharing through the DPN and the DSM.*

*It is for readers understand the overall process and how the sample data can be used. For detailed implementation and configuration instructions, refer to the DPN Integration Playbook and associated guidance.*

## Step 1 - Add Data to the DPN

The data must first be made available within the Producer DPN using the appropriate storage mechanism.

### File-Based Data Product

1. Place the source file in the designated Producer DPN storage location, i.e. upload the file to the configured Storage staging container.
2. Confirm the file is available for processing by the DPN pipeline.

### Streaming Data Product

1. Create or identify the Kafka topic that will act as the source.
2. Publish test messages to the topic.
3. Confirm messages can be viewed in Kafka UI and are available for processing.

## Step 2 - Configure the DPN Data Pipeline

Once the source data is available, a DPN Data Pipeline must be configured in accordance with the **DPN Integration Playbook**. This configuration establishes the technical connection that the DSM Data Product will reference.

As part of the setup, the Kafka topic used by the gRPC Gateway is created for both File-Based and Stream-Based integration pathways. Record the topic name, as it must be entered when creating the Data Product in DSM (see Step 3.2).

## Step 3 - Create the Data Product in DSM

Once the DPN data pipeline has been configured and successfully tested, the Data Product can be created in DSM.

When creating the Data Product, it is important that the DSM configuration matches the configuration already established within the DPN.

The following information must align between DSM and the DPN configuration:

### 3.1 Integration Pathway

Select the integration pathway that matches the DPN pipeline that has been configured:

- **Stream-Based Data Product**
- **File-Based Data Product**

> **Note:** The integration pathway is defined by the Data Product Template. When creating your test Data Product for publication in pre-prod1, select **"Publish a Data Product against an Existing Template"** and choose the appropriate NESO-provided template:
>
> - ***Test Data Publication_File Transfer***
> - ***Test Data Publication_Streaming***

### 3.2 Kafka Topic

Enter the Kafka topic configured within the DPN pipeline.

> **Note:** The topic name entered in DSM must exactly match the topic configured within the Producer DPN. This ensures that requests made through DSM are routed to the correct data exchange pipeline.

### 3.3 Endpoint Configuration

Select the endpoint that will be used to exchange the Data Product.

> **Note:** The endpoint selected in DSM must:
>
> - *Be registered as an active Endpoint to your organisation within DSM (home/Your Organisation/DPN/Your Endpoint)*
> - *Be endpoint that supports the correct integration pathway being used by the data product*

## Step 4 - Publish the Data Product

Once configured, publish the Data Product within DSM. Publication makes the Data Product discoverable by authorised consumer organisations.

At this stage:

- The Data Product becomes available in the DSM Data Catalogue.
- Consumers can view metadata and request access.
