---
title: Uploading data
has_children: false
parent: Contributing
nav_order: 2
---

# Uploading data with hca-util
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Prerequisites

`hca-util` is a command line based tool that assists with data upload to HCA upload areas. To be able to use `hca-util` you will need:

1. Python3 installed on your computer
1. Basic knowledge of how to navigate the command line and run commands in a terminal, e.g. `cd`, `ls`, `pwd`
1. Credential information emailed to you by your wrangler. If you don't have the following information, please email wrangler-team@data.humancellatlas.org to obtain these credentials.
    1. A unique identifier that identifies your personal upload area. This should be kept secure and not shared with others outside your research group. e.g. `72ca5e3f-dacf-427a-a8a4-ecf15789006d`
    1. Your AWS access key e.g. `AKIAI44QH8DHBEXAMPLE`
    1. Your AWS secret key e.g. `je7MtGbClwBF/2Zp9Utk/h3yCo8nvbEXAMPLEKEY`. 

    Keep these credentials safe and do not pass them to users who should not have access to upload files or see the files you have uploaded. In particular, do not record these credentials in any public place such as a public Github repository.

If you are missing any of the prerequisites above, please contact [wrangler-team@data.humancellatlas.org](mailto:wrangler-team@data.humancellatlas.org) for guidance. 

## Installation

Check that you have Python 3 installed by opening a terminal and running the following command:

```
which python3
```

It should return the location of your Python 3 installation e.g.

```
/path/to/bin/python3
```

If nothing is returned it means you do not have Python 3 installed. 

There are many tutorials online for installing python so please follow one that makes sense to you and suits your operating system or contact your system administrator for help. One example can be found here: https://realpython.com/installing-python/

Once you have installed Python 3, in your terminal run the following command to install `hca-util`

```
pip3 install hca-util
```

Once installed, you can see the available commands by typing the following command in your terminal. 

```
hca-util -h
```

