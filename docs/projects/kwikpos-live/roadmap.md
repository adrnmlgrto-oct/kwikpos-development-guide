# Roadmap & Planned Work

This document outlines planned features, integrations, and improvements for KwikPOS Live. These items represent future work that needs to be implemented.

## Planned Integrations

### KwikPOS Pro Data Sync Integration

**Priority:** High<br />
**Status:** Planned

**Description:**
Integration to enable KwikPOS Pro (our new POS product) to send sales data and transactions to the KwikPOS Live cloud backend. This follows the same pattern as the existing legacy POS integration but needs to be implemented on the KwikPOS Pro side.

**Current State:**

- Legacy Chase POS already syncs data to KwikPOS Live cloud
- Sync endpoints are already available and ready on KwikPOS Live backend
- KwikPOS Pro team needs to implement the client-side integration to call these endpoints

**Requirements:**

- KwikPOS Pro must implement API calls to existing sync endpoints
- Sales data, transactions, and inventory movements need to be sent to cloud
- Real-time or near-real-time synchronization preferred
- Handle offline scenarios (queue data when offline, sync when online)

**Implementation Notes:**

- **Backend (KwikPOS Live) side:** Sync endpoints already exist and are ready
- **Frontend (KwikPOS Pro) side:** Team needs to hook up their POS to call these endpoints
- This is primarily a KwikPOS Pro development task
- KwikPOS Live team may need to provide endpoint documentation and support

**Responsibilities:**

- **KwikPOS Live Backend:** Maintain and support existing sync endpoints
- **KwikPOS Pro Team:** Implement the actual integration and sync logic in their POS application

**Resources:**

- Existing sync endpoint documentation (to be provided to KwikPOS Pro team)
- Legacy POS integration as reference implementation
- API specifications for data format and authentication

**Notes:**

- Coordination with KwikPOS Pro development team is essential
- May need to schedule knowledge transfer sessions
- Ensure KwikPOS Pro team has access to API documentation

---

### Inventory Syncing Integration

**Priority:** High<br />
**Status:** Planned

**Description:**
Enable inventory data synchronization between POS terminals and the cloud backend. This will allow centralized inventory tracking and management across multiple stores and branches.

**Current State:**

- Requirements not fully defined yet
- Inventory management planned as a future cloud feature
- Need to determine sync frequency, conflict resolution, and data flow

**Requirements:**

- TBD - Requirements gathering needed
- Inventory levels sync from POS to cloud
- Potentially bidirectional sync (cloud to POS for centralized inventory management)
- Conflict resolution strategy for inventory discrepancies

**Implementation Notes:**

- Coordinate with product team to gather detailed requirements
- Determine if this is real-time or batch synchronization
- Design database schema for inventory data if not already present
- Consider multi-tenant implications for inventory tracking

**Next Steps:**

- Requirements gathering with stakeholders
- Technical design based on requirements
- Implementation plan and timeline

**Notes:**

- Requirements are still being defined - not enough details available yet
- This may be part of the larger inventory management feature

---

## Planned Features

### AI-Powered Sales Reports and Forecasting

**Priority:** Medium<br />
**Status:** Planned

**Description:**
Implement AI-powered analytics features including intelligent sales reports, sales forecasting, trend analysis, and predictive insights to help clients make better business decisions.

**User Stories:**

- As a restaurant owner, I want to see sales forecasts so that I can plan inventory and staffing
- As a manager, I want AI-generated insights on sales trends so that I can identify growth opportunities
- As a business analyst, I want predictive reports so that I can make data-driven decisions

**Technical Approach:**

- Integrate AI/ML models for sales prediction and forecasting
- Use historical sales data to train forecasting models
- Implement trend analysis algorithms
- Create new API endpoints for AI-generated reports
- Design dashboard UI for displaying AI insights

**Potential Technologies:**

- Machine learning libraries (TensorFlow, scikit-learn, or similar)
- Time series forecasting models (ARIMA, Prophet, LSTM)
- `XGBoost` machine learning tool for sales forecasting
- May require integration with external AI services or in-house model development

**Acceptance Criteria:**

- Sales forecasting with reasonable accuracy based on historical data
- Trend detection and anomaly identification
- AI-generated insights and recommendations
- User-friendly visualization of forecasts and predictions
- Performance is acceptable (reports generate in reasonable time)

**Resources:**

- Historical sales data for training
- Business requirements for specific insights needed
- UI/UX designs for report presentation

**Notes:**

- May require data science expertise
- Consider privacy and data security for AI processing
- Evaluate build vs. buy for AI capabilities

---

### Cloud-Based Inventory Management System

**Priority:** High<br />
**Status:** Planned

**Description:**
Build a comprehensive cloud-based inventory management system that leverages the multi-tenant architecture to provide centralized inventory tracking, management, and reporting across multiple stores and branches.

**Planned Timeline:** February 2026

**User Stories:**

- As a multi-branch owner, I want to manage inventory centrally so that I can track stock across all locations
- As a store manager, I want to see real-time inventory levels so that I can avoid stockouts
- As a warehouse manager, I want to track inventory movements so that I can optimize stock distribution

