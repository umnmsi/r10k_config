# r10k_config

This repository contains the live r10k configuration file in use in our puppet code deployments.  
We have rigged up r10k to deploy its own configuration, so pushing to this repository is the way
to make changes.

It's also useful for reference if you need to see exactly how our code deployment is happening.

Currently, spp is configured to run `r10k deploy environment --puppetfile` in response to github pushes
in the MSI-Puppet organization.
