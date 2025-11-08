# /scp-security-audit

Perform comprehensive security analysis identifying vulnerabilities, security risks, and compliance issues based on OWASP and industry standards.

## Workflow

### Phase 1: Audit Scoping (Before Execution)

1. **Define Audit Scope**
   - Ask what should be audited (specific feature, entire app, API endpoints, etc.)
   - Identify security concerns or recent incidents
   - Determine audit depth (quick scan vs comprehensive audit)
   - Confirm if looking for specific vulnerability types

2. **Understand Context**
   - Ask about the application type (web, API, mobile backend, etc.)
   - Identify sensitive data handled (PII, payment info, health data, etc.)
   - Determine compliance requirements (GDPR, HIPAA, PCI-DSS, SOC2, etc.)
   - Confirm deployment environment (cloud, on-prem, serverless, etc.)

3. **Set Priorities**
   - Ask what security aspects matter most (data protection, auth, injection, etc.)
   - Identify known vulnerabilities or concerns
   - Determine if this is pre-deployment audit or ongoing review
   - Confirm if recommendations should include fixes or just findings

### Phase 2: Security Analysis (During Execution)

4. **Map Attack Surface**
   - Use Serena to identify all entry points (API endpoints, forms, file uploads, etc.)
   - Map data flow from input to storage
   - Identify external integrations and dependencies
   - Document authentication and authorization points
   - Show progress: "Mapping attack surface and entry points..."

5. **Check OWASP Top 10**
   - Use Sequential Thinking to systematically check each OWASP category
   - **A01:2021 - Broken Access Control**
   - **A02:2021 - Cryptographic Failures**
   - **A03:2021 - Injection**
   - **A04:2021 - Insecure Design**
   - **A05:2021 - Security Misconfiguration**
   - **A06:2021 - Vulnerable and Outdated Components**
   - **A07:2021 - Identification and Authentication Failures**
   - **A08:2021 - Software and Data Integrity Failures**
   - **A09:2021 - Security Logging and Monitoring Failures**
   - **A10:2021 - Server-Side Request Forgery (SSRF)**
   - Show progress: "Checking against OWASP Top 10..."

6. **Analyze Authentication & Authorization**
   - Review authentication mechanisms
   - Check password policies and storage
   - Evaluate session management
   - Review token handling (JWT, API keys, etc.)
   - Check authorization logic and access controls
   - Identify privilege escalation risks
   - Show progress: "Analyzing authentication and authorization..."

7. **Check Input Validation & Sanitization**
   - Identify all user input points
   - Check for SQL injection vulnerabilities
   - Check for XSS (Cross-Site Scripting) vulnerabilities
   - Check for command injection risks
   - Review file upload security
   - Check for path traversal vulnerabilities
   - Show progress: "Checking input validation and sanitization..."

8. **Review Data Protection**
   - Check encryption at rest and in transit
   - Review sensitive data handling
   - Check for data leaks in logs or errors
   - Review API response data exposure
   - Check secure cookie settings
   - Evaluate secrets management
   - Show progress: "Reviewing data protection measures..."

9. **Analyze Dependencies & Components**
   - Check for known vulnerabilities in dependencies
   - Review third-party library usage
   - Check for outdated packages
   - Evaluate supply chain security
   - Show progress: "Analyzing dependencies for vulnerabilities..."

10. **Research Current Threats**
    - Use Tavily to find recent security vulnerabilities for used frameworks
    - Use Context7 to check official security advisories
    - Research framework-specific security best practices
    - Identify emerging threats relevant to the stack
    - Show progress: "Researching current security threats..."

### Phase 3: Risk Assessment (During Execution)

11. **Categorize Security Findings**
    - Assign severity scores (Critical, High, Medium, Low)
    - Assess exploitability and impact
    - Consider likelihood of exploitation
    - Prioritize by risk level
    - Show progress: "Assessing risk levels..."

### Phase 4: Deliverables (After Execution)

