# Memory Bank Dolutech – Advanced Rule for AI Agents in Software Projects

## Purpose of the Memory Bank

The purpose of the memory bank is to ensure that all technical information, decisions, learnings, integrations, and evolutions of a software project are documented, organized, and versioned from the very beginning of development. This facilitates audits, team continuity, onboarding, traceability, governance, and security analysis, providing a single source of reference and consultation throughout the project lifecycle.

## Initial Procedure – How the Agent Should Act

1. **Whenever starting a new project, create a folder in the root called** `memory-bank` **(no name variations).**
2. All files created inside this folder must be in Markdown format (`.md`) and follow the standard and examples set forth in this document.
3. Each file has a specific purpose and must be updated whenever an event, change, decision, or relevant evolution occurs in the project.
4. The agent must ensure that files are always up to date and consistent, avoiding outdated or duplicated information.
5. The memory bank must be treated as an integral part of project version control (git, svn, etc), with commits alongside the source code.

---

## Memory Bank File Structure

### 1. `languages.md`

**Purpose:**

- Document in detail all languages, frameworks, libraries, SDKs, runtimes, build tools, and technology standards adopted in the project.
- Indicate the purpose of each technology (example: “React – frontend SPA”, “Prisma – Node.js ORM for PostgreSQL”).

**Required content:**

- Name of language/framework/tool
- Version used (always specify)
- Purpose in the project
- Observed advantages and possible limitations

**Example:**

```
- Node.js v20.3.0 – Main backend (REST API)
- PostgreSQL v15 – Relational database
- Prisma v5.0 – ORM for Node.js/PostgreSQL integration
- TailwindCSS v3.4 – Frontend styling
- React v18 – Frontend SPA
- Express v4.18 – Backend framework
- Docker v26.0 – Environment orchestration
```

---

### 2. `integrations.md`

**Purpose:**

- List and describe in detail all external integrations (APIs, payment gateways, third-party services, cloud providers, social authentication, webhooks, etc).
- Describe endpoints, methods, authentication, callbacks, scopes, permissions, and sensitive data involved.

**Required content:**

- Name of the integration and provider
- Description of the purpose
- Technical details (endpoint, methods, payloads, authentication, callbacks)
- Critical security/privacy points
- Status (active, deprecated, test, staging)

**Example:**

```
- PagSeguro API (https://api.pagseguro.com) – Payment processing. OAuth2 authentication. Endpoints: /v1/payment, /v1/checkout. Status callbacks at /webhook/pagseguro. Status: active.
- AWS S3 – File storage. Access via AWS SDK, use of segregated buckets. Minimum permissions applied via IAM. Status: staging.
- Google OAuth – Social login, OAuth2 authorization, frontend/backend integration, scopes: email, profile. Status: active.
```

---

### 3. `features.md`

**Purpose:**

- Document each system feature, including business context, implemented rules, involved APIs, start/completion dates, owner, status, and relationship with requirements or tasks (e.g., link to issue in Jira or GitHub).

**Required content:**

- Name of the feature
- Description/summary
- Start and end dates
- Status (in development, completed, reviewed, approved, deprecated)
- Main responsible
- Relationship with task/requirement
- Involved components and modules

**Example:**

```
- User registration: Allows new users to create an account via email/password. Start: 2025-07-13. Completion: 2025-07-14. Status: completed. Responsible: Ana Costa. Issue: #12. Frontend (React), Backend (Express), Database (PostgreSQL).
- Password recovery: Reset process via token sent by email. Start: 2025-07-15. Status: in development. Responsible: Rafael Lima. Issue: #19. Integration with SendGrid.
```

---

### 4. `fixes.md`

**Purpose:**

- Register in detail found bugs, detected vulnerabilities, security flaws, performance improvements, and any type of correction, indicating impact, date, commit, responsible, and post-fix verification.

**Required content:**

- Clear description of the problem
- Date of identification
- Date of correction
- Reference to commit/pull request
- Person responsible for the fix
- Test/validation performed
- Impact on the system (affects production? requires rollback? is there a workaround?)

**Example:**

