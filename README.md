# What is DevSecOps: 
DevSecOps—short for development, security, and operations—automates the integration of security at every phase of the software development lifecycle, from initial design through integration, testing, deployment, and software delivery.

# DevSecOps Common Practices
- **Software Composition Analysis (SCA):** To analyze, manage and scan all open-source components to check for policy and license compliance, security risks, and version updates. 
- **Static Application Security Testing (SAST):** To analyze the codebase and design the rulesets that is to indicate the security vulnerabilities especially in nonrunning state of the application.
- **Container Image Scan:** To identify the vulnerable version of this component in the images being deployed as well as to monitor container hosts for vulnerabilities and suspicious activities.
- **Container Image Tag Sign:** To provides a means of validating where a container image came from, checking that the image has not been tampered with.
- **Dynamic Application Security Testing (DAST):** To analyze the application when it runs and tries to hack from outside like a hacker. 

# Automated implementation of the DevSecOps Practices via CI/CD Pipelines
![alt text](https://github.com/saloyiana/DevSecOps-CI-CD-Pipelines/blob/main/devsecops-cicd-flow.png)   

# Tools Implementation Examples
## Manifests Sacn - 'kubescape'
Install the tool
'curl -s https://raw.githubusercontent.com/kubescape/kubescape/master/install.sh | /bin/bash'
Run the scan aginst default polices:
'kubescape scan </path/to/directory>'
## Manifests Sacn - 'checkov'
Install the tool
'pip3 install checkov'
Run the scan aginst default polices:
'bash -c 'find -iname chart.yaml' | xargs -n1 -I% bash -c " dirname %" | xargs -n1 -I% bash -c "helm template % > %.yaml && checkov -f %.yaml --framework kubernetes || true" --'
# References
- https://digitalvarys.com/approaches-to-automate-security-testing-in-cicd-pipelines/   
- https://www.g2.com/categories/software-composition-analysis   
- https://www.ibm.com/topics/devsecops   
- https://www.alldaydevops.com/blog/sca-sast-cva-dast-4-common-security-terms-explained?hs_amp=true   
- https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux_atomic_host/7/html/managing_containers/signing_container_images   
