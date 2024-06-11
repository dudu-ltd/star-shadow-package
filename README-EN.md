# Desktop Client for StarShadow Graph Database

<p align="center">
    <img src="./logo.png"></img>
</p>

Welcome to the world of StarShadow. If you are a new player of StarShadow or a graph database, or not a developer. You can follow the following documents to use StarShadow without deploying your own graph database.

## Download Software

### Download via Git【Recommended】

-  windows

    ```shell
    git clone -b windows --single-branch https://gitee.com/dudu-ltd/star-shadow-package.git
    ```
- macos
    ```shell
    # Coming soon
    ```

- linux
    ```shell
    # Coming soon
    ```


### Download ZIP

#### Links
- Windows: [StarShadow-win-v1.0.0-beta.zip](https://github.com/dudu-ltd/star-shadow-package/archive/refs/tags/v1.0.0-beta.zip)
- macOS: Coming soon
- linux: Coming soon

#### Installation
The current version uses the green version, which can be directly unzipped to the directory you want to install. Enter the folder, and then find the 【与众不同的那个图标.exe】 and double-click to open it.

Use WeChat to complete registration and login.

## Quick Start Steps

If you don't have your own graph database yet, or want to know our recommended usage, you can get started with StarShadow through the following steps.

:::info
The sample project uses the trial version of [NebulaGraph 3.4.0 provided by Alibaba Cloud Computing Nest](https://computenest.aliyun.com/market/service-39f4f251e9484369a778?spm=5176.29141018.J_PGjKnplUAs1kXQYVyQamo.9.7b625d102SpFHx), which is valid until 【2024-06-22】. You can also quickly experience NebulaGraph graph database through this method.
:::

1. Click the link to the [sample project](https://gitee.com/dudu-ltd/star-shadow-sample)
2. Find 【Clone/Download】 and click
3. In the pop-up window, find 【Download ZIP】 and click
4. Place the downloaded zip file in the folder where you want to place the StarShadow data
5. Unzip the zip file to the 【current folder】
6. Return to the opened StarShadow graph database client
    1. Find 【File】 in the upper left corner
    2. Click 【Open Folder】
    3. Select the 【star-shadow-sample-main】 folder that was unzipped in step 5
    4. Click 【Select Folder】 in the lower right corner of the pop-up window
7. At this point, you can experience StarShadow through the sample project

:::danger Danger
In step 3 above, you can also use git clone, but to avoid you in the subsequent use process, mistakenly submit the connection parameters of the private database, please try to use the download ZIP method.
If you use git to manage the StarShadow workspace in future projects, please be careful when submitting to the open source repository. Because it contains the connection information of the database.
:::

## Using the Sample Project

1. In the opened left navigation tree, right-click to manage the corresponding schema;
2. In the specific data table (tag, edge), the serial number column supports right-click to pop up the interface to complete the operation on the data;
3. Under the 【Query】 tree node, you can select 【MATCH】 to experience the script we prepared for you this time, which includes the following functions:
    1. Based on nGQL, we have extended the parameter template. You can switch between multiple sets of parameters by clicking on the serial number 1, 2, 3... on the right side of the parameter panel in the code editing area. Select which set of parameters, click 【Run】, and the query script will use which set of parameters to complete the data query:
    2. In the example usage of 【MATCH】, you can experience the merged table header, the visualization of the node relationship diagram, and the visualization of the path data
    3. In the example usage of 【GET SUBGRAPH】, you can experience that each column in the result is composed of tables, and you can open a pop-up composed of tables by clicking on a cell, thereby realizing the reading of table data.

## Finally
We will continue to supplement the common scripts of the graph database through the sample project in the future. If you have formed a useful template in the subsequent process and want to share it with others, please contact us.

So far, we have introduced some basic usage here. If you want to know how the graphical interface operation works, please go to the next stop: [Guide](./help.html)

We hope that our work can help you remove some obstacles in the process of exploring the graph, and we hope that we can always accompany you.

