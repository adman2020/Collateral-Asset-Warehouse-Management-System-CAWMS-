# Requirements Document

## Introduction

The Collateral Asset Warehouse Management System (CAWMS) is a full-lifecycle digital collateral asset management platform designed for banks and microfinance companies. The system aims to replace existing Excel spreadsheets and paper-based document workflows, enabling end-to-end electronic management of collateral assets from warehouse-in, loan-out, and transfer to warehouse-out, thereby improving operational efficiency, reducing error rates, and enhancing monitoring capabilities.

## Project Overview
**Project Name**: Collateral Asset Warehouse Management System (CAWMS)
**Client**: XXXX Bank (Bank)
**Implementation Region**: Unlimited
**Project Objective**: Provide the bank with a full-lifecycle digital collateral asset warehouse management system, enabling end-to-end electronic management of asset warehouse-in, loan-out, transfer, and warehouse-out processes

## Business Background and Pain Points
### Current Situation Analysis
- **Current System**: Excel spreadsheets + paper-based documents + multiple isolated systems
- **Core Issues**:
  1. System silos, disconnected data
  2. Manual operations, high error rate (5-8%)
  3. Paper-based processes, low efficiency (processing time 3-5 days)
  4. Difficult monitoring, hard-to-control risks

### Driving Factors
1. Business growth demand: Rapid growth in collateral asset business
2. Regulatory compliance pressure: Financial regulators impose strict requirements for digital management
3. Market competition: Peer banks have begun digital transformation
4. Internal efficiency improvement: Manual operation costs continue to rise
5. Risk management strengthening: Existing processes have numerous risk points

The core business scenarios of the system include:
- Collateral Asset Warehouse-in: Complete asset receipt, verification, registration, and storage
- Collateral Asset Loan-out: Support temporary loan-out and return management
- Collateral Asset Transfer: Enable cross-vault asset allocation
- Collateral Asset Warehouse-out: Handle partial or full release of assets

# Bank Collateral Asset Warehouse Management System (CAWMS) - Kiro Requirements Document



## Core Business Functional Requirements

### 1. Collateral Asset Warehouse-in Management (Warehouse-in)
**Process Types**:
- New Intake - First-time warehouse-in
- Supplementary Intake - Supplementary document warehouse-in

**Approval Workflow**: 5-step approval
1. Prepare CA document checklist (Credit Processing/Drafting Unit)
2. Review and refine documents (BU/CTS Officer/PO)
3. Data entry into CA management system (BU/CTS Officer/PO)
4. Supervise/Approve CA warehouse-in (CTS Cluster Supervisor/Provincial Operations Supervisor/Treasury Center Supervisor)
5. Verify, data entry, document export, digital signature, print, and asset storage (Warehouse Administrator)

**Core Features**:
- ✅ WI-001: New intake application (manual input or data import from SeaOps/LOS/T24/Excel)
- ✅ WI-002: Supplementary intake
- ✅ WI-003: Warehouse-in approval workflow (5 steps, supports approval history viewing)
- ⏳ WI-004: CA-WI Slip generation
- ⏳ WI-005: Electronic seal (multi-party electronic seal)
- ✅ WI-006: Warehouse-in history query
- ✅ WI-007: Document checklist management (attachment upload, preview, download)
- ✅ WI-008: Warehouse code auto-generation
- ⏳ WI-009: MB04 data export

### 2. Collateral Asset Loan-out Management (Loan-out)
**Approval Workflow**: 6-step loan-out process + 4-step return process

**Core Features**:
- ✅ LO-001: Loan-out application (supports warehouse-in record selection, asset information auto-population)
- ✅ LO-002: Loan-out approval workflow (6-step loan-out approval + 4-step return approval)
- ⏳ LO-003: Credit processing confirmation
- ⏳ LO-004: CA-LO Slip generation
- ✅ LO-005: Return management
- ✅ LO-006: Loan period tracking (overdue alert)
- ⏳ LO-007: Core business system status synchronization (Mock mode)
- ✅ LO-008: Loan-out history query

### 3. Collateral Asset Transfer Management (Transfer)
**Process**: Transfer process reuses loan-out and return module workflows

**Core Features**:
- ✅ TF-001: Transfer application (supports warehouse information auto-display)
- ✅ TF-002: Transfer-out approval workflow (2 steps, supports resubmission after cancellation)
- ✅ TF-003: Receiving warehouse-in confirmation
- ⏳ TF-004: Transfer form generation
- ✅ TF-005: Custody record update

### 4. Collateral Asset Warehouse-out Management (Warehouse-out)
**Warehouse-out Types**:
- Partial Release
- Full Release

**Warehouse-out Reasons**: Loan settlement, debt processing, asset exchange, partial warehouse-out, deduction

**Core Features**:
- ✅ WO-001: Warehouse-out application
- ✅ WO-002: Warehouse-out approval workflow (4 steps, supports resubmission after cancellation)
- ✅ WO-003: Partial release
- ✅ WO-004: Full release
- ⏳ WO-005: CA-WO Slip generation
- ✅ WO-006: Warehouse-out reason management
- ✅ WO-007: Warehouse-out history query

