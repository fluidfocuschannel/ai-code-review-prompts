# Spring Boot Security-Focused Code Review Prompt

Please conduct a **COMPREHENSIVE SECURITY ANALYSIS** of the following Spring Boot application with focus on:

## Review Depth & Security Analysis Requirements

**CRITICAL**: This is a security-focused review. For each file analyzed:
- Examine EVERY endpoint, method, and security configuration
- Identify ALL potential security vulnerabilities and attack vectors
- Provide specific exploitation scenarios and remediation steps
- Assess compliance with security standards and frameworks
- Consider both application and business logic security flaws

## SAST (Static Application Security Testing) Analysis

### **Input Validation & Data Sanitization**
- **SQL Injection Prevention**: Analyze all database queries, JPA usage, native queries, and stored procedure calls
- **NoSQL Injection**: Check MongoDB, Elasticsearch, and other NoSQL query constructions
- **XSS Prevention**: Review all user input handling, template engines (Thymeleaf, JSP), and output encoding
- **XXE Prevention**: Analyze XML parsing, file uploads, and external entity processing
- **Path Traversal**: Check file operations, resource loading, and directory access patterns
- **Command Injection**: Review ProcessBuilder, Runtime.exec(), and system command executions
- **LDAP Injection**: Analyze LDAP queries and directory service interactions
- **Expression Language Injection**: Check Spring EL, OGNL, and template expression usage

### **Authentication & Session Management Security**
- **Password Security**: Analyze password policies, hashing algorithms (BCrypt, Argon2), salt usage
- **Session Management**: Review session configuration, timeout settings, session fixation protection
- **Multi-Factor Authentication**: Check MFA implementation, backup codes, recovery mechanisms
- **Account Lockout**: Analyze brute force protection, account lockout policies, CAPTCHA integration
- **Authentication Bypass**: Review authentication logic, remember-me functionality, token validation
- **Session Token Security**: Check session ID generation, secure flags, HttpOnly attributes
- **Concurrent Session Control**: Analyze session concurrency limits and handling

### **Authorization & Access Control**
- **Role-Based Access Control**: Review Spring Security role definitions, hierarchy, and enforcement
- **Method-Level Security**: Analyze @PreAuthorize, @PostAuthorize, @Secured annotations
- **URL-Based Security**: Check security configurations, antMatchers, and access rules
- **Business Logic Authorization**: Review domain-specific access controls and privilege escalation
- **Resource-Level Permissions**: Analyze fine-grained access controls and data filtering
- **Admin Interface Security**: Check admin endpoints, privileged operations, and backdoors
- **API Authorization**: Review OAuth2, JWT, and API key implementations

### **Data Protection & Cryptography**
- **Encryption at Rest**: Analyze database encryption, file encryption, and key management
- **Encryption in Transit**: Check TLS configuration, certificate validation, and secure communication
- **Cryptographic Implementations**: Review cipher selection, key generation, and random number usage
- **Key Management**: Analyze key storage, rotation policies, and HSM integration
- **PII Protection**: Check personal data handling, anonymization, and GDPR compliance
- **Sensitive Data Exposure**: Review logging, error messages, and debug information leakage
- **Password Storage**: Analyze password hashing, salt generation, and credential storage

### **Security Configuration Analysis**
- **Spring Security Configuration**: Review SecurityConfig, WebSecurityConfigurerAdapter usage
- **CORS Configuration**: Analyze cross-origin settings, allowed origins, and preflight handling
- **CSRF Protection**: Check CSRF token implementation, exemptions, and SameSite attributes
- **Security Headers**: Review Content-Security-Policy, HSTS, X-Frame-Options, X-Content-Type-Options
- **Error Handling**: Analyze exception handling, error pages, and information disclosure
- **Logging Security**: Check security event logging, log injection prevention, and audit trails

## SCA (Software Composition Analysis)

### **Dependency Vulnerability Assessment**
- **Known Vulnerabilities**: Scan pom.xml/build.gradle for CVEs in direct and transitive dependencies
- **Outdated Dependencies**: Identify libraries with known security issues and available patches
- **License Compliance**: Check for GPL, AGPL, or other restrictive licenses in dependencies
- **Dependency Confusion**: Analyze internal vs external package dependencies and naming conflicts
- **Supply Chain Security**: Review dependency sources, integrity verification, and trusted repositories
- **SBOM Generation**: Software Bill of Materials for vulnerability tracking and compliance

