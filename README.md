# No-open-sg
OVERVIEW

In this lab, I wrote a policy that blocks open security group rules. Like allowing the entire internet (0.0.0.0/0) to access sensitive ports such as SSH (22) or RDP (3389). These are among the most common and dangerous misconfigurations in cloud environments and are frequently exploited in attacks. I wrote a policy using Rego, tested it with Conftest, and ran everything inside GitHub Codespaces with no local setup required. 

WHAT I LEARNED

Understood why open security group rules are dangerous
Wrote a Rego policy to block them
Used Conftest to test your policy
Ran it all inside GitHub Codespaces

IMPACT

Open security groups are like leaving your front door wide open to the world. Even if you don’t intend to expose critical systems, attackers constantly scan for these entry points. Not fixing this can lead to:

Remote shell access from malicious actors
Ransomware planted directly on cloud instances
Non-compliance with standards like NIST, FedRAMP, or CMMC
Loss of customer trust and public credibility And the worst part? It’s usually an accident. One that policy as code could have blocked before it ever went live.

WHY IT MATTERS

This policy directly addresses critical security and compliance objectives by satisfying the following NIST SP 800-53 controls:

AC-4 – Information Flow Enforcement: This policy prevents unauthorized traffic by explicitly blocking open ingress rules. It enforces controlled access at the infrastructure layer, stopping unrestricted data flow into sensitive systems.

AC-6(9) – Least Privilege: Limitation on Access by Port: By denying public access to ports 22 (SSH) and 3389 (RDP), the policy ensures that only authorized and minimal access is granted, reducing attack surface.

SC-7 – Boundary Protection: The policy enforces clear network boundaries by preventing open exposure to external sources. This is critical for segmenting systems and protecting internal components.

SC-7(3) – Access Points: Deny by Default: Rather than allowing traffic by default, this policy requires explicit safe configuration. It aligns with deny-by-default principles foundational to zero-trust architectures.

SI-4(20) – System Monitoring for Unauthorized Communications: While not a monitoring tool, the policy acts as a preventative measure by blocking high-risk misconfigurations before they occur—supporting broader monitoring and detection goals.
