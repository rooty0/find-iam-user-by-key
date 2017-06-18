# find-iam-user-by-key

##Overview

This tool helps to find a user name by provided aws key.


##Description

Key Features of this tool:

* Simple. Just bash scrips
* Can be used for search in multiple accounts at same time. You just need to provide profiles in the configuration file of this tool
* Really fast!!! Because of cache strategy

There are some solutions online ([like this one](https://gist.github.com/OnlyInAmerica/9964456
"Find an AWS IAM user corresponding to an AWS Access Key")) which can do similar things,
but they doesn't fit with features above.

###populate_iam_users

You should run this script first. This script builds a local database for you. So this script is most slow.

Output example:

    $ ./populate_iam_users
    Building local database of all IAM users...
    - Profile: default
    - Profile: qubole
    - Profile: machinelearning
    done
    
###find_user_by_key

This script reads local database and performs searching for a specific user which owns provided key.

Output example:

    $ ./find_user_by_key BENEEP2THOOLAI8OOKOH
    ./database/default:ACCESSKEYMETADATA	BENEEP2THOOLAI8OOKOH	2014-09-11T23:22:53Z	Active	stanislav.rudenko

##Requirements

* awscli should be installed


    
    $ pip install awscli
    
* ``~/.aws/config`` should be configured

##Setup

You should create config file first

    $ cp .profiles.example .profiles
    $ chmod 600 .profiles
    
See information inside for more details

Or run it with AWS_PROFILES configured

##Development

###Contributing

Feel free to send pull requests with updates.
