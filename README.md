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
## Image Sacn - 'trivy'   
- **Install the tool**      
````
sudo apt-get install rpm   
wget https://github.com/aquasecurity/trivy/releases/download/v0.16.0/trivy_0.16.0_Linux-64bit.deb   
sudo dpkg -i trivy_0.16.0_Linux-64bit.deb
```   
- **Run the scan aginst default polices:**    
```
trivy image --exit-code 0 --severity LOW,MEDIUM $Image:$Tag    
trivy image --exit-code 1 --severity HIGH,CRITICAL $Image:$Tag     
```

## Manifests Sacn - 'kubescape'   
- **Install the tool**      
`curl -s https://raw.githubusercontent.com/kubescape/kubescape/master/install.sh | /bin/bash`   
- **Run the scan aginst default polices:**    
`kubescape scan $HelmChartPath`   

## Manifests Sacn - 'checkov'
- **Install the tool**      
`pip3 install checkov`   
- **Run the scan aginst default polices:**      
```
helm template $HelmChartPath > for-checkov-scan.yaml   
checkov -f for-checkov-scan.yaml --framework kubernetes --check MEDIUM --check HIGH --exit-code 0   
checkov -f for-checkov-scan.yaml --framework kubernetes --check MEDIUM --check HIGH --exit-code 1    
```    

# References
- https://digitalvarys.com/approaches-to-automate-security-testing-in-cicd-pipelines/   
- https://www.g2.com/categories/software-composition-analysis   
- https://www.ibm.com/topics/devsecops   
- https://www.alldaydevops.com/blog/sca-sast-cva-dast-4-common-security-terms-explained?hs_amp=true   
- https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux_atomic_host/7/html/managing_containers/signing_container_images   