```
- Bug: 500 error when registering user with already registered email. Identified: 2025-07-15. Fixed: 2025-07-15. Commit: #c2a34b. Responsible: Pedro Soares. Validation: Automated test. Impact: blocked registration, did not affect production.
- Vulnerability: CSRF flaw in endpoint /api/user/update. Identified: 2025-07-16. Fixed: 2025-07-17. Commit: #e22ac0. Responsible: Lucas M. Tested manually.
```

---

### 5. `project-status.md`

**Purpose:**

- Summarize the overall project status: current version, milestones, module status, main risks, next steps, technical pending issues, production/staging environment, and infrastructure health.

**Required content:**

- Current project version
- Last relevant commit and date
- Completed/in-progress modules
- Main pending items or risks
- Production/staging status
- Relevant general notes

**Example:**

```
Version: 1.2.1
Last update: 2025-07-17 (commit #da23b2)
Frontend: OK
Backend: OK
PagSeguro Integration: awaiting staging approval
Pending: Redis cache adjustment in production
Risks: delay in payment gateway
```

---

### 6. `frontend.md`

**Purpose:**

- Document the entire frontend evolution: architectural decisions, routes, components, state patterns, tests, responsiveness strategies, backend communication, SDK integrations, error handling, accessibility, UX standards, optimizations.

**Required content:**

- Decisions made (with justification)
- Folder structure, main components created/changed
- Technologies/tools used (e.g., Redux, Context API, Zustand)
- Direct integrations (APIs, SDKs)
- Implemented authentication and authorization patterns
- Responsiveness, internationalization, accessibility approach
- Build and deployment strategies

**Example:**

```
- Adopted React Context for authentication management. Justification: simplifies the global user flow.
- All forms use Yup validation and global error handling.
- Adaptive layout with Tailwind, breakpoints documented in /src/styles/theme.js
- Auth API consumption via axios, using interceptors for token refresh.
- Protected pages with HOC AuthGuard.
```

---

### 7. `backend.md`

**Purpose:**

- Detail the entire backend structure: architecture, endpoints, authentication/authorization flows, data models, background routines, integrations, workers, queues, cache, logging mechanisms, middlewares, and security standards.

**Required content:**

- Description and diagram of main backend modules
- Implemented endpoints (with methods, payload, business rules)
- Authentication/authorization strategies (JWT, OAuth2, RBAC, ACL)
- Database, cache, queues, jobs integration
- Logging and monitoring policies
- Security controls: validation, sanitization, permissions
- Automated tests (coverage, tools)

**Example:**

```
- Endpoint POST /api/auth/login – authentication via JWT, credential validation by AuthService, logs in Elastic.
- Prisma ORM for PostgreSQL manipulation, versioned migrations, documented seeds.
- Asynchronous job for email sending using BullMQ and Redis.
- Rate limiting middleware (express-rate-limit) on all sensitive endpoints.
```

---

### 8. `architecture.md`

**Purpose:**

- Map the overall project architecture, including textual or visual diagrams, module detailing, main flows, system dependencies, integration points, gateways, middlewares, authentication flows, error control, orchestration, and monitoring.

**Required content:**

- Diagram or textual flow description
- Main components/modules and their communication
- External integration points
- Authentication/authorization flow (frontend, backend, third-party)
- Monitoring, logging, alarm structure
- Resilience patterns (retry, fallback, circuit breaker, etc)

**Example:**

```
[Frontend (React)] <-> [API Gateway (Express)] <-> [Services (Auth, Payments, User)] <-> [Database (PostgreSQL)]
Auth communicates with external email service via worker
PagSeguro integration protected by application firewall
Monitoring: Prometheus + Grafana
```

---

### 9. `communication.md`

**Purpose:**

- Document in detail how the frontend communicates with the backend and other services, protocols used, exposed endpoints, API contracts, request/response examples, authentication formats, and message standards.

**Required content:**

- Endpoints and routes consumed by frontend
- HTTP methods, payloads, required headers
- Protocols (REST, GraphQL, WebSocket, etc)
- Authentication patterns used in communications
- Real examples of requests and responses (with payloads)

**Example:**

```
Frontend calls POST /api/auth/login sending JSON { email, password }
Response: 200 OK, body: { token, user }
Authentication: Bearer JWT on all protected routes
Some modules use WebSocket for real-time updates
```

