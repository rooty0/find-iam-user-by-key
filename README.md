# find-iam-user-by-key

## Overview

This tool helps to find a user name by provided aws key.


## Description

Key Features of this tool:

* Simple. Just bash scrips
* Use it to search in **multiple accounts** at the same time! You need to provide profiles in the configuration file of this tool, see ``.profiles.example`` configuration file
* Really fast!!! (Because of local cache)

There are some solutions online ([like this one](https://gist.github.com/OnlyInAmerica/9964456
"Find an AWS IAM user corresponding to an AWS Access Key")) which can do similar things,
but they don't fit with the features above.

### populate_iam_users

You need to run this script first. This script builds a local cache for you. Obviously, this script takes some time to execute.

Output example:

    $ ./populate_iam_users
    Building local cache of all IAM users...
    - Profile: default
    - Profile: qubole
    - Profile: machinelearning
    done
    
### find_user_by_key

This script reads local cache and performs searching for a specific user which owns provided key.

Output example:

    $ ./find_user_by_key BENEEP2THOOLAI8OOKOH
    ./profile_cache/default:ACCESSKEYMETADATA	BENEEP2THOOLAI8OOKOH	2014-09-11T23:22:53Z	Active	john.doe

## Requirements

* awscli should be installed ``$ pip install awscli``
* ``~/.aws/config`` should be configured

## Setup

There're 2 options you can follow:

- Create a config file (See information inside the file for more details)


    $ cp .profiles.example .profiles
    $ chmod 600 .profiles

- **Other option** is to define environment variable ``AWS_PROFILES`` instead of using config ``.profiles`` . FYI, don't
confuse environment variables ``AWS_PROFILES`` with ``AWS_PROFILE`` that related to aws cli.

## Development

### Contributing

Feel free to send pull requests with updates.
