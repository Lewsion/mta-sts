# MTA-STS Policy Template - Project Context

## Project Overview

This is a template repository for hosting MTA-STS (Mail Transfer Agent Strict Transport Security) policy files on GitHub Pages. The project allows users to create and host their MTA-STS policy file (`.well-known/mta-sts.txt`) to secure email delivery by enforcing SMTP-over-TLS connections.

MTA-STS is a security standard that enables domain owners to declare their email server's support for encrypted SMTP connections. When properly configured, it mitigates man-in-the-middle attacks by instructing sending email servers to only connect via encrypted channels.

## Repository Structure

- `.well-known/` - Contains the MTA-STS policy file served at the well-known location
  - `mta-sts.txt` - The actual MTA-STS policy file that defines how email should be delivered
- `index.html` - Redirects visitors to the MTA-STS policy file
- `_config.yml` - Jekyll configuration to include the `.well-known` directory in builds
- `CNAME` - Defines the custom domain for GitHub Pages
- Various configuration and documentation files for GitHub Pages hosting

## Key Files and Configuration

### MTA-STS Policy File (`.well-known/mta-sts.txt`)

The current policy file contains:

```txt
version: STSv1
mode: enforce
mx: mx1.forwardemail.net
mx: mx2.forwardemail.net
max_age: 604800
```

This policy enforces encrypted connections to the specified MX servers for one week (604800 seconds).

### Domain Configuration

- The `CNAME` file points to `mta-sts.lewsion.com`, indicating the domain for which this MTA-STS policy is configured.
- GitHub Pages serves this repository at that domain via DNS CNAME record.

### Jekyll Configuration

- `_config.yml` includes the `.well-known` directory in the GitHub Pages build, which is necessary for the MTA-STS policy file to be served at the correct path.

## Setup and Usage Instructions

1. Fork or create a repository from this template
2. Modify `.well-known/mta-sts.txt` with your own MX server details
3. Set up a CNAME DNS record pointing `mta-sts.yourdomain.com` to `yourusername.github.io`
4. Configure GitHub Pages with your custom domain
5. Add a TXT DNS record `_mta-sts.yourdomain.com` with your policy ID to enable MTA-STS for your domain
6. Optionally configure TLS reporting with a `_smtp._tls.yourdomain.com` TXT record

## Development Conventions

- This is a static site that gets served via GitHub Pages
- The `.well-known/mta-sts.txt` file should follow RFC 8461 specification
- Policy IDs in DNS TXT records need to be updated when the MTA-STS policy file changes
- The repository uses Jekyll for GitHub Pages hosting

## Security Considerations

- The MTA-STS policy enforces TLS encryption for email delivery
- Proper domain validation is required to prevent unauthorized modification of MTA-STS policies
- The `max_age` directive controls how long the policy remains in effect before requiring re-verification

## Testing and Validation

- Visit `https://mta-sts.yourdomain.com` to verify the policy file is accessible
- Use tools like MXToolBox MTA-STS Lookup or Hardenize to validate your implementation
- Monitor TLS reports if you implement the optional TLS reporting configuration
