# Pod security policy (PSP)

Removed in v1.25 and replaced with newer:
* Pod Security Admission (PSA)
* Pod Security Standards (PSS)  

Those are stable in v1.25

## Old PSP
It's an admission controller that validates pod against preconfigured rules, and can deny if e.g. priviliged is set to True:
![](../images/19_psp_1.png)

Those preconfigured rules are defined in a manifest of kind PodSecurityPolicy:
![](../images/19_psp_2.png)
it's validating & mutating (adds default values and checks)

PSP is by default not enabled in admission controllers.  
PSP posed problems because person/service who was creating pods, must have also have access to PodSecurityPolicy.
Solution could be as follows:

![](../images/19_psp_3.png)

So PSP was very cumbersome and hard to rollout.