If this succeeds continue to the [configuration](#configuration) section.

Depending on your Python installation you may need to use `sudo` to install the tool in your system directory. If the above command gives a `Permission denied` error, try using the following command:

```
sudo pip3 install hca-util
```

You will then be prompted for your system password. If this succeeds continue to the [configuration](#configuration) section below.

### Installing `hca-util` in a virtual environment

If the above process fails we recommend creating a  [virtual environment](https://docs.python.org/3/tutorial/venv.html) to install the `hca-util` tool. 

To create an environment called `hca_util_env`, use the following commands:

```
cd /location/of/virtual/env
python3 -m venv hca_util_env
source hca_util_env/bin/activate
```

After running the `source` command you should see the name of the environment in brackets at the beginning of the terminal line i.e `(hca_util_env)` and you should be able to install and run the `hca-util` tool within this environment as follows:

```
pip3 install hca-util
```

You can now continue with configuring the tool.

## Configuration

The first time you use the tool it will need to be configured. The configuration creates an AWS profile called `hca-util` that will give you the appropriate permissions to upload to your upload area. 

To configure use the following command with the `AWS access key` and `AWS secret key` that you should have received via email.

```
hca-util config <YOUR ACCESS KEY> <YOUR SECRET KEY>
```

This would look something like:

```
$ hca-util config AKIAI44QH8DHBEXAMPLE je7MtGbClwBF/2Zp9Utk/h3yCo8nvbEXAMPLEKEY
Credentials saved.
Valid credentials
```

## Selecting your upload area

Once configured, you need to `select` your upload area using the identifier you have been provided via email.

```
hca-util select <YOUR IDENTIFIER>
```

For example:

```
$ hca-util select 72ca5e3f-dacf-427a-a8a4-ecf15789006d
Selected 72ca5e3f-dacf-427a-a8a4-ecf15789006d
```
You are now ready to upload files to your upload area!

## Uploading files

Once your upload area is selected you can use the `upload` command upload the files related to your project into the upload area. 

To upload a single file or space-separated list of files use the `-f` alongside the `upload` command. If files have spaces they must be escaped or enclosed in quotes. This would look something like:

```
$ hca-util upload -f /path/to/file/sample1_R1.fastq.gz
Uploading...
/path/to/file/sample1_R1.fastq.gz 2845965046 / 2845965046.0  (100.00%)

$ hca-util upload -f /path/to/file/sample1_R1.fastq.gz "/path/to/file/dissociation protocol.pdf" /path/to/file/enrichment\ protocol.pdf
Uploading...
/path/to/file/sample1_R1.fastq.gz 2845965046 / 2845965046.0  (100.00%)
/path/to/file/dissociation protocol.pdf 354 / 354.0  (100.00%)
/path/to/file/enrichment protocol.pdf 354 / 354.0  (100.00%)
```

To upload all files in your current working directory, you specify the `-a` flag as follows:

```
$ hca-util upload -a
Uploading...
sample1_R1.fastq.gz  2845965046 / 2845965046.0  (100.00%)
sample1_R2.fastq.gz  2845965046 / 2845965046.0  (100.00%)
sample2_R1.fastq.gz  2845965046 / 2845965046.0  (100.00%)
sample2_R2.fastq.gz  2845965046 / 2845965046.0  (100.00%)
dissociation protocol.pdf 354 / 354.0  (100.00%)
enrichment protocol.pdf 354 / 354.0  (100.00%)
```

To check if all the files you expected to upload are present in your upload area use the `list` command

This should look something like: 

```
hca-util list
72ca5e3f-dacf-427a-a8a4-ecf15789006d/sample1_R1.fastq.gz
72ca5e3f-dacf-427a-a8a4-ecf15789006d/sample1_R2.fastq.gz
72ca5e3f-dacf-427a-a8a4-ecf15789006d/sample2_R1.fastq.gz
72ca5e3f-dacf-427a-a8a4-ecf15789006d/sample2_R2.fastq.gz
72ca5e3f-dacf-427a-a8a4-ecf15789006d/dissociation protocol.pdf
72ca5e3f-dacf-427a-a8a4-ecf15789006d/enrichment protocol.pdf
```

By default the upload command won't upload files that have the same name as files already present in the upload area. If you do need to overwrite an uploaded file with a file of the same name, you will need to use the `-o`* flag. For example:

```
$ hca-util upload -o -f /path/to/file/sample1_R1.fastq.gz
Uploading...
/path/to/file/sample1_R1.fastq.gz 2845965046 / 2845965046.0  (100.00%)
```

_**Notes:**_ 

_* The `-o` flag needs to come before the `-f` OR after all the filenames._

_* If you change your mind and wish to cancel the upload hit `ctrl` + `c` to cancel the upload._

_* If there are sub-directories within a folder these will be ignored so please ensure all files to be uploaded are within the working directory._

## Deleting files

To delete files from your upload area use the `delete` command.

To delete a single file or list of specified files, use the `delete` command with the `-f` flag.

```
hca-util delete -f <FILENAME>
```

For example:

```
$ hca-util delete -f sample1_R1.fastq.gz
Deleting...
Deleting 72ca5e3f-dacf-427a-a8a4-ecf15789006d/sample1_R1.fastq.gz  Done.
```

To delete all files in the selected area, use the `-a` flag with the `delete` command. For example:

```
$ hca-util delete -a
Deleting...
72ca5e3f-dacf-427a-a8a4-ecf15789006d/sample1_R2.fastq.gz
72ca5e3f-dacf-427a-a8a4-ecf15789006d/sample2_R1.fastq.gz
72ca5e3f-dacf-427a-a8a4-ecf15789006d/sample2_R2.fastq.gz
72ca5e3f-dacf-427a-a8a4-ecf15789006d/dissociation protocol.pdf
72ca5e3f-dacf-427a-a8a4-ecf15789006d/enrichment protocol.pdf
$ hca-util list
72ca5e3f-dacf-427a-a8a4-ecf15789006d/
No item
```

If you cannot delete files from your upload area but would like to, please email [wrangler-team@data.humancellatlas.org](mailto:wrangler-team@data.humancellatlas.org).

## Help!

If you have any issues with uploading files or using the hca-util tool, please email [wrangler-team@data.humancellatlas.org](mailto:wrangler-team@data.humancellatlas.org).

Source code for tool can be found on github here: https://github.com/ebi-ait/hca-util

