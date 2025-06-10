# Example: `mta-sts.txt`

This is an example of an **MTA-STS policy file** with all possible values.  
Save this file as `.well-known/mta-sts.txt` and serve it over HTTPS at:  
`https://mta-sts.example/.well-known/mta-sts.txt`

---

## Policy Fields

```plaintext
version: STSv1
# The version of the MTA-STS policy. Must be "STSv1".

mode: enforce
# The policy mode. Possible values:
#   enforce   - SMTP servers must enforce the policy.
#   testing   - Policy is in testing; violations are reported but not enforced.
#   none      - No policy is applied.

mx: mail.example.com
mx: *.mail.example.net
# The list of MX patterns (hostnames) that are valid for your domain.
# Wildcards (*) are allowed only as the left-most label.

max_age: 86400
# The time (in seconds) that the policy is valid for.
# Recommended minimum is 86400 (1 day). Maximum is 31557600 (1 year).
```

---

## Example Full Policy

```plaintext
version: STSv1
mode: enforce
mx: mail.example.com
mx: *.mail.example.net
max_age: 86400
```

---

For more details, see:  
[RFC 8461 - MTA-STS Specification](https://datatracker.ietf.org/doc/html/rfc8461)