---
title: Improve the Speed of your Data Upload
layout: article
excerpt: 
category: in-practice
---

{why}

## title

    Is this a remote cloud server, a local machine?

    Can you speak to its upload bandwidth in other applications?

    How many computer cores are available on the machine uploading the files (the Python client will use this number in determining the default number of files to upload in parallel, which affects the overall transfer speed)?

    On a linux machine this number can be obtained with the following command:
    cat /proc/cpuinfo | grep processor | wc -l

    Or on a Mac as follows:
    sysctl -n hw.ncpu
Another useful thing to know would be the number of CPUs on the machine, which can be obtained on Windows by running the following command from the Windows command prompt

echo %NUMBER_OF_PROCESSORS%

This number influences the default number of concurrent files that the Python client will choose to upload with. The default value (which is the above number + 4) can be overridden through the use of the Synapse configuration  file by setting the max_threads value. Generally however the default value will be appropriate for the environment and we should only try experimenting with it if the upload performance seems inconsistent with the numbers above.