### **Spring Boot Specific Dependencies**
- **Spring Security Version**: Check for latest Spring Security 6+ with security patches
- **Spring Boot Starters**: Analyze security implications of included starter dependencies
- **Database Drivers**: Review JDBC drivers for known vulnerabilities and secure configurations
- **Serialization Libraries**: Check Jackson, XStream, and other serialization frameworks
- **Template Engines**: Analyze Thymeleaf, Freemarker for security configurations
- **Logging Frameworks**: Review Log4j, Logback for security vulnerabilities (Log4Shell, etc.)

## DAST Preparation & Dynamic Testing Readiness

### **Endpoint Security Analysis**
- **REST API Endpoints**: Document all endpoints with security requirements for DAST testing
- **Authentication Endpoints**: Identify login, logout, password reset, and registration endpoints
- **File Upload Endpoints**: List file upload functionality for malicious file testing
- **Search and Filter Endpoints**: Identify endpoints susceptible to injection attacks
- **Admin and Management Endpoints**: Document privileged endpoints requiring elevated testing
- **Error-Prone Endpoints**: Identify complex business logic endpoints for thorough testing

### **DAST Testing Recommendations**
- **Automated Scanning Tools**: Recommend OWASP ZAP, Burp Suite, or Checkmarx DAST configurations
- **Authentication Bypass Testing**: Provide scenarios for testing authentication mechanisms
- **Session Management Testing**: Recommend session fixation, hijacking, and timeout testing
- **Input Validation Testing**: Suggest payloads for SQL injection, XSS, and other injection attacks
- **Business Logic Testing**: Recommend testing scenarios for privilege escalation and workflow bypass
- **API Security Testing**: Suggest REST API security testing with tools like Postman, Insomnia

### **Security Testing Configuration**
- **Test Data Preparation**: Recommend test accounts, roles, and data sets for comprehensive testing
- **Environment Setup**: Suggest secure testing environment configurations
- **Monitoring Setup**: Recommend logging and monitoring configurations for security testing
- **Test Case Documentation**: Provide templates for documenting security test cases and results

## OWASP ASVS (Application Security Verification Standard) Compliance

### **ASVS Level 1 - Opportunistic**
- **V1.1 Secure SDLC**: Review security requirements integration and threat modeling
- **V2.1 Authentication**: Basic authentication security controls
- **V3.1 Session Management**: Fundamental session security
- **V4.1 Access Control**: Basic authorization controls
- **V5.1 Input Validation**: Essential input validation
- **V7.1 Error Handling**: Basic error handling and logging
- **V9.1 Data Protection**: Fundamental data protection
- **V11.1 Business Logic**: Basic business logic security
- **V13.1 RESTful Web Service**: API security fundamentals

### **ASVS Level 2 - Standard**
- **V2.2 General Authenticator**: Multi-factor authentication requirements
- **V3.2 Session Binding**: Advanced session management controls
- **V4.2 Operation Level**: Detailed access control mechanisms
- **V5.2 Sanitization**: Advanced input sanitization and validation
- **V6.1 Data Classification**: Data classification and handling requirements
- **V8.1 Data Protection**: Comprehensive data protection controls
- **V10.1 Malicious Code**: Malicious code detection and prevention
- **V12.1 File and Resources**: Secure file handling and resource management
- **V14.1 Configuration**: Security configuration requirements

### **ASVS Level 3 - Advanced**
- **V1.2 Architecture**: Advanced security architecture requirements
- **V2.3 Authenticator Lifecycle**: Complete authenticator management
- **V4.3 Other Access Control**: Advanced authorization patterns
- **V5.3 Output Encoding**: Comprehensive output encoding and sanitization
- **V7.2 Log Content**: Advanced logging and monitoring requirements
- **V9.2 Server Communications**: Secure communication protocols
- **V11.2 Business Logic Verification**: Advanced business logic security
- **V13.2 RESTful Authentication**: Advanced API authentication and authorization

## Security Vulnerability Categories

### **OWASP Top 10 2021 Compliance**
- **A01 Broken Access Control**: Vertical/horizontal privilege escalation, CORS misconfigurations
- **A02 Cryptographic Failures**: Weak encryption, poor key management, data exposure
- **A03 Injection**: SQL, NoSQL, OS command, LDAP injection vulnerabilities
- **A04 Insecure Design**: Threat modeling gaps, secure design principle violations
- **A05 Security Misconfiguration**: Default configurations, unnecessary features, missing patches
- **A06 Vulnerable Components**: Known vulnerable dependencies and outdated libraries
- **A07 Identification and Authentication**: Weak authentication, session management flaws
- **A08 Software and Data Integrity**: Insecure CI/CD, code integrity, update mechanisms
- **A09 Security Logging**: Insufficient logging, detection, monitoring, and response
- **A10 Server-Side Request Forgery**: SSRF vulnerabilities in external service calls