---

### 10. `version.md`

**Purpose:**

- Maintain a detailed history of project versions, release dates, changes, main features, bugfixes, status, and delivery environment (production/staging/dev).

**Required content:**

- Version number/ID
- Release date
- Main changes (feature/fix/breaking change)
- Status (production, staging, dev)

**Example:**

```
v1.0.0 (2025-07-13) – Initial backend/frontend structure, basic authentication, staging deploy.
v1.1.0 (2025-07-15) – User registration, AWS S3 integration, production deploy.
v1.2.0 (2025-07-17) – Payments system, CSRF fix, frontend layout adjustment.
```

---

### 11. `security.md`

**Purpose:**

- Document all security requirements, controls, and practices applied in the project, audit results, security frameworks recommendations, incident response plans, compliance status, and records of found vulnerabilities.

**Required content:**

- Security frameworks and standards adopted (e.g., OWASP Top 10, ASVS)
- Password, authentication, encryption policies
- Audit results, pentests, automated scans
- Identified and resolved vulnerabilities
- Incident response plan
- Compliance status (PCI DSS, LGPD, GDPR, etc)

**Example:**

```
Adopted OWASP ASVS Level 2 for backend, Level 1 for frontend
Passwords: minimum 12 characters, bcrypt 12 rounds
External pentest performed on 2025-07-18, 2 critical vulnerabilities fixed
Project compliant with LGPD, sensitive data segregated
```

---

### 12. `tests.md`

**Purpose:**

- Document the testing strategy (unit, integration, end-to-end, smoke, stress, fuzzing), coverage, tools, CI/CD automation, main scenarios, and quality metrics.

**Required content:**

- Testing strategy and types adopted
- Test coverage (percentage per module)
- Tools used (Jest, Cypress, Postman, etc)
- CI/CD pipeline status
- Main bugs found through tests
- Manual vs. automated tests

**Example:**

```
- Unit tests (Jest) for all backend services, coverage > 85%
- e2e tests with Cypress, 16 critical frontend scenarios
- CI pipeline runs lint, tests, build, and security scan on every PR
- Load test: 100 req/s for 10 minutes without failures
```

---

### 13. `index-memory-bank.md`

**Purpose:**

- Serve as the central index of the memory bank, listing all required files, description of each one’s function, usage examples, update instructions, and minimum recommended maintenance frequency.
- Must be updated whenever a new relevant file is added or removed from the memory bank.

**Required content:**

- List of all required and optional memory bank files
- Brief description of the function of each file
- Summary instructions for update/maintenance
- Minimum recommended update frequency (e.g., “features.md: update when creating new feature; security.md: after every audit or pentest”)

**Example:**

```
# Memory Bank Index

- languages.md: Project technologies, frameworks, and tools
- integrations.md: External integrations, providers, APIs
- features.md: Developed features, status, owners
- fixes.md: Bugs, vulnerabilities, applied improvements
- project-status.md: Overall status, pending issues, risks
- frontend.md: Frontend structure and evolution
- backend.md: Backend structure and evolution
- architecture.md: Architecture, diagrams, flows
- communication.md: Communication between modules, APIs, standards
- version.md: Version and release control
- security.md: Controls, audits, practices, and security incidents
- tests.md: Testing strategy, coverage, and tools

**General Instructions:**
- Update each file whenever there is relevant evolution or event
- Do not omit problems, risks, or limitations
- The index should be reviewed after every new file created or deleted
- All files should have the last update date at the top
```

---

## Notes and Recommendations for the Agent

- The agent is responsible for ensuring continuous updating, traceability, and documentation accuracy of the entire memory bank.
- Documentation must be objective, precise, always with date and responsible person identified.
- Register links to tasks, issues, pull requests, diagrams, images, and any relevant artifacts for each item.
- The memory bank is fundamental for governance, continuity, team transfers, compliance, and future audits.
- Do not fail to update documents after fixes, audits, deliveries, and critical decisions.
- Promote a collaborative documentation culture, encouraging the whole team to participate in the memory bank.

---

**END OF FILE**

