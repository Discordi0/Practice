
# About

`Expressway` is an easy-difficulty Linux machine that demonstrates enumeration and exploits the IKE service, a component of the `IPsec` framework. Upon leaking the Pre-Shared key of the service and cracking it, the retrieved clear-text credentials are used to access the target via SSH. For privilege escalation, [CVE-2025-32462](https://nvd.nist.gov/vuln/detail/CVE-2025-32462) is exploited to get a privileged shell as the `root` user.

---

# Questions

## Q1: 