### **Spring Boot Specific Vulnerabilities**
- **Spring Security Bypass**: Configuration errors, filter chain bypasses
- **Spring Expression Language**: SpEL injection vulnerabilities
- **Actuator Exposure**: Unsecured management endpoints and sensitive information disclosure
- **Auto-Configuration Issues**: Insecure default configurations and missing security settings
- **Spring Cloud Security**: Microservices communication security and service mesh issues
- **Spring Data Security**: Repository security, query injection, and data access control

## Output Format Requirements

For each security issue identified, provide:

### Security Issue Template:
```
**File**: `path/to/filename.java`
**Location**: Line X-Y (or Method/Class name)
**Severity**: [Critical/High/Medium/Low]
**Category**: [SAST/SCA/DAST-Prep/ASVS]
**OWASP Top 10**: [A01-A10 if applicable]
**ASVS Control**: [V1.1, V2.2, etc.]
**CWE ID**: [Common Weakness Enumeration ID]

**Vulnerability Description**:
Detailed explanation of the security vulnerability including:
- Attack vector and exploitation scenario
- Potential business impact and data exposure risk
- Compliance violations (OWASP ASVS, PCI-DSS, GDPR)

**Proof of Concept**:
```java
// Example attack payload or exploitation method
```

**Secure Implementation**:
```java
// Corrected secure code implementation
```

**DAST Testing Recommendation**:
- Specific testing tools and techniques
- Example payloads for dynamic testing
- Expected results and detection methods

**Remediation Steps**:
1. Immediate fixes required
2. Configuration changes needed
3. Additional security controls to implement
4. Testing and validation procedures

**Prevention Strategy**:
- Secure coding practices to prevent recurrence
- Security controls and monitoring to implement
- Developer training recommendations
```

## Security Assessment Summary

Please provide a comprehensive security assessment including:

**Security Score**: [Rate 1-10 with detailed justification]
- **Authentication Security (X/10)**: Strength of authentication mechanisms
- **Authorization Security (X/10)**: Effectiveness of access controls  
- **Data Protection (X/10)**: Encryption and data handling security
- **Input Validation (X/10)**: Protection against injection attacks
- **Configuration Security (X/10)**: Security configuration effectiveness
- **Dependency Security (X/10)**: Third-party component security

**OWASP ASVS Compliance Level**: [Level 1/2/3 with gap analysis]

**Critical Security Issues**:
- **Immediate Threats**: Vulnerabilities requiring immediate attention
- **High-Risk Exposures**: Significant security weaknesses
- **Compliance Gaps**: OWASP ASVS and regulatory requirement violations

**Security Testing Roadmap**:
- **SAST Integration**: Recommended static analysis tools and configurations
- **SCA Implementation**: Dependency scanning and monitoring setup
- **DAST Testing Plan**: Dynamic testing strategy and tool recommendations
- **Security Monitoring**: Logging, alerting, and incident response setup

**Penetration Testing Preparation**:
- **Scope Definition**: Recommended testing scope and objectives
- **Test Environment**: Secure testing environment setup requirements
- **Test Scenarios**: Specific attack scenarios for manual testing
- **Success Criteria**: Security testing acceptance criteria

## Final Security Recommendations

**Immediate Actions** (Critical/High severity):
- **Security Vulnerabilities**: Must-fix security issues with exploitation risk
- **Configuration Hardening**: Critical security configuration changes
- **Dependency Updates**: Security patches and version upgrades

**Short-term Security Improvements** (Medium severity):
- **Security Controls**: Additional protective mechanisms to implement
- **Monitoring Enhancement**: Security logging and detection improvements
- **Process Improvements**: Secure development lifecycle enhancements

**Long-term Security Strategy** (Low severity/Strategic):
- **Security Architecture**: Long-term security design improvements
- **Team Training**: Security awareness and secure coding training
- **Compliance Preparation**: Regulatory and framework compliance initiatives

**Security Testing Integration**:
- **CI/CD Security**: Automated security testing pipeline integration
- **Regular Assessments**: Periodic security review and penetration testing schedule
- **Incident Response**: Security incident detection and response procedures