**Technical Approach:**

- Design database schema for inventory items, stock levels, and movements
- Implement CRUD APIs for inventory management
- Build real-time inventory tracking with sync from POS terminals
- Create inventory reporting and analytics features
- Develop multi-tenant inventory access controls (each tenant sees only their inventory)
- Build UI for inventory management dashboard

**Key Features:**

- Item master data management (SKU, descriptions, categories)
- Stock level tracking per location/branch
- Inventory movement tracking (receipts, transfers, adjustments)
- Low stock alerts and notifications
- Inventory reports (stock levels, movement history, valuation)
- Multi-location inventory visibility

**Acceptance Criteria:**

- Centralized inventory database with multi-tenant support
- Real-time or near-real-time inventory sync from POS
- Inventory reports accessible via web dashboard
- Role-based access control for inventory management
- Performance handles multiple stores and thousands of items

**Resources:**

- Business requirements document
- UI/UX designs for inventory dashboard
- Integration specifications with POS systems

**Notes:**

- **Target Date:** February 2026
- Coordinate with POS teams for inventory sync integration
- Consider scalability for large inventories
- May need data migration for existing inventory data

---

## Known Issues & Tech Debt

### Spring Boot and Java Version Upgrade

**Priority:** High<br />
**Status:** Planned

**Description:**
Upgrade from Spring Boot 2.7.2 and Java 8 to Spring Boot 3.x and Java 17 LTS to stay on supported versions, improve performance, security, and access newer framework features.

**Current State:**

- Running on Spring Boot 2.7.2 with Java 8
- Java 8 is no longer receiving public updates (EOL)
- Spring Boot 2.x will eventually lose support
- Missing out on performance improvements and modern Java features

**Impact:**

- Security vulnerabilities in older Java versions
- Missing performance optimizations in newer JVMs
- Unable to use modern Spring Boot 3.x features
- Potential dependency compatibility issues over time
- Difficulty hiring developers familiar with old tech stack

**Proposed Solution:**

- Upgrade to Java 17 LTS (current long-term support version)
- Migrate to Spring Boot 3.x (latest stable version)
- Update dependencies to compatible versions
- Test thoroughly to ensure no breaking changes
- Plan phased rollout to minimize risk

**Migration Steps:**

1. Audit current dependencies and identify compatibility issues
2. Set up local development environment with Java 17
3. Update Spring Boot to 3.x in a separate branch
4. Fix breaking changes and deprecated API usage
5. Update all dependencies to Spring Boot 3.x compatible versions
6. Comprehensive testing (unit, integration, end-to-end)
7. Performance testing and optimization
8. Staged deployment (dev → staging → production)

**Risks/Considerations:**

- Breaking changes in Spring Boot 3.x (e.g., Jakarta EE namespace changes)
- Potential API incompatibilities with dependencies
- Need thorough regression testing
- May require code refactoring
- Deployment downtime considerations

**Effort Estimate:**

- Medium to Large (several weeks of development and testing)

**Testing Requirements:**

- Full regression testing of all endpoints
- Integration testing with POS systems
- Performance benchmarking
- Security testing
- User acceptance testing

**Notes:**

- This is technical debt that should be addressed sooner rather than later
- Java 8 EOL creates security and compliance risks
- Coordinate with team for development schedule
- Consider doing in phases to reduce risk

---

## Notes for Future Developers

### General Context

KwikPOS Live serves as the central cloud backend for our POS ecosystem. It aggregates sales data from multiple POS terminals across different client stores and branches, providing analytics and reporting capabilities through a multi-tenant architecture.

### Key Contacts

- **Developer:** Sophie
- **KwikPOS Pro Development Team:** For POS integration coordination

### Things to Keep in Mind

- This is a multi-tenant system - always ensure tenant data isolation
- Performance is critical for real-time data syncing from multiple POS terminals
- Coordinate with POS teams (Legacy and KwikPOS Pro) for any API changes
- Database migrations must be carefully planned due to production data
- AWS infrastructure changes should be documented and coordinated

---

## Timeline & Prioritization

### Q1 2026 (January - March)

- **Cloud-Based Inventory Management** - Target: February 2026
    - Database schema design and implementation
    - Core inventory APIs development
    - Basic inventory dashboard UI
    - Integration with POS systems for inventory sync

### Q2 2026 (April - June)

- **AI-Powered Sales Reports and Forecasting** - Timeline TBD
    - Requirements finalization
    - AI model selection and integration
    - Report generation APIs
    - Dashboard UI for AI insights

### Future (No Specific Timeline)

- **Spring Boot and Java Version Upgrade** - Schedule TBD
    - Dependency audit and upgrade planning
    - Development and testing
    - Phased deployment

- **KwikPOS Pro Sync Integration** - Dependent on KwikPOS Pro team
    - Primarily KwikPOS Pro team responsibility
    - KwikPOS Live team provides endpoint support

- **Inventory Syncing Integration** - Requirements pending
    - Requirements gathering
    - Technical design
    - Implementation

### Ongoing

- Bug fixes and technical improvements as identified
- Performance optimizations
- Security updates and patches
- Support for existing integrations
