# r10k_config

This repository contains the live r10k configuration file in use in our puppet code deployments.  
We have rigged up r10k to deploy its own configuration, so pushing to this repository is the way
to make changes. It's also useful for reference if you need to see exactly how our code deployment is happening.

Currently, spp is configured to run `r10k deploy environment --puppetfile` in response to github pushes
in the MSI-Puppet organization.

## Contributing
The master branch, which controls, cannot be pushed to directly. If you would like to change the r10k
configuration, do so in a new branch and submit a pull request. Travis-CI will run r10k with your changes
to verify that they are workable, and a member of @MSI-Puppet/puppet-librarians will review and merge it.
