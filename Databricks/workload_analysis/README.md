# Databricks Workload Query notebook

## Overview
The following notebook [Databricks_workload_query.dbc](https://github.com/MobilizeNet/SnowConvertDDLExportScripts/tree/main.Databricks_workload_query.dbc) allows you to share information about your Databricks workspace workload without giving direct access to your system.

## How it works
- This notebook uses standard Databricks python API to gather minimal clusters, jobs, tasks, and runs information. 

- It is required to be executed by the workspace owner.

- The information is stored in PySpark dataframes and a few visualizations are provided for your perusal.
- If you decide to share the information, At the end of the notebook the dataframes are converted to CSV, and zipped. You can then press the **download zip** button to get the file.

## Steps
1. Open your Databricks workspace and creates an new notebook.
2. Open File menu and click import.
3. Select URL and paste ***https://github.com/MobilizeNet/SnowConvertDDLExportScripts/tree/main.Databricks_workload_query.dbc***
4. Follow notebook instructions.
   1. Install Databricks pypi dependency.
   2. Update configuration accordling with your cluster (host_url, and token). ***We Advise against using the token directly in the notebook. Please store it in a secret scope, using Databricks CLI***.  For more details [Databricks Authentication](https://docs.databricks.com/dev-tools/api/latest/authentication.html)

## Examples of tables and Visualizations

### Clusters
 ![Clusters Table](./images/clusters_table.png)

 ![Clusters Viz](./images/clusters_viz.png)

### Tasks
 ![Tasks Table](./images/task_table.png)


## Top Time-consuming jobs
 ![Top Time-consuming jobs](./images/top_timing_jobs_viz.png)

 ![Top Time-consuming jobs](./images/top_running_job_series_viz.png)


# DataBricks Export Scripts

This repository provides some simple scripts to help exporting your Databricks code 

## Version

Version 1.0
Release 2023-01-23

## Overview

There are several ways to extract your code from DataBricks. We will provide several alternatives. Choose the one that works better in your scenario.


## Extracting with the DBX Command Line Tool

The Databricks command line tool can be used in order to export your application code.
1. Open a terminal.
1. Install the databricks command line tool. Follow the instructions in the [documentation](https://docs.databricks.com/dev-tools/cli/index.html). In most cases just running `pip install databricks-cli` should be enough.
2. From the terminal, setup a pair of environment variables:
It should be something like this:
```
$ export DATABRICKS_HOST=https://adb-3333333354739464.4.azuredatabricks.net/
$ export DATABRICKS_TOKEN=dapi03d48985b96c7a777da4c50b060777b5
```
Adjust those variables to point to your databricks account.
3. You can then run:
```
databricks workspace list
```
that will show a listing like:
```
Users
Shared
Repos
```
4. Export a workspace. For example to export all the `Shared` workspace you can run:
```
$ databricks workspace export_dir "/Shared" "~/exportSharedWorkspace" -o
```
5. Zip the folder.
```
zip -r exportedWorkspace.zip ~/exportSharedWorkspace
```

# Reporting issues and feedback

If you encounter any bugs with the tool please file an issue in the
[Issues](https://github.com/MobilizeNet/SnowConvertDDLExportScripts/issues) section of our GitHub repo.

# License

These scripts are licensed under the [MIT license](https://github.com/MobilizeNet/SnowConvertDDLExportScripts/blob/main/SQLServer/LICENSE.txt).
