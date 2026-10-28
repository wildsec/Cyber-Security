Secure Software Development Lifecycle
### Overview  
**Secure SDLC (SSDLC)** integrates security activities into the traditional software development lifecycle. Rather than testing security at the end, security is built into each phase from requirements to deployment.  
  
### Phases & Security Activities  
  
#### 1. Requirements & Planning  
- Define security requirements  
- Threat modeling (STRIDE, PASTA, Attack Trees)  
- Compliance mapping (GDPR, PCI-DSS, etc.)  
- Security acceptance criteria  
#### 2. Design  
- Architecture security review  
- Threat modeling update  
- Secure design patterns selection  
- Data flow analysis
#### 3. Implementation/Coding  
- Secure coding standards (OWASP, CERT, MISRA)  
- Static Application Security Testing (SAST)  
- IDE security plugins  
- Peer code reviews with security focus  
#### 4. Testing  
- Dynamic Application Security Testing (DAST)  
- Interactive Application Security Testing (IAST)  
- Fuzzing  
- Penetration testing  
- Software Composition Analysis (SCA) for dependencies
#### 5. Deployment  
- Secure configuration hardening  
- Secrets management  
- Infrastructure as Code (IaC) scanning  
- Runtime Application Self-Protection (RASP)  
#### 6. Maintenance  
- Vulnerability management  
- Patch management  
- Security monitoring  
- Incident response  
- Secure decommissioning  
  
### Core Principles  
1. **Shift Left**: Security earlier in development (cheaper to fix)  
2. **Automation**: CI/CD pipeline integration  
3. **Defense in Depth**: Multiple security checkpoints  
4. **Continuous Monitoring**: Security doesn't end at deployment  
  
### Cybersecurity Application  
- Reduces cost of vulnerability remediation (100x cheaper pre-deployment)  
- Prevents security debt accumulation  
- Enables DevSecOps culture  
- Compliance with CRA, IEC 62443, and industry requirements  
- Essential for modern software development