## System Functional Requirements

### Data Management Features
- Data import: Support automatic import from SeaOps/LOS/T24/Excel
- Manual entry: Support necessary manual data entry and editing
- Data validation: Field-level validation, business logic validation, integrity checks
- Version management: Historical data traceability and version management
- Data export: Support standard format data export

### Process Management Features
- Electronic approval: End-to-end electronic approval, supporting multi-level approval
- Digital signature: Support digital signatures for forms such as CA-WI Slip, CA Loan-Out Slip
- Process configuration: Configurable approval workflows and business processes
- Status tracking: Real-time process status tracking and query
- Exception handling: Standardized exception handling procedures

### Permission Management Features
- Role-based permissions: Fine-grained role-based access control (RBAC)
- Data isolation: Branch offices can only view and operate their own unit's data
- Operation audit: Complete operation audit and log recording
- User management: User account management and role assignment
- Permission approval: Permission request and approval workflow

### Monitoring and Reporting Features
- ✅ Real-time monitoring: Real-time asset status monitoring and alerts
- ⏳ Standard reports: Automated generation of standardized business reports
- ✅ Custom queries: Support custom condition-based queries and export
- ✅ Alert notifications: Rule-based automatic alerts and reminders
- ✅ Statistical charts: Data visualization statistical charts

### Internationalization and User Experience Features
- ✅ Multi-language support: Chinese / Vietnamese / English language switching (frontend `vue-i18n` + backend `MessageSource`)
- ✅ Dark theme: Tech blue / sci-fi style theme switching with global state management
- ✅ Unified approval center: Aggregated view with pending / completed / history four modules (warehouse-in / loan-out / transfer / warehouse-out)

### Document Management Features
- File upload: Support multi-format file upload and storage
- File association: File and asset record association management
- Version control: File version management and historical traceability
- Online preview: Support online preview of common file formats
- File retrieval: Content-based file search

## Non-functional Requirements

### Performance Requirements
- Response time: Critical operation response time < 3 seconds
- Concurrent users: Support 500 concurrent users
- Processing capacity: Process 1,000+ transactions per day
- System availability: 99.9% availability
- Data capacity: Support 5+ years of transaction data storage

### Security Requirements
- Authentication: Integration with the bank's unified identity authentication system
- Data encryption: Encrypted data in transit and at rest
- Access control: Strict access control and permission management
- Audit trail: Complete security audit and operation logs
- Compliance: Meet financial regulatory security requirements

### Integration Requirements
- **T24 Core System Integration**: Real-time synchronization of customer information and account information
- **SeaOps System Integration**: Operational data synchronization
- **LOS Credit System Integration**: Credit approval data synchronization
- **Electronic Seal System Integration**: Integration with existing electronic seal system
- **Print Service Integration**: Integration with in-house print service
-  For the above integration items, only demo implementations are provided at present. Data can be directly created as verification test data; actual system connections are not yet implemented.

## Technical Solution Design

### Overall Architecture
Layered design based on Spring Boot:
1. **User Layer**: PC/Tablet/Mobile browsers
2. **Access Layer**: Nginx reverse proxy cluster (load balancing, SSL offloading)
3. **Application Layer**: Spring Boot 3.x monolithic application (7 major business modules + common services)
4. **External Integration Layer**: (Simulated) T24 / SeaOps / LOS / Excel integration
5. **Data Layer**: MySQL 8.x + file storage

### Technology Stack Selection
- **Frontend**: Nuxt.js 3.x + Naive UI + Vue 3 Composition API
- **Backend**: Spring Boot 3.x + Spring Security 6.x (RBAC + JWT)
- **Database**: MySQL 8.x
- **ORM**: MyBatis-Plus 3.x (global logical delete configuration)
- **Load Balancer**: Nginx 1.24+
- **Internationalization**: `@nuxtjs/i18n` + `vue-i18n` (frontend) / `MessageSource` (backend)
- **Report Engine**: Apache POI + JasperReports 5.6.1
- **Electronic Seal**: Third-party digital signature SDK
- **File Preview**: OnlyOffice Document Server (architecture reserved)

### Security Architecture
- Authentication: JWT Token authentication (Spring Security + JWT)
- Access control: RBAC role-based permissions (8 roles + menu permissions + data scope control)
- Transport encryption: HTTPS end-to-end encryption (TLS 1.2+)
- Data encryption: AES-256 sensitive field encryption, BCrypt password hashing
- Audit logging: Spring AOP interceptor + audit log table
- SQL injection prevention: Parameterized queries (MyBatis-Plus)
- XSS prevention: Output encoding + CSP
- CSRF prevention: Token verification

## Implementation Plan

### Phase Breakdown
1. **Phase 1 (2026-03)**: Project preparation and detailed design ✅
2. **Phase 2 (2026-03~04)**: Core feature development (warehouse-in/loan-out/transfer/warehouse-out CRUD + approval workflows) ✅
3. **Phase 2.1 (2026-04)**: Frontend experience optimization (i18n, dark theme, file attachments, unified approval center) ✅
4. **Phase 3 (2026-04~05)**: Extended feature development (report enhancement, OnlyOffice integration, remaining i18n) 🔄
5. **Phase 4 (2026-05)**: UAT testing, production deployment, and training ⏳
6. **Phase 5 (2026-05+)**: Operations support and optimization ⏳

