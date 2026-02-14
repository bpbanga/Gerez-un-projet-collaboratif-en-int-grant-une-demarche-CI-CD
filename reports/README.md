# 📊 CI/CD Quality Report – BobApp

## 🔗 SonarCloud Projects

### Backend
Project: bobapp  
Language: Java  
Last Analysis: 14/02/2026 – 16:39  

SonarCloud link:  
https://sonarcloud.io/project/overview?id=bpbanga222309_bobapp-backend  

---

### Frontend
Project: bobapp-frontend  
Language: TypeScript / Angular  
Last Analysis: 14/02/2026 – 16:40  

SonarCloud link:  
https://sonarcloud.io/project/overview?id=bpbanga222309_bobapp-frontend  

---

# 📈 SonarCloud KPIs (Official Metrics)

## 🖥 Backend

- Lines of Code: 118
- Security Rating: A
- Reliability Rating: D
- Maintainability Rating: A
- Coverage: 38.8%
- Duplications: 0.0%
- Bugs: 1
- Vulnerabilities: 0
- Code Smells: 7
- Quality Gate: PASSED

---

## 🌐 Frontend

- Lines of Code: 167
- Security Rating: A
- Reliability Rating: A
- Maintainability Rating: A
- Coverage: 47.8%
- Duplications: 0.0%
- Bugs: 0
- Vulnerabilities: 0
- Code Smells: 6
- Quality Gate: PASSED

---

# 🚦 Quality Gate Configuration

Quality Gate used: Sonar Way (Default – Built-in)

We are using the free version of SonarCloud, which implies:
 - It is not possible to create a custom Quality Gate
 - Conditions apply only to New Code
 - Global coverage is displayed but not blocking
 - Existing bugs on old code do not block the pipeline

## Conditions on New Code (Sonar Way)

- No new bugs
- No new vulnerabilities
- Reliability Rating = A
- Security Rating = A
- Maintainability Rating = A
- Coverage ≥ 80%
- Duplicated Lines ≤ 3%
- 100% Security Hotspots Reviewed

### 📌 Coverage Clarification

Although the Quality Gate is PASSED, the global coverage currently is:
 - Backend: 38.8%
 - Frontend: 47.8%
This is expected because Sonar Way evaluates coverage only on New Code, not on the entire existing codebase.
To compensate for this limitation, additional checks are enforced in GitHub Actions to prevent deployment if quality steps fail.

# 🔄 CI/CD Gating Strategy

Strict order enforced via GitHub Actions `needs:`:

tests → coverage → sonar → docker build/push

Rules:
- No docker push on pull_request
- Docker push only on push to main
- No continue-on-error on quality steps
- Pipeline fails if Quality Gate fails

---

# 📦 GitHub Actions Artifacts

## Backend
- JaCoCo HTML report available in GitHub Actions artifacts
- Workflow: CI/CD Backend
- Artifact: jacoco-report

## Frontend
- Angular coverage HTML report available in GitHub Actions artifacts
- Workflow: CI/CD Frontend
- Artifact: coverage-report

---

# 🧠 Feedback Analysis (Notes & Avis)

User feedback highlighted:
- Occasional API instability
- Minor UI latency
- Missing edge-case validations

## Actions Implemented

| Issue Type | Action Taken |
|------------|-------------|
| Reliability issues | Added unit tests and integration tests |
| UI latency | Improved async handling |
| Validation bugs | Added test coverage and stricter validation rules |
| Technical debt | Enforced Sonar Quality Gate |
| Coverage gaps | Increased test coverage enforcement |

Quality monitoring now ensures:
- No new blocker issues
- Mandatory coverage thresholds
- Continuous static analysis
- Automated CI/CD validation

---

# ✅ Conclusion

The repository now integrates:

- Automated testing
- Code coverage (JaCoCo & Angular)
- SonarCloud static analysis
- Quality Gate enforcement
- Docker CI/CD with strict gating
- Centralized reporting in /reports

This guarantees sustainable code quality and controlled technical debt.
