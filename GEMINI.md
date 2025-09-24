# GEMINI.md

## Directory Overview

This directory contains the necessary files to host a Mail Transport Agent Strict Transport Security (MTA-STS) policy on GitHub Pages. The purpose of this project is to provide a simple and effective way to publish an MTA-STS policy, which helps to secure email delivery by enforcing TLS encryption.

This is not a code project but rather a configuration-based setup for serving a static policy file.

## Key Files

* `.well-known/mta-sts.txt`: This is the core MTA-STS policy file. It defines the MTA-STS policy mode, mail servers, and the maximum age of the policy.
* `CNAME`: This file specifies the custom domain (`mta-sts.lewsion.com`) that is used for the GitHub Pages site.
* `index.html`: This file acts as a simple redirect to the `mta-sts.txt` policy file, ensuring that visitors to the root of the site are directed to the policy.
* `_config.yml`: This is a Jekyll configuration file that is used by GitHub Pages. In this project, it is configured to ensure that the `.well-known` directory is included when the site is built.
* `README.md`: This file provides detailed instructions on how to use this repository as a template to host your own MTA-STS policy.

## Usage

The contents of this directory are intended to be used as a template for publishing an MTA-STS policy. To use this project, you would typically:

1. Fork this repository or use it as a template.
2. Modify the `.well-known/mta-sts.txt` file to reflect your own mail server configuration and desired policy.
3. Update the `CNAME` file with your own custom domain.
4. Configure your domain's DNS settings to point to the GitHub Pages site.
5. Create the necessary `_mta-sts` DNS TXT records to enable the policy.

The `README.md` file contains a comprehensive guide on how to perform these steps.