### Key Deliverables
- Requirements specification document
- System detailed design document
- Runnable system base framework
- Complete CAWMS system codebase
- User training materials
- Production acceptance report

## Project Benefit Analysis

### Financial Benefits
- **Efficiency Improvement Benefits**: $530,000/year
  - Processing time reduction by 85%: $150,000
  - Error rate reduction by 90%: $100,000
  - Manual operation reduction by 70%: $200,000
  - Report generation reduction by 95%: $50,000
  - File retrieval reduction by 98%: $30,000

- **Cost Savings Benefits**: $185,000/year
  - Paper costs: $40,000
  - Storage costs: $25,000
  - Labor costs: $100,000
  - Management costs: $20,000

- **Risk Reduction Benefits**: $350,000/year
  - Operational risk: $100,000
  - Compliance risk: $200,000
  - Security risk: $50,000

- **Decision Support Benefits**: $300,000/year

**Total Annual Benefits**: $1,365,000
**Annual Operating Costs**: $120,000
**Annual Net Benefits**: $1,245,000
**Payback Period**: 9-15 months

### Non-financial Benefits
- **Strategic Value**: Advance the bank's comprehensive digital transformation and enhance competitiveness
- **Operational Value**: Process standardization, improved data quality, enhanced monitoring capabilities
- **Innovation Value**: Technology accumulation, product innovation, model innovation, ecosystem development

## Risk Management

### Technical Risks
- **System Integration Risk** (Impact: High, Probability: Medium)
  - Mitigation: Advance POC validation, prepare alternative solutions, phased integration
- **Performance Risk** (Impact: Medium, Probability: Medium)
  - Mitigation: Early performance testing involvement, optimize architecture, implement caching strategies
- **Security Risk** (Impact: High, Probability: Low)
  - Mitigation: Financial-grade security solution, third-party audit, security monitoring mechanisms

### Business Risks
- **User Acceptance Risk** (Impact: Medium, Probability: Medium)
  - Mitigation: Sufficient user training, gradual rollout, establish incentive mechanisms
- **Process Change Risk** (Impact: Medium, Probability: High)
  - Mitigation: Deep user involvement, fully consider existing habits, provide transition support
- **Requirement Change Risk** (Impact: Medium, Probability: High)
  - Mitigation: Strict change control, phased implementation, reserve change buffers

### Implementation Risks
- **Timeline Risk** (Impact: High, Probability: High)
  - Mitigation: Reasonable scheduling, critical path management, agile development
- **Resource Risk** (Impact: Medium, Probability: Medium)
  - Mitigation: Advance resource planning, establish backup resource pool, local partners
- **Localization Risk** (Impact: Medium, Probability: High)
  - Mitigation: In-depth research on regulations and culture, deep local user involvement

```yaml
Project Specifications:
  Project Name: "Collateral Asset Warehouse Management System (CAWMS)"
  Business Domain: "Banking & Finance - Collateral Asset Management"
  Client: "XXXX Bank (Bank)"
  Implementation Region: "Unlimited"
  Core Modules:
    - Collateral Asset Warehouse-in Management (Warehouse-in)
    - Collateral Asset Loan-out Management (Loan-out)
    - Collateral Asset Transfer Management (Transfer)
    - Collateral Asset Warehouse-out Management (Warehouse-out)
  Technology Stack:
    Frontend: "Nuxt.js 3.x + Naive UI + @nuxtjs/i18n"
    Backend: "Spring Boot 3.x + Spring Security 6.x"
    Database: "MySQL 8.x (Master-Slave Replication)"
    Deployment: "Nginx Load Balancing + Docker"
  Integration Requirements:
    - Core System Integration
    - Ops System Integration
    - LOS Credit System Integration
    - Electronic Seal System Integration
  Performance Requirements:
    - Response Time: "P95 < 3 seconds"
    - Concurrent Users: "500"
    - Availability: "99.9%"
  Security Requirements:
    - Banking-grade security compliance
    - Financial regulatory requirements
    - Encrypted data storage
  Implementation Timeline: "12 months (5 phases)"
  Expected Benefits: "Annual net benefit $1,245,000, payback period 9-15 months"
```

```
Developing a Collateral Asset Management System for a Bank:
Core Features: Four major processes - asset warehouse-in, loan-out, transfer, and warehouse-out
Integration Requirements: T24, SeaOps, LOS, electronic seal
Technology Stack: Spring Boot + React + MySQL
Security Requirements: Banking-grade security, regulatory compliance
Performance Requirements: 500 concurrent users, 99.9% availability
Implementation Timeline: 12 months, 5 phases
Expected Benefits: Annual net benefit $1.245M, payback period 9-15 months
```

---
*Document generated: 2026-04-24*
*Data source: Bank Collateral Asset Management System Complete Solution.docx*
*Document status: Updated — Core business features development completed and verified*