12. **Generate Security Audit Report**
    Output structured markdown with:

    **Security Audit Summary**
    - Application: [name]
    - Audit date: [current date]
    - Scope: [what was audited]
    - Compliance focus: [requirements if any]

    **Executive Summary**
    - **Overall Security Score:** [X/10]
    - **Critical vulnerabilities:** [count]
    - **High-risk issues:** [count]
    - **Medium-risk issues:** [count]
    - **Low-risk issues:** [count]
    - **Risk level:** [Critical/High/Medium/Low]

    **Immediate Actions Required:** [List of critical items]

    ---

    **Critical Vulnerabilities** 🚨 (Fix Immediately)

    ### CVE-SEVERITY-001: [Vulnerability Name]
    **Category:** [OWASP category]
    **Severity:** Critical
    **CVSS Score:** [if applicable]

    **Location:**
    - `[file_path]:[line_number]`

    **Vulnerability Description:**
    [Detailed description of the security issue]

    **Proof of Concept:**
    ```typescript
    // Vulnerable code
    ```

    **Attack Scenario:**
    1. [Step 1 of how this could be exploited]
    2. [Step 2]
    3. [Impact]

    **Impact:**
    - **Confidentiality:** [High/Medium/Low]
    - **Integrity:** [High/Medium/Low]
    - **Availability:** [High/Medium/Low]
    - **Data at risk:** [what data could be compromised]

    **Remediation:**
    ```typescript
    // Secure code
    ```

    **Fix steps:**
    - [ ] [Specific action 1] `[Estimate]`
    - [ ] [Specific action 2] `[Estimate]`

    **References:**
    - [OWASP guideline](url)
    - [Security advisory](url)

    ---

    **High-Risk Issues** ⚠️ (Fix Soon)

    ### SEC-HIGH-001: [Issue Name]
    **Category:** [OWASP category]
    **Severity:** High

    [Same structure as Critical]

    ---

    **Medium-Risk Issues** 💡 (Address in Sprint)

    ### SEC-MED-001: [Issue Name]
    [Same structure]

    ---

    **Low-Risk Issues / Best Practices** 📝 (Improve Over Time)

    ### SEC-LOW-001: [Issue Name]
    [Abbreviated structure]

    ---

    **OWASP Top 10 Analysis**

    ### A01:2021 - Broken Access Control
    **Status:** ⚠️ Issues Found

    **Findings:**
    - [file_path]:[line_number] - Missing authorization check
    - [file_path]:[line_number] - Insecure direct object reference

    **Recommendations:**
    - Implement role-based access control
    - Add authorization middleware to all protected routes

    ### A02:2021 - Cryptographic Failures
    **Status:** ✅ Mostly Secure

    **Findings:**
    - [minor issue if any]

    **Recommendations:**
    - [improvement if any]

    ### A03:2021 - Injection
    **Status:** 🚨 Critical Issues

    **Findings:**
    - [file_path]:[line_number] - SQL injection vulnerability
    - [file_path]:[line_number] - Command injection risk

    [Continue for all 10 categories...]

    ---

    **Security Architecture Assessment**

    ### Authentication
    **Score:** [X/10]

    **Current implementation:**
    - Method: [JWT, sessions, OAuth, etc.]
    - Password hashing: [algorithm]
    - MFA: [Yes/No]

    **Issues:**
    - ⚠️ [Issue 1]
    - ⚠️ [Issue 2]

    **Recommendations:**
    - [Recommendation 1]
    - [Recommendation 2]

    ### Authorization
    **Score:** [X/10]

    **Current implementation:**
    - Model: [RBAC, ABAC, etc.]
    - Enforcement: [where and how]

    **Issues:**
    - [List]

    **Recommendations:**
    - [List]

    ### Data Protection
    **Score:** [X/10]

    **Encryption at rest:** [Yes/No - details]
    **Encryption in transit:** [TLS version, etc.]
    **Sensitive data handling:** [assessment]

    **Issues:**
    - [List]

    **Recommendations:**
    - [List]

    ### Input Validation
    **Score:** [X/10]

    **Current approach:**
    - [Description of validation strategy]

    **Gaps:**
    - [List of missing or weak validation]

    **Recommendations:**
    - [List]

    ### Session Management
    **Score:** [X/10]

    **Current implementation:**
    - [Description]

    **Issues:**
    - [List]

    **Recommendations:**
    - [List]

    ### Error Handling & Logging
    **Score:** [X/10]

    **Current approach:**
    - [Description]

    **Issues:**
    - ⚠️ Sensitive data in error messages
    - ⚠️ Insufficient security event logging

    **Recommendations:**
    - [List]

    ---

    **Dependency Security**

    ### Vulnerable Dependencies
    ```
    [Package name]@[version]
    Severity: [Critical/High/Medium/Low]
    Vulnerability: [CVE or description]
    Fixed in: [version]
    ```

    ### Outdated Dependencies
    - [package]@[current] → [latest] (security updates available)

    **Remediation:**
    - [ ] Update [package] to [version] `[Estimate]`
    - [ ] Test for breaking changes `[Estimate]`

    ---

    **Compliance Check** (if applicable)

    ### GDPR Compliance
    - [ ] Right to access - [Status]
    - [ ] Right to deletion - [Status]
    - [ ] Data encryption - [Status]
    - [ ] Consent management - [Status]

    ### PCI-DSS (if handling payments)
    - [ ] Requirement 1: [Status]
    - [ ] Requirement 2: [Status]
    [etc.]

    ---

    **Security Best Practices**

    ✅ **Following:**
    - HTTPS enforced
    - Password hashing with bcrypt
    - CSRF protection enabled

    ⚠️ **Missing:**
    - Rate limiting on authentication endpoints
    - Security headers (CSP, HSTS, etc.)
    - API request validation schema

    ❌ **Violations:**
    - Secrets in environment variables (should use secrets manager)
    - No Web Application Firewall

    ---

    **Remediation Roadmap**

    ### Phase 1: Critical Fixes (Immediate) `[Total estimate]`
    - [ ] Fix SQL injection in [file] 🚨 `[Estimate]`
    - [ ] Fix broken access control in [file] 🚨 `[Estimate]`
    - [ ] Implement input validation for [endpoint] 🚨 `[Estimate]`

    ### Phase 2: High-Priority (This Week) `[Total estimate]`
    - [ ] Add rate limiting to auth endpoints ⚠️ `[Estimate]`
    - [ ] Implement security headers ⚠️ `[Estimate]`
    - [ ] Update vulnerable dependencies ⚠️ `[Estimate]`

    ### Phase 3: Improvements (This Sprint) `[Total estimate]`
    - [ ] Enhance logging for security events 💡 `[Estimate]`
    - [ ] Implement API request validation 💡 `[Estimate]`
    - [ ] Add security tests 💡 `[Estimate]`

    ### Phase 4: Long-term Hardening `[Total estimate]`
    - [ ] Implement WAF 📝 `[Estimate]`
    - [ ] Set up secrets manager 📝 `[Estimate]`
    - [ ] Security training for team 📝 `[Estimate]`

    ---

    **Testing Recommendations**

    - [ ] Set up automated dependency scanning (Snyk, Dependabot)
    - [ ] Implement security linting (eslint-plugin-security)
    - [ ] Add security unit tests for validation logic
    - [ ] Perform penetration testing before production
    - [ ] Set up continuous security monitoring

    ---

    **Resources & References**
    - [OWASP Top 10 2021](https://owasp.org/Top10/)
    - [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/)
    - [Framework security guide](url)
    - [Dependency security advisory](url)

13. **Offer Follow-up Actions**
    - "Would you like me to implement fixes for critical vulnerabilities?"
    - "Should I create detailed remediation steps for [specific vulnerability]?"
    - "Would you like me to audit additional areas or modules?"
    - "Should I research security best practices for [specific aspect]?"

## Context Awareness

**When file is selected:**
- Deep security audit of that specific file
- Analyze file's security role and exposure
- Identify vulnerabilities in that file

**When code is selected:**
- Security analysis of selected code block
- Show specific vulnerabilities in selection
- Provide secure refactored version

**When in API route context:**
- Focus on injection, authentication, authorization
- Check input validation thoroughly
- Review rate limiting and error handling

**When in auth context:**
- Deep dive on authentication security
- Check password handling, session management
- Review token security

**When no context:**
- Perform full application security audit
- Check all OWASP categories
- Review overall security posture

## Example Usage

### Example 1: Full Application Security Audit
```
User: /scp-security-audit
Assistant: I'll perform a comprehensive security audit. This is critical, so let me be thorough.

Questions:
1. What type of application? (web app, API, mobile backend, etc.)
2. Handling sensitive data? (PII, payments, health info, etc.)
3. Any compliance requirements? (GDPR, HIPAA, PCI-DSS, etc.)
4. Recent security concerns or incidents?
5. Already using any security tools? (linters, scanners, etc.)

[Uses Serena to map all entry points and data flows...]
[Uses Sequential Thinking to check all OWASP categories...]
[Uses Tavily to research recent vulnerabilities in used frameworks...]

**Security Audit Results:**
Overall Security Score: 5/10 - Several critical issues found

🚨 **Critical: 3 vulnerabilities**
- SQL injection in search endpoint
- Broken access control in admin routes
- Hardcoded API keys in source code

⚠️ **High: 5 issues**
- Missing rate limiting
- Weak password policy
- No CSRF protection
[etc.]

[Detailed findings with remediation roadmap...]
```

### Example 2: API Endpoint Security Review
```
User: [selects API route] /scp-security-audit
Assistant: I'll perform a security audit of this API endpoint.

Questions:
1. Is this endpoint public or authenticated?
2. What sensitive data does it handle?
3. Expected request volume?
4. Any known security concerns?

[Analyzes the specific endpoint...]

**Endpoint Security Assessment:**
Endpoint: POST /api/users/search
Security Score: 4/10 - Critical issues found

🚨 **Critical Vulnerabilities:**
1. SQL Injection (Line 45)
   - User input directly in SQL query
   - Attack: `'; DROP TABLE users; --`
   - Impact: Full database compromise

2. Missing Authorization (Line 23)
   - No check if user can search
   - Impact: Unauthorized data access

[Provides specific fixes with code...]
```

### Example 3: Authentication Security Audit
```
User: /scp-security-audit review our authentication system
Assistant: I'll audit your authentication implementation. This is security-critical.

Questions:
1. What auth method? (JWT, sessions, OAuth, etc.)
2. Supporting MFA?
3. Password reset flow implemented?
4. Any recent auth-related issues?

[Uses Serena to analyze all auth-related code...]

**Authentication Security Assessment:**
Overall Auth Security: 6/10

**Strengths:**
✅ Using bcrypt for password hashing
✅ HTTPS enforced
✅ JWT with reasonable expiry

**Critical Issues:**
🚨 JWT secret in environment variables (use secrets manager)
🚨 No rate limiting on login endpoint (brute force risk)

**High Priority:**
⚠️ Weak password policy (min 8 chars, no complexity requirements)
⚠️ No account lockout after failed attempts
⚠️ Tokens stored in localStorage (XSS vulnerability)

[Detailed remediation with code examples...]
```

## MCP Tools Usage Priority

1. **Serena** - Map attack surface, entry points, and data flows
2. **Sequential Thinking** - Systematically check OWASP categories
3. **Tavily** - Research current vulnerabilities and security advisories
4. **Context7** - Check official security documentation
5. **Filesystem-with-morph** - (Not used - audit only, no changes)

## Output Format

- **Structured markdown** with severity levels
- **CVSS scores** where applicable
- **Code examples** showing vulnerabilities and fixes
- **Attack scenarios** to demonstrate impact
- **Actionable remediation roadmap** with estimates
- **Interactive prompts** for follow-up
- Compliance checklists where relevant
- Links to OWASP and security resources
