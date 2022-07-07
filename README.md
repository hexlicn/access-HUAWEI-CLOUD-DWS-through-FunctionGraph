# access HUAWEI CLOUD GaussDB&(DWS) via FunctionGraph

I'm trying to create HUAWEI CLOUD FunctionGraph function that runs queries on Data Warehouse - GaussDB(DWS). How can I do this?

## Resolution


### Prerequisites

Before you create a Lambda function, you must set up the following VPC:

1. Create a [VPC with a private subnet](https://support.huaweicloud.com/intl/en-us/qs-vpc/en-us_topic_0017816228.html). 

2. Create a private [Data Warehouse cluster](https://support.huaweicloud.com/intl/en-us/qs-vpc/en-us_topic_0017816228.html) selecting the VPC and subnet that you just created.



### Create your FunctionGraph function

To [create a FunctionGraph function](https://support.huaweicloud.com/intl/en-us/qs-functiongraph/functiongraph_04_0101.html) that queries your GaussDB(DWS) cluster, perform the following steps:

1. Open the [FunctionGraph console](https://console-intl.huaweicloud.com/functiongraph/?agencyId=e75efe0129c743b593ea9f85fc15a894&region=af-south-1&locale=en-us#/serverless/dashboard).

2. Choose Create function.

3. Update the following fields:

Function name: Enter a custom name.
Agency: Create a agency delegate FunctionGraph to access other Huawei Cloud services. For example, an agency is required when FunctionGraph accesses services GaussDB(DWS)
Enterprise Project: Create a new enterprise for resource management, otherwise you can keep the default one.
Runtime: Enter your code environment. (The examples from this note are compatible with "Python 3.6", please mention that different regions may have different Python library version.)

4. Choose Create function.



### Add Python code to your FunctionGraph function

1. In the FunctionGraph console, choose Code.

2. Paste the sample code (see "sample_query_gaussdb_dws.py") into the Code box.



### Post Configuration

1. Before you test the function, you need to upload dependent Python library and open VPC for interanl accessing to GaussDB(DWS).

2. Open the [FunctionGraph console](https://console-intl.huaweicloud.com/functiongraph/?agencyId=e75efe0129c743b593ea9f85fc15a894&region=af-south-1&locale=en-us#/serverless/dashboard).

3. Choose Dependencies, and "Create Dependency", give it a "Name", Runtime choose Python 3.6, and Upload the zip "psycopg2-2_9_3-py36-EulorCompile.zip" (If you're in Python 3.9 complier, please come to Huawei Cloud support to get the Python 3.9 library accordingly)

4. Back to "Function List" and choose your function that you just created, within "Dependencies" under code block, click "Add" and in the "Private" sub-menu, choose the Python 3.6 library you've uploaded just now.

5. Navigate to "Configuration" menu, choose VPC, open the "Status", and choose the VPC that resident the same with GaussDB(DWS), save it.

6. Now you can test the function running.
