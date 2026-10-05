# Lab 2: Create and start the GoldenGate Extract process

## Introduction

In this lab, you use the GoldenGate Model Context Protocol (MCP) server to create and start the `EXFRAUD` Extract to capture data in real-time from the payment table stored in Oracle AI Autonomous Database. 

Estimated time: 15 minutes.

### About the Extract process

An Extract is a process that extracts, or captures, data from a source database.

### About the GoldenGate MCP Server

The GoldenGate MCP server provides tools to interact with Oracle GoldenGate deployments through the GoldenGate Administration REST APIs. It includes tools for administration, process lifecycle management, and operational monitoring. It enables end-to-end, AI agent-driven operational workflows.

### Objectives

In this lab, you learn to:

- Use the GoldenGate MCP server
- Add and run an Extract
- Verify the Extract configuration and status

### Prerequisites

- This lab assumes that you completed all preceding labs
- The OCI GoldenGate deployment is in the **Active** state
- The dashboard chat and its GoldenGate MCP operations flow are available

## Task 1: Connect to the Enterprise Fraud Monitoring Console

1. Find the Fraud Dashboard URL on the __LiveLabs Sandbox login page__.

2. Open the link or copy and paste it in your laptop browser and connect to the **Enterprise Fraud Monitoring Console**.

3. Click **Show** to maximize the **GoldenGate MCP + PAF Chat** panel if you minimized it previously.

   The chat panel is where you submit GoldenGate MCP requests throughout this lab.

    ![GoldenGate MCP and PAF Chat panel used to submit Extract requests](images/mcp-chat-list-extracts.jpg)

## Task 2: Discover the source connection

1. In the **GoldenGate MCP + PAF Chat** panel, submit the following requests.

   List domains

    ```text
    List the GoldenGate domains.
    ```

   List connections:

    ```text
    List the GoldenGate connections in the OracleGoldenGate domain.
    ```
   Confirm that the source connection is present. The expected connection name is:

    ```text
    ATP_Fraud_Source_Connection
    ```

## Task 3: Create the Extract

1. In the **GoldenGate MCP + PAF Chat** panel, submit the following requests.

    ```text
    List GoldenGate extracts.
    ```

In a brand new environment, it should return `No GoldenGate Extracts are configured.`

2. Create the Extract using the following prompt.

    ```text
    Create a new Extract called EXFRAUD using trail ft and the ATP connection. Capture data from table PAYMENT_TRANSACTION in schema YAN_POS.
    ```

Wait until the Extract ``EXFRAUD`` is created successfully before issuing another request. If the operations flow requests confirmation or missing parameters, provide them for this Extract.

## Task 4: Start and monitor the Extract

1. In the **GoldenGate MCP + PAF Chat** panel, submit the following requests.

   Start the Extract

    ```text
    Start extract EXFRAUD.
    ```

   Then verify its details and status:

    ```text
    Show details and status for extract EXFRAUD.
    ```

The Extract should be started successfully.

Confirm that the configured trail is `ft` and that the table statement refers to `YAN_POS.PAYMENT_TRANSACTION`.

If the Extract stops or abends, request its report:

    ```text
    Show extract report for EXFRAUD.
    ```

Review the actual error and resolve the reported issue before restarting. 

2. Go back to the OCI GoldenGate deployment in the OCI Console, click **Launch Console**.

3. If prompted, enter the username and password found on the __LiveLabs Sandbox login page__, then click **Sign In**.

4. Click **Extracts** then click **EXFRAUD**.

5. Click **Parameters** to review the Extract configuration created using the GoldenGate MCP server.

You may now __proceed to the next lab__.

## Acknowledgements

- **Author** - Shrinidhi Kulkarni
