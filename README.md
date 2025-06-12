# AI Code Review Prompts

A collection of comprehensive AI prompts for automated code reviews across different programming languages and frameworks.

## 🚀 Quick Start

### For GitHub Copilot Users
1. Copy the prompt from the appropriate file
2. Open GitHub Copilot Chat in VS Code
3. Type `@workspace` followed by the prompt
4. Add your code for review

### For API Users (ChatGPT, Claude, etc.)
1. Copy the prompt from the appropriate file
2. Paste it into your preferred AI tool
3. Add your code after the prompt
4. Get comprehensive feedback

## 📁 Available Prompts

### Java & Spring Boot
- **`java/spring-boot-comprehensive.md`** - Enterprise-grade comprehensive review with 37+ detailed checks
- **`java/spring-boot-security-comprehensive.md`** - Security-focused analysis with SAST, SCA, DAST preparation, and OWASP ASVS compliance

#### What Gets Reviewed:
**🔍 Code Quality & Standards** (Comprehensive Review)
- Java 21 modern features (records, pattern matching, sealed classes)
- SOLID principles detailed analysis
- Enterprise Java patterns and best practices
- Code readability, maintainability, and documentation

**🏗️ Spring Boot 3+ Framework Analysis** (Comprehensive Review)
- Configuration and dependency injection patterns
- REST API design and HTTP standards compliance
- Data access layer optimization (JPA/Hibernate)
- Security implementation (Spring Security 6+)
- Testing strategies and coverage assessment

**🔒 Security & Vulnerability Assessment** (Both Reviews)
- Dependency vulnerability scanning (CVE detection)
- OWASP Top 10 compliance validation
- Authentication and authorization review
- Input validation and data protection
- Security headers and configuration analysis

**🛡️ Advanced Security Analysis** (Security-Focused Review)
- **SAST Analysis**: SQL injection, XSS, authentication bypass, cryptographic failures
- **SCA Assessment**: Dependency vulnerabilities, license compliance, supply chain security
- **DAST Preparation**: Endpoint documentation, testing recommendations, attack scenarios
- **OWASP ASVS Compliance**: Level 1-3 verification standards with gap analysis
- **Penetration Testing Readiness**: Scope definition, test scenarios, security roadmap

**⚡ Performance & Architecture** (Comprehensive Review)
- Database query optimization and N+1 problem detection
- Caching strategy evaluation
- Memory management and resource cleanup
- Microservices patterns and scalability assessment
- Circuit breaker and resilience patterns

**📊 Detailed Reporting** (Both Reviews)
- File-by-file analysis with line numbers
- Severity classification (Critical/High/Medium/Low)
- Executive dashboard with quality scores
- Implementation steps and prevention strategies
- Technical debt assessment and prioritization

## 🛠️ Usage Example

```bash
# With GitHub Copilot in VS Code
@workspace [paste the comprehensive prompt] 

# Then add your Java code for review
```

## 📝 What You Get

Each prompt provides:
- ✅ Security vulnerability analysis
- ✅ Best practices compliance
- ✅ Performance optimization suggestions  
- ✅ SOLID principles assessment
- ✅ Detailed improvement recommendations

## 🤝 Contributing

Feel free to:
- Add new language prompts
- Improve existing prompts
- Share your feedback

## ⚠️ Disclaimer

These prompts generate AI-assisted code reviews that should supplement, not replace, human judgment. Always validate AI recommendations before implementing changes in production environments. Users are responsible for reviewing and testing all suggested modifications.

## 📄 License

MIT License - feel free to use and modify.