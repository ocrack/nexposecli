# Nexposecli

This is the experimental gem package for the Ruby Nexpose command-line utility using the Nexpose gem.

This gem is heavily used for internal automation of Rapid7's Nexpose Enterprise Console activities and configuration.

Install it yourself as:

    $ gem install nexposecli

## Usage

    nexposecli --help

or an example of running a query to list all active scans

    nexposecli --config ./lab.yaml --list --SCAN

how to list all reports defined

    nexposecli --config ./lab.yaml --list --REPORT

how to request the console's version details

    nexposecli --config ./lab.yaml --run --COMMAND "ver"

how to run an adhoc scan for a single ip or network cidr-noted range ( --id <site id> )

    nexposecli --config ./lab.yaml --create --SCAN --id 1 --range 192.168.42.103/32

how to add a new custom role for configuration within the console ui, based on a copy of existing role

    nexposecli --config ./lab.yaml --create --ROLE -n security-manager --description "New Role Name" --newname new-short-name

how to add a new user, with default password of "nxpassword" until moved to yaml config is supported

    nexposecli  --config ./lab.yaml --create --USER --name <username> --fullname "Full Name"

how to export packaged scan data in a single zip file

    nexposecli --config ./lab.yaml --SCAN --update --scanpath ./ --action export --id <scan id>

where ./lab.yaml consists of the following:

    config:
       server: 10.10.10.10
       user: nxuser
       password: password

NOTE: Be sure to use your Nexpose Console's ip address and credentials

TODO: Write more detailed usage instructions here

Known Issues:
* Currently expects a ./logs directory in working directory
* A number of the target objects may not return anything to STDOUT without a -v

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/frozenr7/nexposecli.

