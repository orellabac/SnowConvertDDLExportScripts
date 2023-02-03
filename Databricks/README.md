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

## Reporting issues and feedback

If you encounter any bugs with the tool please file an issue in the
[Issues](https://github.com/MobilizeNet/SnowConvertDDLExportScripts/issues) section of our GitHub repo.

## License

These scripts are licensed under the [MIT license](https://github.com/MobilizeNet/SnowConvertDDLExportScripts/blob/main/SQLServer/LICENSE.txt).
